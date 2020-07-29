---
title: 用于推理执行端通道的 c + + 开发人员指南
ms.date: 07/10/2018
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
- Spectre
- CVE-2017-5753
- Speculative Execution
ms.openlocfilehash: d0b9faf0bd11892c05e25e981e8cd729cb623dd4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219321"
---
# <a name="c-developer-guidance-for-speculative-execution-side-channels"></a>用于推理执行端通道的 c + + 开发人员指南

本文包含一些指导，使开发人员能够帮助识别和缓解 c + + 软件中的推理执行端通道硬件漏洞。 这些漏洞可能会跨信任边界泄露敏感信息，并且可能会影响在支持推理、顺序外指令执行的处理器上运行的软件。 此类漏洞首先在2018年1月介绍，并在[Microsoft 安全公告](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002)中介绍。

本文提供的指南与以下各类的漏洞相关：

1. CVE-2017-5753，也称为 Spectre 变体1。 此硬件漏洞类与可能由于条件分支 misprediction 导致的推理执行引起的侧通道相关。 Visual Studio 2017 （从版本15.5.5 开始）中的 Microsoft c + + 编译器支持 `/Qspectre` 开关，该开关为与 CVE-2017-5753 相关的一组有限的可能易受攻击的编码模式提供编译时缓解。 `/Qspectre`Visual Studio 2015 Update 3 到[KB 4338871](https://support.microsoft.com/help/4338871)中也提供了该开关。 [/Qspectre](https://docs.microsoft.com/cpp/build/reference/qspectre)标志的文档提供了有关其效果和使用情况的详细信息。

2. CVE-2018-3639，也称为[推理存储绕过（SSB）](https://aka.ms/sescsrdssb)。 此硬件漏洞类与端通道相关，这可能是由于内存访问 misprediction 导致依赖存储的负载提前执行。

可在名为["Spectre" 和 "Meltdown](https://www.youtube.com/watch?v=_4O0zMW-Zu4) " 的演示文稿中找到可访问的推理执行端通道漏洞的简介，其中一个发现这些问题的研究团队。

## <a name="what-are-speculative-execution-side-channel-hardware-vulnerabilities"></a>什么是推理执行端通道硬件漏洞？

新式 Cpu 通过使用推理和顺序外指令执行来提供更高的性能。 例如，这通常通过预测分支的目标（条件和间接）来实现，这使得 CPU 可以在预测的分支目标上开始推测性执行指令，从而避免延迟，直到实际分支目标得到解决。 当 CPU 稍后发现发生了 misprediction 时，将放弃计算推测性的所有计算机状态。 这可确保误报推理没有结构上明显的效果。

尽管预测执行不会影响到结构化可见状态，但它可能会在非体系结构状态下保留残留跟踪，如 CPU 使用的各种缓存。 这是这些残留的推理执行跟踪，它们可能会导致向两侧通道漏洞。 为了更好地理解这一点，请考虑以下代码片段，其中提供了 CVE-2017-5753 （界限检查绕过）的示例：

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

在此示例中， `ReadByte` 提供缓冲区、缓冲区大小和缓冲区中的索引。 由指定的索引参数由 `untrusted_index` 特权较低的上下文提供，如非管理进程。 如果 `untrusted_index` 小于 `buffer_size` ，则将从中读取该索引处的字符 `buffer` 并将其用于索引到所引用的内存共享区域 `shared_buffer` 。

从体系结构的角度来看，此代码序列是完全安全的，因为它可以保证 `untrusted_index` 始终小于 `buffer_size` 。 但在存在推理执行的情况下，即使大于或等于，CPU 也可能会误预测条件分支并执行 if 语句的主体 `untrusted_index` `buffer_size` 。 这样做的结果是，CPU 可能推测性从超出范围 `buffer` （可能是机密）读取一个字节，然后可以使用该字节值通过计算后续加载的地址 `shared_buffer` 。

虽然 CPU 最终将检测到此 misprediction，但可以在 CPU 缓存中留下残留副作用，以揭示有关从中读取的字节值的相关信息 `buffer` 。 通过在系统上运行的特权较低的上下文来探测每个缓存行的访问速度，可以检测到这些副作用 `shared_buffer` 。 为实现此目的，可以采取的步骤如下：

1. ** `ReadByte` 多次调用， `untrusted_index` `buffer_size` 小于**。 攻击上下文可能会导致受害者上下文调用 `ReadByte` （例如，通过 RPC），以便对分支预测器进行定型，使其不会被视为 `untrusted_index` 小于 `buffer_size` 。

2. **刷新中的 `shared_buffer` 所有缓存行**。 攻击上下文必须在引用的内存的共享区域中刷新所有缓存行 `shared_buffer` 。 由于内存区域是共享的，因此这种方式很简单，可以使用内部函数（例如）来实现 `_mm_clflush` 。

3. 如果大于，则**调用。 `ReadByte` `untrusted_index` `buffer_size` ** 攻击上下文会导致受害者上下文调用，从而 `ReadByte` 不能预测不会执行该分支。 这会导致处理器推测性执行 if 块的正文，使其 `untrusted_index` 大于 `buffer_size` ，从而导致超出范围的读取 `buffer` 。 因此， `shared_buffer` 使用一个可能的机密值（在边界内读取）对其进行索引，从而导致 CPU 加载各自的缓存行。

4. **阅读中的每个缓存行 `shared_buffer` ，查看最快速访问的缓存行**。 攻击上下文可以读取中的每个缓存行 `shared_buffer` 并检测缓存行的加载速度明显快于其他缓存行。 这是可能已在步骤3中引入的缓存行。 由于在此示例中，字节值和缓存行之间存在1:1 关系，因此，攻击者可以推断出超出范围的字节的实际值。

以上步骤举例介绍了如何结合使用一种称为 "刷新 + 重新加载" 的技术，以及如何利用 CVE-2017-5753 的实例。

## <a name="what-software-scenarios-can-be-impacted"></a>哪些软件方案可能会受到影响？

使用[安全开发生命周期](https://www.microsoft.com/sdl/)（SDL）等过程开发安全软件通常要求开发人员确定其应用程序中存在的信任边界。 信任边界存在于应用程序可以与不受信任的上下文（如内核模式设备驱动程序的系统上的另一个进程或非管理用户模式进程）提供的数据进行交互的位置。 涉及推理执行端通道的一类新漏洞与现有软件安全模型中的许多信任边界相关，这些模型隔离设备上的代码和数据。

下表提供了软件安全模型的摘要，开发人员可能需要在这些模型中考虑这些漏洞：

|信任边界|描述|
|----------------|----------------|
|虚拟机边界|隔离不同虚拟机中的工作负荷的应用程序可能会有风险。|
|内核边界|从非管理用户模式进程接收不受信任数据的内核模式设备驱动程序可能有风险。|
|进程边界|从本地系统上运行的另一个进程（例如通过远程过程调用（RPC）、共享内存或其他进程间通信（IPC）机制）接收不受信任数据的应用程序可能有风险。|
|Enclave 边界|在安全 enclave （如 Intel SGX）内执行的应用程序从 enclave 外部接收不受信任的数据可能有风险。|
|语言边界|解释或实时（JIT）编译和执行以较高级别的语言编写的不受信任代码的应用程序可能存在风险。|

将攻击面暴露给上述任何信任边界的应用程序应查看攻击面上的代码，以确定并缓解可能的推理执行端通道漏洞的实例。 应注意的是，公开给远程攻击面（如远程网络协议）的信任边界未被解释为有可能导致执行端通道漏洞的风险。

## <a name="potentially-vulnerable-coding-patterns"></a>可能存在漏洞的编码模式

由于存在多个编码模式，推理执行端通道漏洞可能会引发。 本部分介绍可能易受到攻击的编码模式，并提供每个模式的示例，但应当认识到这些主题的变化可能存在。 因此，建议开发人员将这些模式作为示例，而不是所有可能易受到攻击的编码模式的详尽列表。 当前还可能存在于软件中的相同类内存安全漏洞，同时也存在于执行的推理和无序路径中，包括但不限于缓冲区溢出、超出范围的数组访问、未初始化的内存使用、类型混淆等。 攻击者可用于在结构路径上利用内存安全漏洞的相同基元还适用于推测路径。

一般情况下，如果条件表达式对可以通过不受信任的上下文控制或影响的数据进行操作，则可能会出现与条件分支 misprediction 相关的推理执行端通道。 例如，这可能包括 **`if`** 、 **`for`** 、、 **`while`** **`switch`** 或三元语句中使用的条件表达式。 对于上述每个语句，编译器可能会生成一个条件分支，CPU 可能会在运行时预测分支目标。

对于每个示例，将插入一个带有短语 "推理障碍" 的注释，开发人员可在其中引入屏障作为缓解措施。 这将在 "缓解措施" 一节中更详细地讨论。

## <a name="speculative-out-of-bounds-load"></a>推理超出界限负载

这种类型的编码模式涉及导致推理出边界内存访问的条件分支 misprediction。

### <a name="array-out-of-bounds-load-feeding-a-load"></a>阵列超出界限负载

此编码模式是最初为 CVE-2017-5753 （界限检查绕过）提供的易受攻击的编码模式。 本文的背景部分详细说明了此模式。

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

同样，数组超出界限的负载可能会与因 misprediction 而超出其终止条件的循环一起出现。 在此示例中， `x < buffer_size` 当大于或等于时，与表达式关联的条件分支可能误预测和推测性执行循环的主体 **`for`** `x` `buffer_size` ，从而导致推理出边界外加载。

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

### <a name="array-out-of-bounds-load-feeding-an-indirect-branch"></a>数组外接间接分支

这种编码模式涉及到这样一种情况：条件分支 misprediction 可能会导致对函数指针数组的边界外访问，这会导致间接进入超出范围的目标地址。 以下代码片段提供了演示此的示例。

在此示例中，通过参数提供了不受信任的消息标识符 DispatchMessage `untrusted_message_id` 。 如果 `untrusted_message_id` 小于，则 `MAX_MESSAGE_ID` 它用于索引函数指针的数组，并分支到相应的分支目标。 此代码在结构上是安全的，但如果 CPU 归属误预测条件分支，则可能会导致 `DispatchTable` 索引 `untrusted_message_id` 值大于或等于 `MAX_MESSAGE_ID` ，从而导致超出边界的访问。 这可能会导致从派生于数组界限的分支目标地址执行推理，这可能会导致信息泄露，具体取决于执行推测性的代码。

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

与数组外边界负载馈送其他负载一样，此情况也可能与因 misprediction 而超出其终止条件的循环一起出现。

### <a name="array-out-of-bounds-store-feeding-an-indirect-branch"></a>阵列超出范围的存储将间接分支送进

尽管上面的示例演示了推理出边界负载如何影响间接分支目标，但在边界外存储中也可能会修改间接分支目标，例如函数指针或返回地址。 这可能会导致从攻击者指定的地址执行推理。

在此示例中，通过参数传递不受信任的索引 `untrusted_index` 。 如果 `untrusted_index` 小于数组的元素计数 `pointers` （256个元素），则中提供的指针值 `ptr` 将写入到 `pointers` 数组中。 此代码在结构上是安全的，但如果 CPU 归属误预测条件分支，则可能会导致 `ptr` 推测性超出堆栈分配数组的界限 `pointers` 。 这可能导致的返回地址的推理损坏 `WriteSlot` 。 如果攻击者可以控制的值 `ptr` ，则当 `WriteSlot` 沿着推理路径返回时，它们可能会导致从任意地址执行推理。

```cpp
unsigned char WriteSlot(unsigned int untrusted_index, void *ptr) {
    void *pointers[256];
    if (untrusted_index < 256) {
        // SPECULATION BARRIER
        pointers[untrusted_index] = ptr;
    }
}
```

同样，如果在堆栈上分配了名为的函数指针本地变量 `func` ，则在 `func` 发生条件分支 misprediction 时，可能推测性修改引用的地址。 当通过调用函数指针时，这可能会导致从任意地址执行推理。

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

应注意的是，这两个示例都涉及对堆栈分配的间接分支指针的推理修改。 对于全局变量、堆分配的内存，甚至某些 Cpu 上的只读内存，也可能会发生推理修改。 对于堆栈分配的内存，Microsoft c + + 编译器已经执行了一些步骤，使其更难推测性修改堆栈分配的间接分支目标，例如通过对本地变量进行重新排序，以便将缓冲区作为[/gs](https://docs.microsoft.com/cpp/build/reference/gs-buffer-security-check)编译器安全功能的一部分放置在安全 cookie 旁边。

## <a name="speculative-type-confusion"></a>推理类型混淆

此类别处理可为推测类型产生混乱的代码模式。 当在推理执行期间使用不正确的类型在非结构路径中访问内存时，会发生这种情况。 条件分支 misprediction 和推理存储绕过可能会导致推理类型混淆。

对于忽略的推理存储，在编译器重用多个类型变量的堆栈位置的情况下可能会发生这种情况。 这是因为类型的变量的体系结构存储 `A` 可能被绕过，因此，在赋值之前，允许将类型的负载加载 `A` 到推测性中。 如果以前存储的变量属于不同类型，则可以为推测类型混淆创建条件。

对于条件分支 misprediction，下面的代码段将用于描述推理类型混淆可给出的不同条件。

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

### <a name="speculative-type-confusion-leading-to-an-out-of-bounds-load"></a>推理类型产生的混乱导致超出界限负载

这种编码模式涉及到推测类型混淆的情况下，可能会导致超出界限或无类型混淆的字段访问，其中加载的值将馈送到后续的加载地址。 这类似于数组外边界编码模式，但它是通过替代编码序列列出的，如上所述。 在此示例中，攻击上下文可能会导致受害者上下文多次 `ProcessType` 与类型的对象 `CType1` （ `type` 字段等于）一起执行 `Type1` 。 这会使第一条语句的条件分支定型 **`if`** ，而不是要预测的结果。 然后，攻击上下文可能会导致受害者上下文 `ProcessType` 与类型的对象一起执行 `CType2` 。 如果第一条语句的条件分支 **`if`** 归属误预测并执行语句的主体 **`if`** ，从而将类型的对象强制转换为，则会导致推理类型混淆 `CType2` `CType1` 。 由于小于 `CType2` `CType1` ，内存访问 `CType1::field2` 将导致推理出的数据可能是秘密的，这可能是机密的。 然后，将在负载中使用此值 `shared_buffer` ，以便创建可观察到的副作用，就像前面所述的数组外界示例一样。

### <a name="speculative-type-confusion-leading-to-an-indirect-branch"></a>推理类型导致间接分支的混乱

这种编码模式涉及到推测类型混淆的情况下，在推理执行期间可能导致不安全的间接分支。 在此示例中，攻击上下文可能会导致受害者上下文多次 `ProcessType` 与类型的对象 `CType2` （ `type` 字段等于）一起执行 `Type2` 。 这会使为要采用的第一 **`if`** 条语句和不采用的语句定型的条件分支进行定型 `else if` 。 然后，攻击上下文可能会导致受害者上下文 `ProcessType` 与类型的对象一起执行 `CType1` 。 如果第一条语句的条件分支预测到并不执行该语句，则这可能导致推理类型混淆 **`if`** `else if` ，从而执行的主体 `else if` 和将类型的对象转换 `CType1` 为 `CType2` 。 由于 `CType2::dispatch_routine` 字段与 **`char`** 数组重叠，因此 `CType1::field1` 这可能会导致推理出的间接分支到非预期的分支目标。 如果攻击上下文可以控制数组中的字节值 `CType1::field1` ，则它们可能能够控制分支目标地址。

## <a name="speculative-uninitialized-use"></a>推理未初始化使用

这种类型的编码模式涉及到这样的情况：推理执行可能会访问未初始化的内存，并使用它来馈送后续的 load 或间接分支。 若要利用这些编码模式，攻击者需要能够控制或有意义地影响使用的内存的内容，而无需由其使用的上下文进行初始化。

### <a name="speculative-uninitialized-use-leading-to-an-out-of-bounds-load"></a>推理为未初始化的使用，导致超出界限负载

未初始化的推理使用可能会使用攻击者控制的值导致超出界限的负载。 在下面的示例中，的值 `index` `trusted_index` 在所有体系结构路径上分配，并且 `trusted_index` 假定小于或等于 `buffer_size` 。 但是，根据编译器生成的代码，可能会绕过推理存储，这允许从 `buffer[index]` 和从属表达式到的赋值提前执行 `index` 。 如果发生这种情况，将使用的未初始化值 `index` 作为偏移量， `buffer` 从而使攻击者可以读取超出界限的敏感信息，并通过的从属通道通过侧通道传达此信息 `shared_buffer` 。

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

### <a name="speculative-uninitialized-use-leading-to-an-indirect-branch"></a>推理为间接分支的未初始化的使用

未初始化的推理使用可能会导致间接分支，分支目标由攻击者控制。 在下面的示例中， `routine` 将分配到 `DefaultMessageRoutine1` 或， `DefaultMessageRoutine` 具体取决于的值 `mode` 。 在体系结构路径上，这将导致 `routine` 始终在间接分支之前进行初始化。 但是，根据编译器生成的代码，可能会绕过推理存储区，以便在 `routine` 赋值前推测性执行间接分支 `routine` 。 如果发生这种情况，攻击者可能能够从任意地址推测性执行，前提是攻击者可以影响或控制的未初始化值 `routine` 。

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

## <a name="mitigation-options"></a>缓解选项

可以通过对源代码进行更改来降低推理执行端通道漏洞。 这些更改可能涉及到缓解了某个漏洞的特定实例，如添加*推理关卡*，或对应用程序的设计进行了更改，以使推理的执行无法访问敏感信息。

### <a name="speculation-barrier-via-manual-instrumentation"></a>通过手动检测的推理障碍

开发人员可以手动插入*推理屏障*，以防止在非结构化路径中执行推理。 例如，开发人员可以在条件块体中的危险编码模式之前插入推理关卡，无论是在块的开头（条件分支之后），还是在第一个需要考虑的负载之前。 这会阻止条件分支 misprediction 通过序列化执行来执行非结构路径上的危险代码。 推理关卡序列不同于下表所述的硬件体系结构：

|体系结构|CVE 关卡内部函数-2017-5753|CVE 关卡内部函数-2018-3639|
|----------------|----------------|----------------|
|x86/x64|_mm_lfence （）|_mm_lfence （）|
|ARM|当前不可用|__dsb （0）|
|ARM64|当前不可用|__dsb （0）|

例如，以下代码模式可以使用内部函数进行缓解，如下 `_mm_lfence` 所示。

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

### <a name="speculation-barrier-via-compiler-time-instrumentation"></a>通过编译器时间检测的推理障碍

Visual Studio 2017 （从版本15.5.5 开始）中的 Microsoft c + + 编译器包含对开关的支持， `/Qspectre` 该开关自动为与 CVE-2017-5753 相关的一组有限的受攻击的代码模式插入推理屏障。 [/Qspectre](https://docs.microsoft.com/cpp/build/reference/qspectre)标志的文档提供了有关其效果和使用情况的详细信息。 请务必注意，此标志并不涵盖所有可能易受到威胁的编码模式，因此，开发人员不应将其作为此类漏洞的全面缓解措施。

### <a name="masking-array-indices"></a>屏蔽数组索引

如果可能出现推理出边界负载，则数组索引可以通过添加逻辑来显式绑定数组索引，从而对结构和非体系结构路径进行强限制。 例如，如果可以将数组分配给大小，使之与2的幂对齐，则可以引入简单的掩码。 下面的示例演示了这一点，在此示例中，假定 `buffer_size` 已与2的幂对齐。 这可确保 `untrusted_index` 始终小于 `buffer_size` ，即使条件分支 misprediction 发生且 `untrusted_index` 传入的值大于或等于 `buffer_size` 。

应注意的是，在此处执行的索引掩码可能会根据编译器生成的代码，绕过推理存储区。

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

可用于缓解推理执行端通道漏洞的另一种方法是从内存中删除敏感信息。 软件开发人员可以寻找重构应用程序的机会，以便在推理执行期间不能访问敏感信息。 这可以通过重构应用程序的设计来实现，以将敏感信息隔离到单独的进程中。 例如，web 浏览器应用程序可以尝试将与每个 web 源关联的数据隔离到不同的进程中，从而防止一个进程通过推理执行来访问跨源数据。

## <a name="see-also"></a>另请参阅

[用于缓解推理执行方通道漏洞的指南](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002)<br/>
[减少推理执行端通道硬件漏洞](https://blogs.technet.microsoft.com/srd/2018/03/15/mitigating-speculative-execution-side-channel-hardware-vulnerabilities/)
