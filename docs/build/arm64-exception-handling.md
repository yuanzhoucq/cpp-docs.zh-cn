---
title: ARM64 异常处理
description: 描述 windows 在 ARM64 上使用的异常处理约定和数据。
ms.date: 11/19/2018
ms.openlocfilehash: 1ed147a27cfeb545e2a5fe265df8113a5befac73
ms.sourcegitcommit: 170f5de63b0fec8e38c252b6afdc08343f4243a6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72276832"
---
# <a name="arm64-exception-handling"></a>ARM64 异常处理

ARM64 上的 Windows 对异步硬件生成的异常和同步软件生成的异常使用相同的结构化异常处理机制。 将通过使用语言帮助器函数，基于 Windows 结构化异常处理来生成特定于语言的异常处理程序。 本文档介绍了 Windows on ARM64 中的异常处理，以及由 Microsoft ARM 组装器和 MSVC 编译器生成的代码所使用的语言帮助程序。

## <a name="goals-and-motivation"></a>目标和动机

异常展开数据约定和此描述旨在：

1. 提供足够的描述以允许在所有情况下不进行代码探测的情况下进行展开。

   - 分析代码需要对代码进行分页。 这会阻止在某些情况下（跟踪、采样、调试）的展开。

   - 分析代码非常复杂;编译器必须注意仅生成展开器可以解码的指令。

   - 如果无法通过使用展开代码来完全描述展开，则在某些情况下，必须回退到指令解码。 这会增加总体复杂性，理想情况下应避免这样做。

1. 支持中间序言和中的展开。

   - 在 Windows 中使用展开以实现异常处理。 即使是在 prolog 或 epilog 代码序列中间，代码也能准确地展开。

1. 占用最少的空间。

   - 展开代码不得进行聚合以大幅增加二进制大小。

   - 由于展开代码可能在内存中被锁定，因此，占用的空间较小，可确保每个加载的二进制文件的开销最小。

## <a name="assumptions"></a>假设

在异常处理说明中进行了以下假设：

1. Prolog 和 epilogs 趋向于进行镜像。 利用这种常见的特性，描述展开所需的元数据大小会大幅降低。 在函数体中，无论是否撤消序言操作，都不重要，或者是否以向前的方式完成 epilog 的操作。 这两种操作应产生完全相同的结果。

1. 函数通常是相对较小的。 空间的多个优化依赖于这一事实来实现最有效的数据打包。

1. Epilogs 中没有条件代码。

1. 专用帧指针注册：如果 sp 保存在序言中的另一个寄存器（x29）中，则该寄存器在整个函数中保持不变。 这意味着，可以随时恢复原始 sp。

1. 除非将 sp 保存在另一个寄存器中，否则堆栈指针的所有操作都将严格出现在 prolog 和 epilog 中。

1. 堆栈帧布局按下一部分所述的方式进行组织。

## <a name="arm64-stack-frame-layout"></a>ARM64 堆栈帧布局

![堆栈帧布局](media/arm64-exception-handling-stack-frame.png "堆栈帧布局")

对于帧链接函数，可以在本地变量区域中的任意位置保存 fp 和 lr 对，具体取决于优化注意事项。 目标是最大程度地提高可通过帧指针（x29）或堆栈指针（sp）的单个指令达到的局部变量的数目。 但是，对于 `alloca` 函数，该函数必须链接在一起，并且 x29 必须指向堆栈的底部。 若要允许更好地注册到寻址模式，非易失寄存器保存区位于本地区域堆栈的顶部。 下面的示例演示了几个最有效的 prolog 序列。 为清楚起见和更好地缓存区域，在所有规范 prolog 中存储被调用方保存的寄存器的顺序均为 "增长"。 以下 `#framesz` 表示整个堆栈的大小（不包括 alloca 区域）。 `#localsz` 和 `#outsz` 表示本地区域大小（包括 \<x29、lr > 对的保存区域）和传出参数大小。

1. 链式 #localsz \<= 512

    ```asm
        stp    x19,x20,[sp,#-96]!        // pre-indexed, save in 1st FP/INT pair
        stp    d8,d9,[sp,#16]            // save in FP regs (optional)
        stp    x0,x1,[sp,#32]            // home params (optional)
        stp    x2,x3,[sp,#48]
        stp    x4,x5,[sp,#64]
        stp    x6,x7,[sp,#72]
        stp    x29,lr,[sp,#-localsz]!   // save <x29,lr> at bottom of local area
        mov    x29,sp                   // x29 points to bottom of local
        sub    sp,sp,#outsz             // (optional for #outsz != 0)
    ```

1. 链式 #localsz > 512

    ```asm
        stp    x19,x20,[sp,#-96]!        // pre-indexed, save in 1st FP/INT pair
        stp    d8,d9,[sp,#16]            // save in FP regs (optional)
        stp    x0,x1,[sp,#32]            // home params (optional)
        stp    x2,x3,[sp,#48]
        stp    x4,x5,[sp,#64]
        stp    x6,x7,[sp,#72]
        sub    sp,sp,#(localsz+outsz)   // allocate remaining frame
        stp    x29,lr,[sp,#outsz]       // save <x29,lr> at bottom of local area
        add    x29,sp,#outsz            // setup x29 points to bottom of local area
    ```

