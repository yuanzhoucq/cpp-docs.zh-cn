---
title: 推理执行端通道的 c + + 开发人员指南
ms.date: 07/10/2018
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
- Spectre
- CVE-2017-5753
- Speculative Execution
ms.openlocfilehash: 94e55f08e4ff427aef0c93bf74c711a6fd935d0a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631009"
---
# <a name="c-developer-guidance-for-speculative-execution-side-channels"></a>推理执行端通道的 c + + 开发人员指南

本文包含面向开发人员以帮助识别和防御推理执行端通道硬件在 c + + 软件中的漏洞的指南。 这些漏洞可能会泄露敏感信息跨信任边界和可能会影响支持推理、 扩展的顺序执行的指令处理器运行的软件。 此类漏洞已在 2018 年 1 月中, 所述的第一个和其他背景和指南可在[Microsoft 安全公告](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002)。

本文提供的指导与漏洞所表示的类：

1. CVE-2017-5753，也称为 Spectre 变体 1。 此硬件漏洞类与相关端通道可能会出现由于条件分支预测时，会出现的推理执行。 （从 15.5.5 版开始） 的 Visual Studio 2017 中 Visual c + + 编译器支持`/Qspectre`开关这提供了一组有限的潜在易受攻击的编码模式编译时缓解与相关的 CVE 2017-5753。 `/Qspectre`开关也会出现在通过 Visual Studio 2015 Update 3 [KB 4338871](https://support.microsoft.com/help/4338871)。 文档[/Qspectre](https://docs.microsoft.com/cpp/build/reference/qspectre)标志提供有关其效果和使用情况详细信息。

2. CVE-2018年-3639，也称为[推理存储区绕过 (SSB)](https://aka.ms/sescsrdssb)。 此硬件漏洞类与相关端通道可能会出现由于之前作为内存访问预测结果依赖于存储的负载的推理执行。

标题为演示文稿中找不到推理执行端道漏洞的可访问简介[用例的 Spectre 和 Meltdown](https://www.youtube.com/watch?v=_4O0zMW-Zu4)发现这些问题的研究团队之一。

## <a name="what-are-speculative-execution-side-channel-hardware-vulnerabilities"></a>推理执行端通道硬件漏洞有哪些？

新型 Cpu，从而提供更高程度的性能的推理和无序执行指令的使用。 例如，这通常通过实现预测目标分支 （条件和间接） 使 CPU 开始推测性地执行说明预测的分支目标，从而避免停滞，直到实际分支目标已解决。 在的 CPU 更高版本发现的预测出现时，所有计算机的状态推测性计算将被放弃。 这可确保有没有体系结构上可见的已撤销的误报推理效果。

虽然推理执行不会影响体系结构上可见状态，它将保留剩余跟踪非体系结构的状态，例如 CPU 使用的各种缓存。 它是可以达到端道漏洞的推理执行的这些残留痕迹。 若要更好地理解这一点，请考虑下面的代码段提供 CVE 2017-5753 （边界检查绕过） 的示例：

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

在此示例中，`ReadByte`是提供到该缓冲区的缓冲区、 缓冲区大小和索引。 索引指定的参数，通过`untrusted_index`，提供的无特权的上下文中，例如非管理的过程。 如果`untrusted_index`是小于`buffer_size`，然后从读取该索引处的字符`buffer`和用于对索引到共享的内存引用区域`shared_buffer`。

从体系结构的角度看，此代码序列是完全安全保证，如`untrusted_index`将始终小于`buffer_size`。 但是，出现推理执行的情况下就可以在 CPU 将条件的分支误预测和执行主体 if 语句，即使`untrusted_index`大于或等于`buffer_size`。 因此，CPU 可能推测性读取一个字节的边界 from beyond `buffer` （这可能是机密） 并可以使用该字节值来计算通过后续加载地址`shared_buffer`。

而 CPU 将最终能够检测到此预测，也显示超出界限从读取的字节值有关的信息在 CPU 缓存中保留残留的负面影响`buffer`。 小于可以检测到这些副作用的方式快速探测系统上运行的特权的上下文行中的每个缓存`shared_buffer`访问。 完成此操作时可以执行的步骤如下：

1. **调用`ReadByte`使用多次`untrusted_index`正在小于`buffer_size`** 。 攻击上下文可能会导致要调用的受害者上下文`ReadByte`（例如通过 RPC) 此类分支预测因子的输出是训练是作为 not 采取`untrusted_index`是小于`buffer_size`。

2. **刷新所有缓存行中的`shared_buffer`** 。 攻击上下文必须刷新所有共享的内存引用区域中的缓存行`shared_buffer`。 由于共享内存区域，这非常简单，并可使用内部函数类似于实现`_mm_clflush`。

3. **调用`ReadByte`与`untrusted_index`大于`buffer_size`** 。 攻击上下文会导致牺牲品上下文来调用`ReadByte`，以便它错误地预测不执行分支。 此处理器推测性地执行大量 if 块的原因`untrusted_index`大于`buffer_size`，因此从而导致越界读取的`buffer`。 因此，`shared_buffer`编制索引的索引使用读取超出边界，从而导致要加载的 CPU 的相应的缓存行的潜在机密值。

4. **读取缓存中的每一行`shared_buffer`若要查看最快的速度访问它**。 攻击上下文可以读取在每个缓存行`shared_buffer`和检测速度比其他加载缓存行。 这是可能会通过步骤 3 已恢复的缓存行。 在此示例中的字节值和缓存行之间不存在 1 对 1 关系，因为这会允许攻击者能够推断越界读取的字节的实际值。

上面的步骤提供了使用结合利用 CVE 2017-5753 的实例称为刷新 + 重新加载的技术的示例。

## <a name="what-software-scenarios-can-be-impacted"></a>哪些软件方案可能会受到影响？

使用等进程的安全软件开发[安全开发生命周期](https://www.microsoft.com/sdl/)(SDL) 通常需要开发人员标识存在于其应用程序信任边界。 在其中应用程序可能不太受信任的上下文，如在系统上的另一个进程或非管理用户模式进程在内核模式设备驱动程序的情况下提供的数据进行交互的地方存在一条信任边界。 涉及推理执行端通道的安全漏洞的新类是与信任边界隔离代码和数据的设备上的现有软件安全模型中的许多相关。

下表提供了开发人员可能需要会担心发生这些漏洞的软件安全模型的摘要：

|信任边界|描述|
|----------------|----------------|
|虚拟机边界|隔离在单独的虚拟机接收来自另一个虚拟机不受信任的数据的工作负荷的应用程序可能会面临风险。|
|内核边界|从非管理用户模式进程接收不受信任的数据的内核模式设备驱动程序可能会面临风险。|
|进程边界|从本地系统上运行的另一个进程接收不受信任的数据，例如通过远程过程调用 (RPC)、 共享的内存或其他进程间通信 (IPC) 机制可能有风险的应用程序。|
|Enclave 边界|接收来自外部 enclave 的不受信任的数据 （例如 Intel SGX) 安全 enclave 内执行的应用程序可能会面临风险。|
|语言边界|应用程序，用于解释或实时 (JIT) 编译和执行不受信任的代码编写的更高级别的语言可能有风险。|

攻击面公开到上述任一信任边界应检查代码的攻击面来识别和缓解推理执行端道漏洞的可能的实例上的应用程序。 应注意信任边界公开给远程攻击面，如远程网络协议，已不已证明的推理执行端道漏洞的风险。

## <a name="potentially-vulnerable-coding-patterns"></a>可能有漏洞的编码模式

推理执行端道漏洞可能会出现由于多个编码模式。 本部分介绍可能有漏洞的编码模式，并举例说明对于每个，但应识别这些主题的变体可能存在。 在这种情况下，建议开发人员将需要这些模式示例而不是所有潜在易受攻击的编码模式的详尽列表。 可以立即在软件中存在的内存安全漏洞的同一个类可能还存在沿推理，而出的顺序路径的执行，包括但不是限于缓冲区溢出、 越界数组访问，未初始化的内存使用类型混淆，依次类推。 攻击者可用于利用内存沿体系结构路径的安全漏洞的同一个基元也适用于推理的路径。

一般情况下，在可以控制或受到太受信任的环境的数据上执行条件表达式时，可能会发生推理执行端通道与条件分支预测。 例如，这可能包括在中使用的条件表达式`if`， `for`， `while`， `switch`，或三元语句。 对于每个这些语句，编译器可能会生成 CPU 然后可以预测在运行时的分支目标条件分支。

对于每个示例中，使用短语"推理屏障"注释插入其中一名开发人员可能会引入作为一种缓解的障碍。 此部分中的更详细地讨论上缓解措施。

## <a name="speculative-out-of-bounds-load"></a>推理越界加载

此类别的编码模式涉及到会导致推理越界条件分支预测内存访问。

### <a name="array-out-of-bounds-load-feeding-a-load"></a>数组越界加载将馈送负载

这种编码模式是 CVE 2017-5753 （边界检查绕过） 的最初所述易受攻击编码模式。 本文的背景部分说明了这种模式在详细信息。

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        // SPECULATION BARRIER
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

同样，数组越界负载可能会出现与超过其终止循环结合使用条件由于预测。 在此示例中，与关联的条件分支`x < buffer_size`表达式可能会误预测并推测性地执行的正文`for`循环时`x`大于或等于`buffer_size`，从而导致推理越界加载。

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadBytes(unsigned char *buffer, unsigned int buffer_size) {
    for (unsigned int x = 0; x < buffer_size; x++) {
        // SPECULATION BARRIER
        unsigned char value = buffer[x];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="array-out-of-bounds-load-feeding-an-indirect-branch"></a>数组越界加载将馈送间接分支

这种编码模式涉及条件分支预测可能导致这种情况越界越界读取权访问的函数指针间接分支目标到哪个然后潜在客户地址的数组。 以下代码片段提供一个示例，说明了这一点。

在此示例中，不受信任的消息标识符提供给通过 DispatchMessage`untrusted_message_id`参数。 如果`untrusted_message_id`是小于`MAX_MESSAGE_ID`，则它将使用的函数指针的数组进行索引和分支到相应的分支目标。 此代码是安全的体系结构方面，但如果 CPU 误预测条件分支，可能会导致`DispatchTable`编制索引`untrusted_message_id`时其值是大于或等于`MAX_MESSAGE_ID`，因此从而导致越界访问。 这可能导致从派生的数组，这可能导致信息泄露，具体取决于推测性地执行的代码的边界之外的分支目标地址的推理执行。

```cpp
#define MAX_MESSAGE_ID 16

typedef void (*MESSAGE_ROUTINE)(unsigned char *buffer, unsigned int buffer_size);

const MESSAGE_ROUTINE DispatchTable[MAX_MESSAGE_ID];

void DispatchMessage(unsigned int untrusted_message_id, unsigned char *buffer, unsigned int buffer_size) {
    if (untrusted_message_id < MAX_MESSAGE_ID) {
        // SPECULATION BARRIER
        DispatchTable[untrusted_message_id](buffer, buffer_size);
    }
}
```

与数组超出边界的用例中加载馈送另一种负载，这种情况也可能发生与超过由于预测其终止条件循环结合使用。

### <a name="array-out-of-bounds-store-feeding-an-indirect-branch"></a>越界数组存储区将馈送间接分支

尽管前面的示例演示如何推理越界负载可能会影响间接分支目标，还有可能的越界存储修改间接分支目标，如函数指针或返回地址。 这可能会导致推理执行从一个攻击者指定的地址。

在此示例中，不受信任的索引传递`untrusted_index`参数。 如果`untrusted_index`的元素计数少于`pointers`数组 （256 个元素），然后在提供的指针值`ptr`写入到`pointers`数组。 此代码是安全的体系结构方面，但如果 CPU 误预测条件分支，可能会导致`ptr`推测性地写入超出堆栈分配`pointers`数组。 这可能导致的寄信人地址的推理损坏`WriteSlot`。 如果攻击者可以控制的值`ptr`，则可以使推理执行从一个任意地址时`WriteSlot`返回沿推理的路径。

```cpp
unsigned char WriteSlot(unsigned int untrusted_index, void *ptr) {
    void *pointers[256];
    if (untrusted_index < 256) {
        // SPECULATION BARRIER
        pointers[untrusted_index] = ptr;
    }
}
```

同样，如果名为的函数指针本地变量`func`已在堆栈上分配，则可能有可能推测性地修改地址的`func`条件分支预测发生时引用。 通过调用的函数指针时，这可能导致来自任意地址推理执行。

```cpp
unsigned char WriteSlot(unsigned int untrusted_index, void *ptr) {
    void *pointers[256];
    void (*func)() = &callback;
    if (untrusted_index < 256) {
        // SPECULATION BARRIER
        pointers[untrusted_index] = ptr;
    }
    func();
}
```

应注意，这两个示例涉及推理修改堆栈分配间接分支指针。 有可能推测性修改的全局变量、 堆分配内存和甚至只读内存上一些 Cpu 也可能发生。 对于堆栈分配内存，Visual c + + 编译器已采用步骤以使其更难推测性地修改堆栈分配间接分支目标，例如通过对本地变量进行重新排序，以便与作为安全 cookie 相邻放置缓冲区属于[/GS](https://docs.microsoft.com/cpp/build/reference/gs-buffer-security-check)编译器安全功能。

## <a name="speculative-type-confusion"></a>推理类型混淆

此类别处理编码模式可能导致引发推理类型混淆。 推理执行期间使用非体系结构的路径上的类型不正确访问内存时，将发生这种情况。 条件分支预测和推理存储区绕过可能会导致推理类型混淆。

推理存储区绕过，这会导致编译器将多种类型的变量的堆栈位置重新使用的方案。 这是因为该体系结构的类型的变量存储区`A`可能会被绕过，从而允许类型的负载`A`推测性地执行之前分配该变量。 如果以前存储的变量的不同类型，这可以创建推理类型混淆的条件。

为条件分支预测，将使用以下代码片段来描述不同的条件可提供推理类型混淆升至。

```cpp
enum TypeName {
    Type1,
    Type2
};

class CBaseType {
public:
    CBaseType(TypeName type) : type(type) {}
    TypeName type;
};

class CType1 : public CBaseType {
public:
    CType1() : CBaseType(Type1) {}
    char field1[256];
    unsigned char field2;
};

class CType2 : public CBaseType {
public:
    CType2() : CBaseType(Type2) {}
    void (*dispatch_routine)();
    unsigned char field2;
};

// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ProcessType(CBaseType *obj)
{
    if (obj->type == Type1) {
        // SPECULATION BARRIER
        CType1 *obj1 = static_cast<CType1 *>(obj);

        unsigned char value = obj1->field2;

        return shared_buffer[value * 4096];
    }
    else if (obj->type == Type2) {
        // SPECULATION BARRIER
        CType2 *obj2 = static_cast<CType2 *>(obj);

        obj2->dispatch_routine();

        return obj2->field2;
    }
}
```

### <a name="speculative-type-confusion-leading-to-an-out-of-bounds-load"></a>推理类型混淆通向越界加载

这种编码模式涉及推理类型混淆可以导致这种情况越界或加载的值的源的后续加载地址的类型相混淆字段访问。 这是类似于数组越界编码模式，但通过一种替代方法，如上所示编码序列身份列入清单。 在此示例中，攻击上下文可能会导致要执行的受害者上下文`ProcessType`多次使用类型的对象`CType1`(`type`字段等于`Type1`)。 这会使得第一个条件分支`if`来预测未执行的语句。 攻击上下文则会导致要执行的受害者上下文`ProcessType`类型的对象与`CType2`。 这可能导致类型推理混淆，如果条件的第一个分支`if`语句误预测，并执行的正文`if`语句，因此强制转换类型的对象`CType2`到`CType1`。 由于`CType2`小于`CType1`，对的内存访问`CType1::field2`将导致推理越界加载的可能是机密数据。 然后在从负载中使用此值`shared_buffer`它可以创建可观察的负面影响，如数组超出边界示例前面所述。

### <a name="speculative-type-confusion-leading-to-an-indirect-branch"></a>推理类型混淆，从而导致间接分支

这种编码模式涉及其中推理类型混淆可能会导致在不安全的间接分支过程推理执行这种情况。 在此示例中，攻击上下文可能会导致要执行的受害者上下文`ProcessType`多次使用类型的对象`CType2`(`type`字段等于`Type2`)。 这会使得第一个条件分支`if`要执行的语句和`else if`语句不执行。 攻击上下文则会导致要执行的受害者上下文`ProcessType`类型的对象与`CType1`。 这可能导致类型推理混淆，如果条件的第一个分支`if`预测语句执行和`else if`语句预测不执行，因此执行的正文`else if`类型的对象强制转换和`CType1`到`CType2`。 由于`CType2::dispatch_routine`与字段重叠`char`数组`CType1::field1`，这可能导致推理间接分支到非预期的分支的目标。 如果攻击上下文可以控制中的字节值`CType1::field1`数组，它们可能能够控制分支目标地址。

## <a name="speculative-uninitialized-use"></a>推理未初始化的使用

此类别的编码模式涉及其中推理执行可能会访问未初始化的内存并使用它来后续负载或间接分支方案。 为可利用这些编码模式，攻击者需要能够控制或有意义的方式会影响使用而未进行初始化上下文中使用的内存的内容。

### <a name="speculative-uninitialized-use-leading-to-an-out-of-bounds-load"></a>通向推理未初始化的使用越界加载

推理的未初始化的使用可能会导致越界加载时，使用一个攻击者控制值。 在下面的值的示例`index`分配`trusted_index`体系结构的所有路径上和`trusted_index`被假定为小于或等于`buffer_size`。 但是，具体取决于由编译器生成的代码，就可以推理存储区绕过可能允许从负载`buffer[index]`和相关表达式之前对分配执行`index`。 如果发生这种情况，为未初始化的值`index`将用作的偏移量`buffer`可能使攻击者读取越界敏感的信息并通过通过依赖加载的一侧信道传达此`shared_buffer`.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

void InitializeIndex(unsigned int trusted_index, unsigned int *index) {
    *index = trusted_index;
}

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int trusted_index) {
    unsigned int index;

    InitializeIndex(trusted_index, &index); // not inlined

    // SPECULATION BARRIER
    unsigned char value = buffer[index];
    return shared_buffer[value * 4096];
}
```

### <a name="speculative-uninitialized-use-leading-to-an-indirect-branch"></a>推理未初始化的使用，从而导致间接分支

推理的未初始化的使用可能会导致到间接分支的分支目标通过攻击者控制。 在以下示例中，`routine`分配给任一`DefaultMessageRoutine1`或`DefaultMessageRoutine`具体取决于值`mode`。 在体系结构的路径，这将导致`routine`始终间接分支之前初始化。 但是，具体取决于由编译器生成的代码，推理存储区绕过可能会发生，允许通过间接分支`routine`推测性地执行之前分配给`routine`。 如果发生这种情况，攻击者可能能够推测性地执行从任意地址，假定攻击者可以影响或控制的未初始化的值`routine`。

```cpp
#define MAX_MESSAGE_ID 16

typedef void (*MESSAGE_ROUTINE)(unsigned char *buffer, unsigned int buffer_size);

const MESSAGE_ROUTINE DispatchTable[MAX_MESSAGE_ID];
extern unsigned int mode;

void InitializeRoutine(MESSAGE_ROUTINE *routine) {
    if (mode == 1) {
        *routine = &DefaultMessageRoutine1;
    }
    else {
        *routine = &DefaultMessageRoutine;
    }
}

void DispatchMessage(unsigned int untrusted_message_id, unsigned char *buffer, unsigned int buffer_size) {
    MESSAGE_ROUTINE routine;

    InitializeRoutine(&routine); // not inlined

    // SPECULATION BARRIER
    routine(buffer, buffer_size);
}
```

## <a name="mitigation-options"></a>风险缓解选项

对源代码进行更改，可以缓解推理执行端道漏洞。 这些更改可能涉及到缓解特定实例的一个漏洞，如通过添加*推理屏障*，或通过更改设计应用程序以使敏感信息都无法访问推理执行。

### <a name="speculation-barrier-via-manual-instrumentation"></a>通过手动检测的推理屏障

一个*推理屏障*可以手动插入由开发人员以防止继续沿非体系结构路径的推理执行。 例如，开发人员可以在块的开头 （之后条件分支） 的条件块的正文中插入推理屏障前危险编码模式或之前考虑的问题是在首次加载。 这将阻止从序列化执行非体系结构的路径上执行的危险代码条件分支预测。 下表所述，推理屏障序列将不同的硬件体系结构：

|体系结构|推理屏障 CVE 2017-5753 内部函数|推理屏障 CVE 2018 3639 内部函数|
|----------------|----------------|----------------|
|x86/x64|_mm_lfence()|_mm_lfence()|
|ARM|当前不可用|__dsb(0)|
|ARM64|当前不可用|__dsb(0)|

例如，下面的代码模式可以通过使用在降低`_mm_lfence`内部函数，如下所示。

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        _mm_lfence();
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="speculation-barrier-via-compiler-time-instrumentation"></a>通过编译器时检测推理屏障

（从 15.5.5 版开始） 的 Visual Studio 2017 中 Visual c + + 编译器支持`/Qspectre`开关，这样将自动插入推理屏障的一组有限的潜在易受攻击的编码模式与相关的 CVE 2017-5753。 文档[/Qspectre](https://docs.microsoft.com/cpp/build/reference/qspectre)标志提供有关其效果和使用情况详细信息。 请务必请注意，此标志不涵盖所有可能有漏洞的编码模式，这种情况下开发人员不应依赖于它作为一种全面缓解此类漏洞。

### <a name="masking-array-indices"></a>屏蔽数组索引

在其中推理越界加载的情况下可能会出现，数组索引可以强受体系结构和非体系结构路径上添加逻辑以显式绑定的数组索引。 例如，如果数组可以分配到 2 的幂对齐的大小，然后简单掩码可以引入。 这其中假定下面的示例中所示`buffer_size`对齐到 2 的幂。 这可确保`untrusted_index`是始终小于`buffer_size`，即使条件分支预测发生并`untrusted_index`传递的值大于或等于`buffer_size`。

应注意这里执行的索引屏蔽，无法受到推理存储区绕过，具体取决于由编译器生成的代码。

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        untrusted_index &= (buffer_size - 1);
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="removing-sensitive-information-from-memory"></a>从内存中删除敏感信息

可以用来缓解推理执行端道漏洞的另一种方法是从内存中删除敏感信息。 软件开发人员可以寻找机会重构其应用程序，以便敏感信息在推理执行期间不可访问。 这可以通过重构设计应用程序隔离到单独的进程的敏感信息。 例如，web 浏览器应用程序可尝试隔离到单独的进程，从而防止一个进程可以访问通过推理执行跨域数据与每个 web 源关联的数据。

## <a name="see-also"></a>请参阅

[若要缓解推理执行旁道漏洞的指南](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002)<br/>
[防御推理执行端通道硬件漏洞](https://blogs.technet.microsoft.com/srd/2018/03/15/mitigating-speculative-execution-side-channel-hardware-vulnerabilities/)
