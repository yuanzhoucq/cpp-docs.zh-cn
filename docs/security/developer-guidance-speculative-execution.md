---
title: 推理执行端通道的 c + + 开发人员指南 |Microsoft 文档
ms.custom: ''
ms.date: 05/03/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
- Spectre
- CVE-2017-5753
- Speculative Execution
author: mamillmsft
ms.author: mikeblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0a7e7ddb51f07f7fe6be1da017d8feae9cc4919e
ms.sourcegitcommit: 96cdc2da0d8c3783cc2ce03bd280a5430e1ac01d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="c-developer-guidance-for-speculative-execution-side-channels"></a>推理执行端通道的 c + + 开发人员指南

本文包含用于帮助识别和缓解推测执行端通道硬件漏洞 c + + 软件中的开发人员指南。 这些漏洞可以跨信任边界泄露的敏感信息，并可能会影响在支持推理、 扩展的顺序执行的指令处理器运行的软件。 漏洞此类是年 1 月，2018年中所述的第一个和其他背景和指南可在[Microsoft 安全公告](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002)。

本文提供的指南与漏洞 CVE-自 2017 年 1-5753，也称为 Spectre variant 1 所表示的类。 此硬件漏洞类与端通道可能会出现由于条件分支预测时，会出现的推测执行。 Visual c + + 编译器 （从版本 15.5.5 开始） 的 Visual Studio 2017 中包括对支持`/Qspectre`交换机提供有限的一组潜在易受攻击的编码模式与 CVE 2017 5753 编译时缓解。 文档[/Qspectre](https://docs.microsoft.com/en-us/cpp/build/reference/qspectre)标志提供有关其效果和用法的详细信息。 

标题为演示文稿中找不到的可访问推测执行端通道漏洞简介[Spectre 用例和垮台](https://www.youtube.com/watch?v=_4O0zMW-Zu4)研究团队发现这些问题之一。

## <a name="what-are-speculative-execution-side-channel-hardware-vulnerabilities"></a>推理执行端通道硬件漏洞有哪些？

现代 Cpu 通过使提供的性能更高程度的推理和扩展的顺序来执行指令的使用。 例如，这是通常通过实现预测使 CPU 可开始推理执行预测的分支目标，从而避免停止，直到实际分支目标上的说明进行操作的目标的分支 （条件和 indrect）解析。 中，CPU 更高版本发现预测发生时，所有推理计算得出的计算机状态将被丢弃。 这可确保有已撤销的误报推理没有体系结构上可见效果。

虽然推测执行不会影响 architecturaly 可见状态，它可能处于非体系结构的状态，例如 CPU 使用的各种缓存会导致残留的跟踪。 很可能会引起端通道漏洞的推测执行这些残留跟踪。 若要更好地理解这一点，请考虑下面的代码段，其中提供了示例 CVE 2017 5753 （边界检查绕过）：

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

在此示例中，`ReadByte`是提供到该缓冲区的缓冲区、 缓冲区大小和索引。 索引参数，按指定`untrusted_index`，由小于特权的上下文，例如非管理的过程。 如果`untrusted_index`是小于`buffer_size`，则该索引处的字符读取从`buffer`且用于索引到共享所引用的内存区域`shared_buffer`。

从体系结构的角度来看，此代码序列是完全安全如则可保证`untrusted_index`将始终小于`buffer_size`。 但是，在推测执行，存在很可能 CPU 将 mispredict 条件分支和执行主体 if 语句，即使`untrusted_index`大于或等于`buffer_size`。 因此，CPU 可以推理读取一个字节的边界 from beyond `buffer` （可以是机密），然后可以使用该字节值来计算通过后续负载的地址`shared_buffer`。 

虽然 CPU 最终将检测此预测，剩余的副作用可能会处于泄漏超出界限从读取的字节值的相关信息的 CPU 缓存`buffer`。 小于可以检测到这些副作用通过速度探测系统上运行的特权的上下文行中的每个缓存`shared_buffer`访问。 完成此操作时可以执行的步骤如下：

1. **调用`ReadByte`多次使用`untrusted_index`正在小于`buffer_size`** 。 攻击上下文可能会导致要调用的牺牲品上下文`ReadByte`（例如通过 RPC) 如分支的预测指标是训练后将不作为原`untrusted_index`是小于`buffer_size`。

2. **刷新中的所有缓存行`shared_buffer`** 。 攻击上下文必须刷新所有的共享所引用的内存区域中的缓存行`shared_buffer`。 由于共享的内存区域，这非常简单，并可使用内部函数，如实现`_mm_clflush`。

3. **调用`ReadByte`与`untrusted_index`大于`buffer_size`** 。 攻击上下文导致牺牲品的上下文调用`ReadByte`以便正确预测将使分支。 这会导致处理器推理执行 if 正文块`untrusted_index`大于`buffer_size`，因此从而导致超出边界读取的`buffer`。 因此，`shared_buffer`使用可能机密读取值超出边界，从而导致要加载的 CPU 的各自的缓存行编制索引。

4. **读取中的每个缓存行`shared_buffer`若要查看最快的速度访问它**。 攻击上下文可以读取中的每个缓存行`shared_buffer`和检测的速度比其他显著加快加载的缓存行。 这是可能步骤 3 引入的缓存行。 由于此示例中的字节值和缓存行之间存在 1:1 的关系，这可让攻击者推断超出边界读取的字节的实际值。

上述步骤提供使用称为结合利用 CVE 2017 5753 的实例的刷新 + 重新加载的方法的示例。

## <a name="what-software-scenarios-can-be-impacted"></a>哪些软件方案可能会受到影响？

开发使用类似的进程的安全软件[安全开发生命周期](https://www.microsoft.com/en-us/sdl/)(SDL) 通常要求开发人员来标识在其应用程序中存在的信任边界。 信任边界存在于其中应用程序可能会与不太受信任的上下文，如在系统上的另一个进程或非管理用户模式进程在内核模式设备驱动程序的情况下提供的数据交互的地方。 中的信任边界隔离代码和设备上的数据的现有软件安全模型中的许多相关漏洞涉及推测执行端通道的新类。

下表提供了开发人员可能需要加以注意有关发生这些漏洞的软件安全模型的摘要：

|信任边界|描述|
|----------------|----------------|
|虚拟机边界|隔离在接收来自另一个虚拟机不受信任的数据的单独虚拟机中的工作负荷的应用程序可能有风险。|
|内核边界|从非管理用户模式进程接收不受信任的数据的内核模式设备驱动程序可能有风险。|
|进程边界|接收的应用程序不受信任的数据来自另一个进程运行在本地系统上，例如通过远程过程调用 (RPC)、 共享的内存或其他进程间通信 (IPC) 机制可能有风险。|
|Enclave 边界|在接收不受信任的数据从外部 enclave 可能有风险安全 enclave （例如 Intel SGX) 内执行应用程序。|
|语言边界|解释的应用程序或实时 (JIT) 编译和执行不受信任的代码编写的更高级别的语言可能有风险。|

攻击面公开到上述任一信任边界应查看的受攻击面，以识别和缓解推测执行端通道漏洞的可能的实例上的代码的应用程序。 应注意的是信任边界公开给远程攻击面，如远程网络协议，具有已未演示，若要有推测执行端通道漏洞的风险。

## <a name="potentially-vulnerable-coding-patterns"></a>可能易受攻击的编码模式

因此多个编码模式可能产生推测执行端通道安全漏洞。 本部分介绍可能易受攻击的编码模式，并举例说明了每个，但无法识别这些主题上的变体，可能会存在。 在这种情况下，开发人员建议采用这些模式作为示例，而不是所有潜在易受攻击的编码模式的穷举列表。

一般情况下，在可以控制或受不太受信任的上下文数据上执行的条件表达式时，可能会出现推测执行端通道相关的条件分支预测。 例如，这可能包括在中使用的条件表达式`if`， `for`， `while`， `switch`，或三元语句。 对于每个这些语句，编译器可能会生成 CPU 然后可能预测的分支目标在运行时的条件分支。

对于每个示例中，插入注释以与短语"推理屏障"开发人员可能会引入一个屏障作为一项缓解措施。 此部分中的详细地讨论上缓解措施。

### <a name="speculative-out-of-bounds-load"></a>推理超出边界加载

这种类别的编码模式涉及将导致推理超出边界条件分支预测内存访问。

#### <a name="array-out-of-bounds-load-feeding-a-load"></a>数组超出边界负载将传送负载

此编码模式是最初所述的易受攻击编码模式，用于 CVE 2017 5753 （边界检查绕过）。 此文章的背景部分介绍详细信息在此模式。

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

同样，数组超出边界加载可能发生在结合超过其终止的循环条件由于预测。 在此示例中，与关联的条件分支`x < buffer_size`表达式可能 mispredict 和推理执行主体`for`循环时`x`大于或等于`buffer_size`，因此结果为推理超出边界加载。

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadBytes(unsigned char *buffer, unsigned int buffer_size) {
    for (unsigned int x = 0; x < buffer_size; x++) {
        // SPECULATION BARRIER
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

#### <a name="array-out-of-bounds-load-feeding-an-indirect-branch"></a>数组超出边界负载将传送间接分支

此编码模式涉及条件分支预测可能导致这种情况的间接分支到目标的然后潜在客户地址的函数指针的数组访问超出边界读取超出边界。 以下代码片段提供的示例，说明了这一点。 

在此示例中，不受信任的消息标识符提供给通过 DispatchMessage`untrusted_message_id`参数。 如果`untrusted_message_id`是小于`MAX_MESSAGE_ID`，则它将使用到的函数指针的数组索引并分支到相应的分支目标。 此代码是安全的体系结构上，但如果 CPU mispredicts 条件分支，则可能导致`DispatchTable`要编制索引的`untrusted_message_id`时其值为大于或等于`MAX_MESSAGE_ID`，因此从而导致超出边界访问。 这可能导致推测执行发件人超出数组边界的这可能导致信息泄露，具体取决于推理执行的代码与派生分支目标地址。

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

随着使用超出边界的数组的大小写负载将传送另一种负载，这种情况也可能发生结合超过由于预测其终止条件的循环。

### <a name="speculative-type-confusion"></a>推理类型混淆

这种类别的编码模式涉及导致推理类型混淆条件分支预测。 下面的示例代码将引用此部分中的编码模式。

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

#### <a name="speculative-type-confusion-leading-to-an-out-of-bounds-load"></a>推理类型混淆，从而导致超出边界加载

此编码模式涉及在推理类型混淆可能导致这种情况超出边界或其中加载的值馈送后续负载地址类型混淆字段访问。 这是类似于数组超出边界编码模式，但出现通过编码序列，如上所示的替代方法。 在此示例中，攻击上下文可能会导致要执行的牺牲品上下文`ProcessType`多次使用类型的对象`CType1`(`type`字段等于`Type1`)。 这将产生定型的第一个条件分支的效果`if`语句来预测不执行。 攻击上下文可以导致要执行的牺牲品上下文`ProcessType`类型的对象`CType2`。 这可能会导致推理类型混淆，如果条件的第一个分支`if`语句 mispredicts 并执行的正文`if`语句，因此强制转换类型的对象`CType2`到`CType1`。 由于`CType2`小于`CType1`，内存访问`CType1::field2`将导致推理超出边界加载的可能是机密的数据。 此值随后可用于从负载`shard_buffer`明显的副作用，创建与数组超出边界示例前面所述。

#### <a name="speculative-type-confusion-leading-to-an-indirect-branch"></a>推理类型混淆通向间接分支

此编码模式涉及其中推理类型混淆可能会导致不安全的间接分支中过程推测执行这种情况。 在此示例中，攻击上下文可能会导致要执行的牺牲品上下文`ProcessType`多次使用类型的对象`CType2`(`type`字段等于`Type2`)。 这将产生定型的第一个条件分支的效果`if`要执行的语句和`else if`不要执行的语句。 攻击上下文可以导致要执行的牺牲品上下文`ProcessType`类型的对象`CType1`。 这可能会导致推理类型混淆，如果条件的第一个分支`if`预测语句执行和`else if`语句预测不执行，因此执行的正文`else if`和类型的对象强制转换`CType1`到`CType2`。 由于`CType2::dispatch_routine`字段与重叠`char`数组`CType1::field1`，这可能导致推理间接分支到意外的分支的目标。 如果攻击上下文可以控制中的字节值`CType1::field1`数组，他们可能能够控制的分支目标地址。

## <a name="mitigation-options"></a>缓解选项

通过对源代码进行更改，可以减轻推测执行端通道漏洞。 这些更改可能涉及缓解特定实例的一个漏洞，如通过添加*推理屏障*，或通过设计的应用程序，以使敏感信息的访问推理进行更改执行。

### <a name="speculation-barrier-via-manual-instrumentation"></a>通过手动检测推理屏障

A*推理屏障*可以由开发人员可以防止继续沿非体系结构的路径从推测执行手动插入。 例如，开发人员可以插入推理屏障危险的编码模式之前，在条件块，块的开头 （之后条件分支） 在正文中指定日期或之前的问题是在首次加载。 这将阻止从通过序列化执行在非体系结构的路径上执行的危险代码条件分支预测。 下表所述，推理屏障序列将不同的硬件体系结构：

|体系结构|推理屏障|
|----------------|----------------|
|x86/x64|_mm_lfence()|
|ARM|当前不可用|
|ARM64|当前不可用|


例如，下面的代码模式可以通过使用减轻`_mm_lfence`内部函数，如下所示。

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

### <a name="speculation-barrier-via-compiler-time-instrumentation"></a>通过编译时检测推理屏障

Visual c + + 编译器 （从版本 15.5.5 开始） 的 Visual Studio 2017 中包括对支持`/Qspectre`开关，它会自动插入一组有限的潜在易受攻击的编码模式推理屏障与 CVE 2017 5753 相关。 文档[/Qspectre](https://docs.microsoft.com/en-us/cpp/build/reference/qspectre)标志提供有关其效果和用法的详细信息。 请务必注意，此标志不涵盖所有可能易受攻击的编码模式，这种情况下开发人员不应依赖于它作为此类漏洞全面缓解措施。

### <a name="removing-sensitive-information-from-memory"></a>从内存中删除敏感信息

可用于减少推测执行端通道漏洞的另一种方法是从内存中删除敏感信息。 软件开发人员可以查找的机会以便重新调整其应用程序，以便敏感信息在推测执行期间不可访问。 这可以通过重构应用程序隔离到单独的进程的敏感信息的设计。 例如，web 浏览器应用程序可以尝试隔离到单独的过程，从而防止一个进程无法访问通过推测执行跨域数据与每个 web 源关联的数据。

## <a name="see-also"></a>请参阅

[若要缓解推测执行端通道漏洞的指南](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002)

[缓解推测执行端通道硬件漏洞](https://blogs.technet.microsoft.com/srd/2018/03/15/mitigating-speculative-execution-side-channel-hardware-vulnerabilities/)