1. 非链式，叶函数（lr 未保存）

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]
        str    x23,[sp,#32]
        stp    d8,d9,[sp,#40]           // save FP regs (optional)
        stp    d10,d11,[sp,#56]
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   所有局部变量都基于 SP 进行访问。 \<x29，lr > 指向上一帧。 对于帧大小 \<= 512，"sub sp ..."如果 regs 保存的区域移到堆栈底部，则可以将其优化掉。 缺点是它与上面的其他布局不一致，并且已保存的 regs 在 regs 和预索引和索引后偏移寻址模式的范围内。

1. 非链式，非叶函数（lr 保存在 Int 个保存区域中）

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]         // ...
        stp    x23,lr,[sp,#32]          // save last Int reg and lr
        stp    d8,d9,[sp,#48]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,#64]         // ...
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   或者，对于偶数保存的 Int 寄存器，

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]         // ...
        str    lr,[sp,#32]              // save lr
        stp    d8,d9,[sp,#40]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,#56]         // ...
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   仅保存 x19：

    ```asm
        sub    sp,sp,#16                // reg save area allocation*
        stp    x19,lr,[sp]              // save x19, lr
        sub    sp,sp,#(framesz-16)      // allocate the remaining local area
    ```

   \* reg 保存区域分配不会折叠为 stp，因为预索引的 reg-lr stp 不能使用展开代码表示。

   所有局部变量都基于 SP 进行访问。 \<x29 > 指向前一帧。

1. 链式，#framesz \<= 512，#outsz = 0

    ```asm
        stp    x29,lr,[sp,#-framesz]!       // pre-indexed, save <x29,lr>
        mov    x29,sp                       // x29 points to bottom of stack
        stp    x19,x20,[sp,#(framesz-32)]   // save INT pair
        stp    d8,d9,[sp,#(framesz-16)]     // save FP pair
    ```

   与上面的第一个序言示例相比，这里的优点是所有注册保存指令都可以在只有一个堆栈分配指令后执行。 这意味着，在 sp 上不会有阻止指令级并行的任何反依赖关系。

1. 链式，帧大小 > 512 （可为不带 alloca 的函数选择）

    ```asm
        stp    x29,lr,[sp,#-80]!            // pre-indexed, save <x29,lr>
        stp    x19,x20,[sp,#16]             // save in INT regs
        stp    x21,x22,[sp,#32]             // ...
        stp    d8,d9,[sp,#48]               // save in FP regs
        stp    d10,d11,[sp,#64]
        mov    x29,sp                       // x29 points to top of local area
        sub    sp,sp,#(framesz-80)          // allocate the remaining local area
    ```

   对于优化目的，可以将 x29 置于本地区域中的任意位置，以提供更好的 "reg 对" 和/post-indexed 偏移寻址模式的覆盖范围。 可根据 SP 访问以下可访问的帧指针。

1. 链式，帧大小 > 4K，有或不包含 alloca （）、

    ```asm
        stp    x29,lr,[sp,#-80]!            // pre-indexed, save <x29,lr>
        stp    x19,x20,[sp,#16]             // save in INT regs
        stp    x21,x22,[sp,#32]             // ...
        stp    d8,d9,[sp,#48]               // save in FP regs
        stp    d10,d11,[sp,#64]
        mov    x29,sp                       // x29 points to top of local area
        mov    x15,#(framesz/16)
        bl     __chkstk
        sub    sp,sp,x15,lsl#4              // allocate remaining frame
                                            // end of prolog
        ...
        sub    sp,sp,#alloca                // more alloca() in body
        ...
                                            // beginning of epilog
        mov    sp,x29                       // sp points to top of local area
        ldp    d10,d11,[sp,#64]
        ...
        ldp    x29,lr,[sp],#80              // post-indexed, reload <x29,lr>
    ```

## <a name="arm64-exception-handling-information"></a>ARM64 异常处理信息

### <a name="pdata-records"></a>。 pdata 记录

Pdata 记录是固定长度项的有序数组，用于描述 PE 二进制文件中的每个堆栈操作函数。 短语 "堆栈操作" 非常重要：叶函数不需要任何本地存储，并且无需保存/还原非易失性寄存器，无需 pdata 记录。 为了节省空间，应显式省略这些记录。 从此类函数之一展开会直接从 LR 获取返回地址，以向上移动到调用方。

ARM64 的每个 pdata 记录的长度为8个字节。 每个记录的常规格式会将函数的32位 RVA 置于第一个单词中，然后是第二个单词，其中包含指向 xdata 块的指针或描述规范函数展开序列的打包单词。

![pdata 记录]布局(media/arm64-exception-handling-pdata-record.png "pdata 记录布局")

字段如下所示：

- **函数 START rva**是函数开头的32位 rva。

- **标记**是一个2位字段，它指示如何解释 pdata word 的剩余30位。 如果**标志**为0，则剩余的位将形成**异常信息 RVA** （这两个最低位隐式为0）。 如果**标志**为非零，则剩余的位构成一个**打包的展开数据**结构。

- **异常信息 RVA**是 xdata 部分中存储的可变长度异常信息结构的地址。 此数据必须是对齐的 4 字节。

- 已**打包的展开数据**是从函数展开所需操作的压缩说明，假定规范格式。 在这种情况下，不需要任何 .xdata 记录。

### <a name="xdata-records"></a>。 xdata 记录

当已打包的展开格式不足以描述函数的展开时，必须创建长度可变的 .xdata 记录。 该记录的地址存储在 .pdata 记录的第二个字中。 . Xdata 的格式为打包的可变长度单词集：

![xdata 记录]布局(media/arm64-exception-handling-xdata-record.png "xdata 记录布局")

此数据分为四部分：

1. 1或2个 word 标题，描述结构的总体大小并提供关键函数数据。 仅当 " **Epilog 计数**" 和 "**代码字**" 字段都设置为0时，才会显示第二个单词。 标头包含以下位域：

   a. **函数长度**是一个18位字段。 它指示函数的总长度（以字节为单位）除以4。 如果函数大于1M，则必须使用多个. pdata 和 xdata 记录来描述函数。 有关详细信息，请参阅[大型函数](#large-functions)部分。

   b. 使用**的是 2**位字段。 它描述了 xdata 的版本。 目前仅定义版本0，因此不允许使用值1-3。

   c. **X**是一个1位字段。 它指示存在（1）或缺少异常数据（0）。

   d. **E**是一个1位字段。 它表示描述单个 epilog 的信息被打包到标头（1）中，而不是以后需要其他作用域字（0）。

   e. **Epilog Count**是一个5位字段，它具有两种含义，具体取决于**E**位的状态：

      1. 如果**E**为0，则它指定第2部分中所述的 epilog 作用域总数的计数。 如果函数中存在超过31个作用域，则 "**代码字**" 字段必须设置为0，以指示需要一个扩展词。

      2. 如果**E**为1，则此字段指定第一个展开代码的索引，该索引仅描述 epilog。

   f. **代码字**是一个5位字段，它指定在第3部分中包含所有展开代码所需的32位字的数目。 如果需要的单词超过31个（即，如果有超过124个展开代码字节），则此字段必须为0以指示需要一个扩展字。

   g. **扩展的 Epilog 计数**和**扩展的代码字**分别为16位和8位字段。 它们为编码非常大的 epilogs 提供更多的空间，或大量的展开代码单词。 仅当第一个标头字中的**Epilog Count**和**Code Words**字段均为0时，才会出现包含这些字段的扩展名单词。

1. 如果**Epilog 计数**不为零，则在标头和可选扩展标头后，有关 epilog 作用域的信息列表（打包到一个词）。 它们按增加的起始偏移顺序存储。 每个作用域都包含以下位：

   a. **Epilog 开始偏移量**是一个18位字段，该字段的偏移量（以字节为单位），相对于函数的开头，epilog 除以4。

   b. **Res**是保留供将来扩展的4位字段。 其值必须为 0。

   c. **Epilog 开始索引**是一个10位字段（比**扩展的代码字**多2位）。 它指示描述此 epilog 的第一个展开代码的字节索引。

1. 当 epilog 范围列表中包含展开代码的字节数组后，将在后面的部分中详细说明。 在最接近的全字边界的末尾处填充此数组。 展开代码将写入此数组。 它们从最接近函数主体的一开始，然后移至函数的边缘。 每个展开代码的字节以大字节序顺序存储，因此可以直接从最重要的字节开始提取，这会标识操作和剩余代码的长度。

1. 最后，在展开代码字节之后，如果标头中的**X**位设置为1，则会出现异常处理程序信息。 它包含单个**异常处理程序 RVA** ，后者提供异常处理程序本身的地址。 其后紧跟异常处理程序所需的可变长度数据量。

Xdata 记录经过设计后，就可以提取前8个字节，并使用它们来计算记录的完整大小，减去下面的可变大小异常数据的长度。 下面的代码段计算记录大小：

```cpp
ULONG ComputeXdataSize(PULONG *Xdata)
{
    ULONG EpilogScopes;
    ULONG Size;
    ULONG UnwindWords;

    if ((Xdata[0] >> 27) != 0) {
        Size = 4;
        EpilogScopes = (Xdata[0] >> 22) & 0x1f;
        UnwindWords = (Xdata[0] >> 27) & 0x0f;
    } else {
        Size = 8;
        EpilogScopes = Xdata[1] & 0xffff;
        UnwindWords = (Xdata[1] >> 16) & 0xff;
    }

    Size += 4 * EpilogScopes;
    Size += 4 * UnwindWords;
    if (Xdata[0] & (1 << 20)) {
        Size += 4;        // exception handler RVA
    }
    return Size;
}
```

尽管 prolog 和每个 epilog 在展开代码中都有其自己的索引，但在它们之间共享该表。 完全可以（但不太常见）它们都可以共享相同的代码。 （有关示例，请参阅 "[示例](#examples)" 部分中的示例2。）特别是，对于这种情况，编译器编写器应进行优化，因为可以指定的最大索引为255，这会限制特定函数的展开代码的总数。

### <a name="unwind-codes"></a>展开代码

展开代码的数组是一组序列，用于描述如何撤消序言的效果，以与操作需要撤消的相同顺序存储。 展开代码可以视为一个小指令集，编码为字节字符串。 执行完成后，调用函数的返回地址位于 lr 寄存器中。 在调用函数时，所有非易失性寄存器都还原为其值。

如果保证异常仅出现在函数体中，而不是出现在 prolog 或任何 epilog 内，则只需要一个序列。 但是，Windows 展开模型要求代码可以从部分执行的 prolog 或 epilog 中展开。 为了满足此要求，已仔细设计了展开代码，因此它们清楚地将1:1 映射到序言和 epilog 中的每个相关操作码。 此设计具有几个含义：

1. 通过对展开代码的数量进行计数，可以计算 prolog 和 epilog 的长度。

1. 通过计算某个 epilog 范围开始后的指令数，可以跳过相当数量的展开代码。 然后，可以执行序列的其余部分以完成由 epilog 完成的部分执行的展开。

1. 通过对 prolog 末尾之前的指令数进行计数，可以跳过等效数目的展开代码。 然后，可以执行序列的其余部分，以仅撤消 prolog 中已完成执行的部分。

展开代码按下表进行编码。 所有展开代码都是单个/双字节，只不过分配了一个大型堆栈。 完全有21个展开代码。 每个展开代码只映射 prolog/epilog 中的一个指令，以允许对部分执行的 prolog 和 epilogs 进行展开。

|展开代码|位和解释|
|-|-|
|`alloc_s`|000xxxxx：分配小堆栈，大小为 \< 512 （2 ^ 5 * 16）。|
|`save_r19r20_x`|    001zzzzz： save \<x19，x20 > 对，`[sp-#Z*8]!`，预索引偏移 > =-248 |
|`save_fplr`|        01zzzzzz：将 \<x29，lr > 对 `[sp+#Z*8]`，偏移 \<= 504。 |
|`save_fplr_x`|        10zzzzzz：将 \<x29、lr > 对保存在 `[sp-(#Z+1)*8]!`，预索引偏移 > =-512 |
|`alloc_m`|        11000xxx'xxxxxxxx：分配大堆栈，大小 \< 16k （2 ^ 11 * 16）。 |
|`save_regp`|        110010xx'xxzzzzzz：保存 x （19 + #X）对，`[sp+#Z*8]`，偏移 \<= 504 |
|`save_regp_x`|        110011xx'xxzzzzzz：在 `[sp-(#Z+1)*8]!`，按预索引的偏移量 > =-512 保存对 x （19 + #X） |
|`save_reg`|        110100xx'xxzzzzzz：将 reg x （19 + #X）保存 `[sp+#Z*8]`，偏移量 \<= 504 |
|`save_reg_x`|        1101010x'xxxzzzzz：将 reg x （19 + #X）保存 `[sp-(#Z+1)*8]!`，预先索引的偏移量 > =-256 |
|`save_lrpair`|         1101011x'xxzzzzzz： save 对 \<x （19 + 2 * #X），lr > `[sp+#Z*8]`，偏移量 \<= 504 |
|`save_fregp`|        1101100x'xxzzzzzz：保存对 d （8 + #X），`[sp+#Z*8]`，偏移量 \<= 504 |
|`save_fregp_x`|        1101101x'xxzzzzzz： save 对 d （8 + #X），`[sp-(#Z+1)*8]!`，预索引偏移量 > =-512 |
|`save_freg`|        1101110x'xxzzzzzz：将 reg d （8 + #X）保存 `[sp+#Z*8]`，偏移量 \<= 504 |
|`save_freg_x`|        11011110 ' xxxzzzzz：将 reg d （8 + #X）保存在 `[sp-(#Z+1)*8]!`的预索引偏移 > =-256 |
|`alloc_l`|         11100000 ' xxxxxxxx'xxxxxxxx'xxxxxxxx：分配大小 \< 为256M 的大型堆栈（2 ^ 24 * 16） |
|`set_fp`|        11100001：设置 x29： with： `mov x29,sp` |
|`add_fp`|        11100010 ' xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx： set with： `add x29,sp,#x*8` |
|`nop`|            11100011：不需要展开操作。 |
|`end`|            11100100：展开代码结束。 隐含 epilog 中的 ret。 |
|`end_c`|        11100101：当前链式范围内的展开代码结束。 |
|`save_next`|        11100110：保存下一个非易失性 Int 或 FP 寄存器对。 |
|`arithmetic(add)`|    11100111 ' 000zxxxx：将 cookie reg （z）添加到 lr （0 = x28，1 = sp）;`add lr, lr, reg(z)` |
|`arithmetic(sub)`|    11100111 ' 001zxxxx： lr 的子 cookie reg （z）（0 = x28，1 = sp）;`sub lr, lr, reg(z)` |
|`arithmetic(eor)`|    11100111 ' 010zxxxx： eor lr with cookie reg （z）（0 = x28，1 = sp）;`eor lr, lr, reg(z)` |
|`arithmetic(rol)`|    11100111 ' 0110xxxx： lr with cookie reg （x28）的模拟角色;xip0 = neg x28;`ror lr, xip0` |
|`arithmetic(ror)`|    11100111 ' 100zxxxx： ror lr with cookie reg （z）（0 = x28，1 = sp）;`ror lr, lr, reg(z)` |
| |            11100111： xxxz----：----保留 |
| |              11101xxx：为以下自定义堆栈事例保留：仅为 asm 例程生成 |
| |              11101000： MSFT_OP_TRAP_FRAME 的自定义堆栈 |
| |              11101001： MSFT_OP_MACHINE_FRAME 的自定义堆栈 |
| |              11101010： MSFT_OP_CONTEXT 的自定义堆栈 |
| |              11101100： MSFT_OP_CLEAR_UNWOUND_TO_CALL 的自定义堆栈 |
| |              1111xxxx：已保留 |

在包含多个字节的较大值的说明中，最重要的位将先存储。 此设计使你可以通过只查找代码的第一个字节来查找展开代码的总大小（以字节为单位）。 由于每个展开代码都完全映射到 prolog 或 epilog 中的指令，因此，您可以计算 prolog 或 epilog 的大小。 您可以从序列的开头到末尾进行遍历，并使用查找表或类似设备确定相应操作码的时间长度。

Prolog 中不允许使用索引后的偏移量。 除 `save_r19r20_x`以外，所有偏移范围（#Z）都匹配 STP/STR 寻址的编码，在这种情况下，248足以满足所有保存区域（10个 Int 寄存器 + 8 个 FP 寄存器 + 8 个输入寄存器）。

`save_next` 必须遵循 Int 或 FP 可变寄存器对的保存： `save_regp`、`save_regp_x`、`save_fregp`、`save_fregp_x`、`save_r19r20_x`或其他 `save_next`。 它将下一个寄存器对保存在 "增长" 顺序中的下一个16字节槽。 `save_next` 指的是第一个 FP 寄存器对，如果它跟在 `save-next`，表示最后一个 Int 寄存器对。

由于常规返回和跳转指令的大小相同，因此不需要对尾调用方案使用分离 `end` 展开代码。

`end_c` 旨在出于优化目的处理不连续的函数片段。 一个 `end_c`，指示当前作用域中的展开代码的结束时间必须后跟另一个展开代码序列，该序列以真实 `end`结束。 `end_c` 和 `end` 之间的展开代码表示父区域（"虚拟" 序言）中的序言运算。  下面的部分介绍了更多详细信息和示例。

### <a name="packed-unwind-data"></a>已打包的展开数据

对于 prolog 和 epilogs 遵循下面所述的规范形式的函数，可以使用打包的展开数据。 它完全无需 xdata 记录，并且大大降低了提供展开数据的成本。 规范 prolog 和 epilogs 旨在满足简单函数的常见要求：一个不需要异常处理程序，并按标准顺序执行其设置和拆卸操作。

具有打包的展开数据的 pdata 记录的格式如下所示：

包含打包的展开数据的![pdata 记录](media/arm64-exception-handling-packed-unwind-data.png "。具有打包的展开数据的 pdata 记录")

字段如下所示：

- **函数 START rva**是函数开头的32位 rva。
- **标记**是上面所述的一个2位字段，具有以下含义：
  - 00 = 未使用已打包的展开数据;剩余的位指向 xdata 记录
  - 01 = 在范围的开头和结尾使用单个 prolog 和 epilog 使用的打包展开数据
  - 10 = 用于代码的已打包的展开数据，无任何 prolog 和 epilog。 用于描述分隔函数段
  - 11 = 保留。
- **函数长度**是一个11位字段，它提供整个函数的长度（以字节为单位）除以4。 如果函数大于8k，则必须改为使用 xdata 记录。
- **帧大小**是一个9位字段，它指示为此函数分配的堆栈的字节数除以16。 分配的 stack 大于（8k-16）字节的函数必须使用 xdata 记录。 它包括本地变量区域、传出参数区域、被调用方保存的 Int 和 FP 区域以及 home 参数区域，但不包括动态分配区域。
- **CR**是一个2位标志，它指示函数是否包含用于设置帧链和返回链接的额外说明：
  - 00 = 非链式函数、\<x29、lr > 对未保存在堆栈中。
  - 01 = 非链式函数，\<lr > 保存在堆栈中
  - 10 = 保留;
  - 11 = 链式函数，用于 prolog/epilog \<x29，lr >
- **H**是一个1位标志，它指示函数是否通过将整数参数存储在函数的最开头来注册（x 7）。 （0 = 不是 home 寄存器，1 = home 寄存器）。
- **O**是一个4位字段，它指示在规范堆栈位置中保存的非易失性 INT 寄存器（x19）数。
- **RegF**是一个3位字段，它指示在规范堆栈位置中保存的非易失性 FP 寄存器（d15）的数量。 （RegF = 0：不保存 FP 注册;RegF > 0：已保存 RegF + 1 FP 寄存器。 打包的展开数据不能用于仅保存一个 FP 寄存器的函数。

属于类别1、2（无传出参数区域）、第3部分和第4节中的规范 prolog 可以使用打包展开格式表示。  Epilogs for 规范函数遵循类似的形式，但**H**不起作用，将省略 `set_fp` 指令，并在 epilog 中反转每个步骤的步骤顺序和说明。 Xdata 的算法遵循下表中所述的步骤：

步骤0：预计算每个区域的大小。

步骤1：保存 Int 被调用方保存的寄存器。

步骤2：此步骤特定于早期部分中的类型4。 lr 保存在 Int 区域末尾。

步骤3：保存 FP 被调用方保存的寄存器。

步骤4：将输入参数保存到 home 参数区域。

步骤5：分配剩余的堆栈，包括本地区域、\<x29、lr > 对和传出参数区域。 5a 对应于规范类型1。 5b 和5c 适用于规范类型2。 5d 和5e 用于类型3和类型4。

分步#|标志值|指令数|操作码|展开代码
-|-|-|-|-
0|||`#intsz = RegI * 8;`<br/>`if (CR==01) #intsz += 8; // lr`<br/>`#fpsz = RegF * 8;`<br/>`if(RegF) #fpsz += 8;`<br/>`#savsz=((#intsz+#fpsz+8*8*H)+0xf)&~0xf)`<br/>`#locsz = #famsz - #savsz`|
1|0 < **o** < = 10|O/2 + **o** %2|`stp x19,x20,[sp,#savsz]!`<br/>`stp x21,x22,[sp,#16]`<br/>`...`|`save_regp_x`<br/>`save_regp`<br/>`...`
2|**CR**==01*|1|`str lr,[sp,#(intsz-8)]`\*|`save_reg`
3|0 < **RegF** < = 7|（RegF + 1）/2 +<br/>（RegF + 1） %2）|`stp d8,d9,[sp,#intsz]`\*\*<br/>`stp d10,d11,[sp,#(intsz+16)]`<br/>`...`<br/>`str d(8+RegF),[sp,#(intsz+fpsz-8)]`|`save_fregp`<br/>`...`<br/>`save_freg`
4|**H** = = 1|4|`stp x0,x1,[sp,#(intsz+fpsz)]`<br/>`stp x2,x3,[sp,#(intsz+fpsz+16)]`<br/>`stp x4,x5,[sp,#(intsz+fpsz+32)]`<br/>`stp x6,x7,[sp,#(intsz+fpsz+48)]`|`nop`<br/>`nop`<br/>`nop`<br/>`nop`
5a|**CR** = = 11 & & #locsz<br/> < = 512|2|`stp x29,lr,[sp,#-locsz]!`<br/>`mov x29,sp`\*\*\*|`save_fplr_x`<br/>`set_fp`
5b|**CR** = = 11 & &<br/>512 < #locsz < = 4080|3|`sub sp,sp,#locsz`<br/>`stp x29,lr,[sp,0]`<br/>`add x29,sp,0`|`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5c|**CR** = = 11 & & #locsz > 4080|4|`sub sp,sp,4080`<br/>`sub sp,sp,#(locsz-4080)`<br/>`stp x29,lr,[sp,0]`<br/>`add x29,sp,0`|`alloc_m`<br/>`alloc_s`/`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5d|（**Cr** = = 00 \|\| **CR**= = 01） & &<br/>#locsz <= 4080|1|`sub sp,sp,#locsz`|`alloc_s`/`alloc_m`
5e|（**Cr** = = 00 \|\| **CR**= = 01） & &<br/>#locsz > 4080|2|`sub sp,sp,4080`<br/>`sub sp,sp,#(locsz-4080)`|`alloc_m`<br/>`alloc_s`/`alloc_m`

\* 如果**CR** = = 01 且**o**为奇数，步骤1中的步骤2和最后 save_rep 将合并为一个 save_regp。

\*\* 如果**o** == **CR** = = 0， **RegF** ！ = 0，则浮点的第一个 stp 执行前置减量。

\*\*\* epilog 中不存在与 `mov x29,sp` 对应的指令。 如果函数需要从 x29 还原 sp，则不能使用打包的展开数据。

### <a name="unwinding-partial-prologs-and-epilogs"></a>展开部分 prolog 和 epilogs

最常见的展开情况是：异常或调用出现在函数体中，远离序言和所有 epilogs。 在这种情况下，展开非常简单：展开器只是从索引0开始执行展开数组中的代码，然后继续，直到检测到结束操作码。

如果在执行序言或 epilog 时发生异常或中断，则更难正确地展开。 在这些情况下，仅部分构造堆栈帧。 问题在于正确地确定要执行的操作。

例如，采用以下序言和 epilog 序列：

```asm
0000:    stp    x29,lr,[sp,#-256]!          // save_fplr_x  256 (pre-indexed store)
0004:    stp    d8,d9,[sp,#224]             // save_fregp 0, 224
0008:    stp    x19,x20,[sp,#240]           // save_regp 0, 240
000c:    mov    x29,sp                      // set_fp
         ...
0100:    mov    sp,x29                      // set_fp
0104:    ldp    x19,x20,[sp,#240]           // save_regp 0, 240
0108:    ldp    d8,d9,[sp,224]              // save_fregp 0, 224
010c:    ldp    x29,lr,[sp],#256            // save_fplr_x  256 (post-indexed load)
0110:    ret    lr                          // end
```

每个操作码旁边都是描述此操作的相应展开代码。 您可以看到 prolog 的展开代码序列是 epilog 的展开代码的精确镜像（不计算 epilog 的最后一条指令）。 这是一种常见情况，这就是为什么我们始终以为 prolog 的展开代码按与序言的执行顺序相反的顺序存储的原因。

因此，对于序言和 epilog，我们保留一组通用的展开代码：

`set_fp`, `save_regp 0,240`, `save_fregp,0,224`, `save_fplr_x_256`, `end`

Epilog case 非常简单，因为它按正常顺序排列。 从 epilog 内的偏移量0开始（在函数中的偏移0x100 处开始），我们希望执行完全展开序列，因为尚未执行任何清理操作。 如果在中找到了单一指令（在 epilog 中为 offset 2），则可以通过跳过第一个展开代码来成功展开。 我们可以通用化这种情况，并假设操作码和展开代码之间的映射为1:1。 然后，若要从 epilog 中的指令*n*开始展开，应跳过前*n*个展开代码，并从该处开始执行。

事实证明，类似的逻辑适用于序言，但反向运算除外。 如果从序言中的偏移量0开始展开，则不需要执行任何操作。 如果我们从第2个偏移量（这是中的一个指令）展开，则我们希望开始从末尾执行展开序列。 （请记住，代码按相反的顺序存储。）而且，我们还可以通用化：如果从序言中的指令 n 开始展开，应开始从代码列表的末尾执行 n 展开代码。

Prolog 和 epilog 代码并非总是完全匹配。 这就是，展开数组可能需要包含多个代码序列的原因。 若要确定开始处理代码的位置的偏移量，请使用以下逻辑：

1. 如果从函数体中展开，则在索引0处开始执行展开代码，并继续，直到遇到 "end" 操作码。

1. 如果从 epilog 内展开，请使用与 epilog 范围一起提供的 epilog 特定的起始索引作为起始点。 计算有问题的 PC 从 epilog 开始的字节数。 然后，在展开代码中向前推进，直到已执行所有已执行的指令。 然后从该点开始执行。

1. 如果从序言中展开，请使用索引0作为起始点。 计算序列中 prolog 代码的长度，然后计算该 PC 的相关数量从 prolog 末尾的字节数。 然后，在展开代码中向前推进，直到执行所有尚未执行的指令。 然后从该点开始执行。

这些规则意味着 prolog 的展开代码必须始终为数组中的第一个。 而且，它们也是从正文中展开的一般情况下使用的代码。 任何 epilog 特定的代码序列应紧随其后。

### <a name="function-fragments"></a>函数片段

出于代码优化目的和其他原因，最好将函数拆分为分隔片段（也称为区域）。 拆分时，每个生成的函数片段都需要各自的 pdata （可能为 xdata）记录。

对于具有自己的序言的每个单独的辅助片段，其序言中不会进行任何堆栈调整。 次要区域所需的所有堆栈空间都必须由其父区域（或称为主机区域）预先分配。 这会在函数的原始序言中严格保持堆栈指针的操作。

函数片段的典型情况是 "代码分离"，因为编译器可能会将代码区域移出其宿主函数。 有三种异常情况可能会导致代码分离。

#### <a name="example"></a>示例

- （region 1： begin）

    ```asm
        stp     x29,lr,[sp,#-256]!      // save_fplr_x  256 (pre-indexed store)
        stp     x19,x20,[sp,#240]       // save_regp 0, 240
        mov     x29,sp                  // set_fp
        ...
    ```

- （区域1：结束）

- （区域3：开始）

    ```asm
        ...
    ```

- （区域3：结束）

- （region 2： begin）

    ```asm
        ...
        mov     sp,x29                  // set_fp
        ldp     x19,x20,[sp,#240]       // save_regp 0, 240
        ldp     x29,lr,[sp],#256        // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- （区域2：结束）

1. 仅限 Prolog （region 1：所有 epilogs 都在单独的区域中）：

   仅必须描述序言。 这不能以 pdata 格式表示。 在 xdata 情况下，它可以通过设置 Epilog Count = 0 来表示。 请参阅上述示例中的区域1。

   展开代码： `set_fp`、`save_regp 0,240`、`save_fplr_x_256``end`。

1. 仅限 Epilogs （区域2： prolog 位于主机区域）

   假设时间控件跳转到此区域，则已执行所有 prolog 代码。 部分展开在 epilogs 中的执行方式与在正常函数中发生的方式相同。 此类型的区域不能由 pdata 表示。 在 xdata 记录中，它可以使用 "虚拟" 序言码进行编码，由 `end_c` 和 `end` 展开代码对括起来。  前导 `end_c` 指示 prolog 的大小为零。 每个 epilog 点的 epilog 开始索引要 `set_fp`。

   区域2： `end_c`、`set_fp`、`save_regp 0,240`、`save_fplr_x_256`、`end`的展开代码。

1. 没有 prolog 或 epilogs （区域3： prolog，并且所有 epilogs 都在其他片段中）：

   可以通过设置标志 = 10 应用 pdata 格式。 对于 xdata 记录，Epilog 计数 = 1。 展开代码与上面区域2的代码相同，但是 Epilog 开始索引还指向 `end_c`。 部分展开操作永远不会发生在此代码区域中。

函数片段的另一种更复杂的情况是 "收缩环绕"。 编译器可以选择延迟将一些被调用方保存的寄存器保存到函数入口 prolog 之外。

- （region 1： begin）

    ```asm
        stp     x29,lr,[sp,#-256]!      // save_fplr_x  256 (pre-indexed store)
        stp     x19,x20,[sp,#240]       // save_regp 0, 240
        mov     x29,sp                  // set_fp
        ...
    ```

- （region 2： begin）

    ```asm
        stp     x21,x22,[sp,#224]       // save_regp 2, 224
        ...
        ldp     x21,x22,[sp,#224]       // save_regp 2, 224
    ```

- （区域2：结束）

    ```asm
        ...
        mov     sp,x29                  // set_fp
        ldp     x19,x20,[sp,#240]       // save_regp 0, 240
        ldp     x29,lr,[sp],#256        // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- （区域1：结束）

在区域1的序言中，堆栈空间已预先分配。 你可以看到，区域2将具有相同的展开代码，即使它已移出其主机函数。

区域1： `set_fp`，`save_regp 0,240`，`save_fplr_x_256`，与 Epilog 开始索引点 `end` 按平时 `set_fp`。

区域2： `save_regp 2, 224`、`end_c`、`set_fp`、`save_regp 0,240`、`save_fplr_x_256`、`end`。 Epilog 开始索引点到首个展开代码 `save_regp 2, 224`。

### <a name="large-functions"></a>大型函数

片段可用于描述大于 xdata 标头中位域施加的1M 限制的函数。 若要描述此类函数，需要将它分解为小于1M 的片段。 应调整每个片段，使其不会将 epilog 拆分为多个部分。

只有函数的第一个片段将包含序言;所有其他片段都标记为没有序言码。 根据 epilogs 的数量，每个片段可能包含零个或多个 epilogs。 请记住，片段中的每个 epilog 范围指定了相对于片段起始位置的起始偏移，而不是函数的开头。

如果片段没有序言并且没有 epilog，则它仍需要 pdata （xdata）记录，以描述如何从函数主体内部展开。

## <a name="examples"></a>示例

### <a name="example-1-frame-chained-compact-form"></a>示例1：框架链接，紧凑形式

```asm
|Foo|     PROC
|$LN19|
    str     x19,[sp,#-0x10]!        // save_reg_x
    sub     sp,sp,#0x810            // alloc_m
    stp     fp,lr,[sp]              // save_fplr
    mov     fp,sp                   // set_fp
                                    //  end of prolog
    ...

|$pdata$Foo|
    DCD     imagerel     |$LN19|
    DCD     0x416101ed
    ;Flags[SingleProEpi] functionLength[492] RegF[0] RegI[1] H[0] frameChainReturn[Chained] frameSize[2080]
```

### <a name="example-2-frame-chained-full-form-with-mirror-prolog--epilog"></a>示例2：框架链接型、完整形式的镜像 Prolog & Epilog

```asm
|Bar|     PROC
|$LN19|
    stp     x19,x20,[sp,#-0x10]!    // save_regp_x
    stp     fp,lr,[sp,#-0x90]!      // save_fplr_x
    mov     fp,sp                   // set_fp
                                    // end of prolog
    ...
                                    // begin of epilog, a mirror sequence of Prolog
    mov     sp,fp
    ldp     fp,lr,[sp],#0x90
    ldp     x19,x20,[sp],#0x10
    ret     lr

|$pdata$Bar|
    DCD     imagerel     |$LN19|
    DCD     imagerel     |$unwind$cse2|
|$unwind$Bar|
    DCD     0x1040003d
    DCD     0x1000038
    DCD     0xe42291e1
    DCD     0xe42291e1
    ;Code Words[2], Epilog Count[1], E[0], X[0], Function Length[6660]
    ;Epilog Start Index[0], Epilog Start Offset[56]
    ;set_fp
    ;save_fplr_x
    ;save_r19r20_x
    ;end
```

Epilog 开始索引 [0] 指向相同的序言展开代码序列。

### <a name="example-3-variadic-unchained-function"></a>示例3：可变参数非链式函数

```asm
|Delegate| PROC
|$LN4|
    sub     sp,sp,#0x50
    stp     x19,lr,[sp]
    stp     x0,x1,[sp,#0x10]        // save incoming register to home area
    stp     x2,x3,[sp,#0x20]        // ...
    stp     x4,x5,[sp,#0x30]
    stp     x6,x7,[sp,#0x40]        // end of prolog
    ...
    ldp     x19,lr,[sp]             // beginning of epilog
    add     sp,sp,#0x50
    ret     lr

    AREA    |.pdata|, PDATA
|$pdata$Delegate|
    DCD     imagerel |$LN4|
    DCD     imagerel |$unwind$Delegate|

    AREA    |.xdata|, DATA
|$unwind$Delegate|
    DCD     0x18400012
    DCD     0x200000f
    DCD     0xe3e3e3e3
    DCD     0xe40500d6
    DCD     0xe40500d6
    ;Code Words[3], Epilog Count[1], E[0], X[0], Function Length[18]
    ;Epilog Start Index[4], Epilog Start Offset[15]
    ;nop        // nop for saving in home area
    ;nop        // ditto
    ;nop        // ditto
    ;nop        // ditto
    ;save_lrpair
    ;alloc_s
    ;end
```

Epilog 开始索引 [4] 指向序言展开代码的中间（部分重复使用展开数组）。

## <a name="see-also"></a>另请参阅

[ARM64 ABI 约定概述](arm64-windows-abi-conventions.md)<br/>
[ARM 异常处理](arm-exception-handling.md)
