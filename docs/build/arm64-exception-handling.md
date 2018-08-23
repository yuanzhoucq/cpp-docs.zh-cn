---
title: ARM64 异常处理 |Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e24997fa2eb6e6e5c3d8438b137e168c2f70b1f
ms.sourcegitcommit: 9ad287c88bdccee2747832659fe50c2e5d682a0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2018
ms.locfileid: "39034733"
---
# <a name="arm64-exception-handling"></a>ARM64 异常处理

Windows 在 ARM64 上的使用相同的结构化的异常处理机制，用于异步硬件生成的异常和同步软件生成的异常。 将通过使用语言帮助器函数，基于 Windows 结构化异常处理来生成特定于语言的异常处理程序。 本文档介绍 ARM64 和由 Microsoft ARM 汇编程序和 Visual c + + 编译器生成的代码使用的语言帮助器上的 Windows 中的异常处理。

## <a name="goals-and-motivation"></a>目标和动机

异常展开数据约定，并且此说明被目的如下：

1. 提供足够的说明，以允许展开而无需在所有情况下探测代码。

   - 分析代码需要的代码中分页。 这可以防止在某些情况下，必要时展开 （跟踪、 采样、 调试）。

   - 分析代码很复杂;编译器必须注意仅生成展开器能够解码的说明。

   - 如果展开无法完整地说明了通过使用展开代码，然后在某些情况下它必须故障回复到指令解码。 这提高了整体复杂性，并在理想情况下会避免使用。

2. 在中间的 prolog 中展开和中间 epilog 的支持。

   - 展开对多个异常处理在 Windows 中使用，因此很重要，我们必须能够执行准确展开甚至时序列中间的 prolog 或 epilog 代码。

3. 占用最少量的空间。

   - 展开代码必须不聚合可显著提高二进制的大小。

   - 由于展开代码有可能被锁定在内存中，内存占用较小可确保每个加载的二进制文件的最小的开销。

## <a name="assumptions"></a>假设

以下是中的异常处理说明所做的假设：

1. Prolog 和 epilog 往往镜像或者其他。 通过充分利用此常见特征，可以大大减小描述展开所需的元数据的大小。 该函数体内，并不重要序言中的操作是撤消，还是以前进的方式执行 epilog 的操作。 这两种操作应产生完全相同的结果。

2. 函数通常对整个相对较小。 空间的多个优化依赖这以实现最有效地打包数据。

3. 在 epilog 中没有任何条件代码。

4. 专用帧指针寄存器： sp 保存在 prolog 中的另一个寄存器 (r29) 中，如果的注册保持在整个函数，保持不变，以便可以随时恢复原始 sp。

5. 除非 sp 保存在另一个寄存器中，所有操作的堆栈指针的 prolog 和 epilog 中严格的都发生。

6. 堆栈帧布局被组织的下一节中所述。

## <a name="arm64-stack-frame-layout"></a>ARM64 堆栈帧布局

![堆栈帧布局](../build/media/arm64-exception-handling-stack-frame.png "堆栈帧布局")

对于链接在一起的帧的函数，可以根据优化注意事项的本地变量区域中的任何位置保存 fp 和 lr 对。 目标是最大化的局部变量可以达到通过基于帧指针 (r29) 或堆栈指针 (sp) 的一个单个指令的数量。 但是对于`alloca`函数必须链接和 r29 必须指向堆栈的底部。 若要允许更多寄存器-对-寻址的模式下，非易失性注册的 aave 区域放置于本地区域堆栈的顶部。 下面是示例，展示了几个最有效的 prolog 序列。 为了明确和更好的缓存区域，便于在所有规范的 prolog 中存储被调用方保存的寄存器的顺序是按"增长设置"的顺序。 `#framesz` 下面表示整个堆栈 （不包括 alloca 区域） 的大小。 `#localsz` 并`#outsz`表示本地区域的大小 (包括保存区域\<r29，lr > 对) 和分别传出参数大小。

1. 链接在一起，#localsz < = 512

    ```asm
        stp    r19,r20,[sp,-96]!        // pre-indexed, save in 1st FP/INT pair
        stp    d8,d9,[sp,16]            // save in FP regs (optional)
        stp    r0,r1,[sp,32]            // home params (optional)
        stp    r2,r3,[sp, 48]
        stp    r4,r5,[sp,64]
        stp    r6,r7,[sp,72]
        stp    r29, lr, [sp, -#localsz]!    // save <r29,lr> at bottom of local area
        mov    r29,sp                   // r29 points to bottom of local
        sub    sp, #outsz               // (optional for #outsz != 0)
    ```

2. 链接在一起，#localsz > 512

    ```asm
        stp    r19,r20,[sp,-96]!        // pre-indexed, save in 1st FP/INT pair
        stp    d8,d9,[sp,16]            // save in FP regs (optional)
        stp    r0,r1,[sp,32]            // home params (optional)
        stp    r2,r3,[sp, 48]
        stp    r4,r5,[sp,64]
        stp    r6,r7,[sp,72]
        sub    sp,#localsz+#outsz       // allocate remaining frame
        stp    r29, lr, [sp, #outsz]    // save <r29,lr> at bottom of local area
        add    r29,sp, #outsz           // setup r29 points to bottom of local area
    ```

3. 非链接，叶函数 (未保存的 lr)

    ```asm
        stp    r19,r20,[sp, -72]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    r21,r22,[sp, 16]
        str    r23 [sp,32]
        stp    d8,d9,[sp,40]            // save FP regs (optional)
        stp    d10,d11,[sp,56]
        sub    sp,#framesz-72           // allocate the remaining local area
    ```

   所有局部变量访问基于 sp。 \<r29，lr > 指向上一帧。 帧大小 < = 512，"sub sp，..."可以被优化掉 regs 保存区域移到堆栈的底部。 缺点是范围的它不是范围的与更高版本，其他布局一致，并保存的 regs 采取对 regs 和前和后索引偏移量的寻址模式的一部分。

4. 非链接、 非叶函数 （lr 保存在保存 Int 区域）

    ```asm
        stp    r19,r20,[sp,-80]!        // pre-indexed, save in 1st FP/INT reg-pair
        stp    r21,r22,[sp,16]          // ...
        stp    r23, lr,[sp, 32]         // save last Int reg and lr
        stp    d8,d9,[sp, 48]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,64]          // ...
        sub    sp,#framesz-80           // allocate the remaining local area
    ```

   或带有偶数已保存 Int 寄存器

    ```asm
        stp    r19,r20,[sp,-72]!        // pre-indexed, save in 1st FP/INT reg-pair
        stp    r21,r22,[sp,16]          // ...
        str    lr,[sp, 32]              // save lr
        stp    d8,d9,[sp, 40]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,56]          // ...
        sub    sp,#framesz-72           // allocate the remaining local area
    ```

    仅保存 r19:

    ```asm
        sub    sp, sp, #16              // reg save area allocation*
        stp    r19,lr,[sp,0]            // save r19, lr
        sub    sp,#framesz-16           // allocate the remaining local area
    ```

   \* 因为不能使用展开代码表示预索引的 reg lr stp stp 到区域分配保存 reg 不折叠。

   所有局部变量访问基于 sp。 \<r29 > 指向上一帧。

5. 链接在一起，#framesz < = 512，#outsz = 0

    ```asm
        stp    r29, lr, [sp, -#framesz]!    // pre-indexed, save <r29,lr>
        mov    r29,sp                       // r29 points to bottom of stack
        stp    r19,r20,[sp, #framesz -32]   // save INT pair
        stp    d8,d9,[sp, #framesz -16]     // save FP pair
    ```

   与上述 #1 prolog 相比，优点是，所有寄存器保存的说明都准备就绪可以只有一个堆栈分配指令后立即执行。 因此，防止指令级并行性的 sp 上是没有反相关性。

6. 链接在一起，帧大小 > 512 （可选的功能而无需分配）

    ```asm
        stp    r29, lr, [sp, -80]!          // pre-indexed, save <r29,lr>
        stp    r19,r20,[sp,16]              // save in INT regs
        stp    r21,r22,[sp,32]              // ...
        stp    d8,d9,[sp,48]                // save in FP regs
        stp    d10,d11,[sp,64]
        mov    r29,sp                       // r29 points to top of local area
        sub    sp,#framesz-80               // allocate the remaining local area
    ```

   出于优化目的，r29 可以放在本地区域为"reg 对"和前/后-indexed 偏移量寻址模式提供更好的覆盖范围中的任意位置。 帧指针下方的局部变量可以访问基于 sp。

7. 链接在一起，帧大小 > 4 K，带或不带 alloca()，

    ```asm
        stp    r29, lr, [sp, -80]!          // pre-indexed, save <r29,lr>
        stp    r19,r20,[sp,16]              // save in INT regs
        stp    r21,r22,[sp,32]              // ...
        stp    d8,d9,[sp,48]                // save in FP regs
        stp    d10,d11,[sp,64]
        mov    r29,sp                       // r29 points to top of local area
        mov    r8, #framesz/16
        bl     chkstk
        sub    sp, r8*16                    // allocate remaining frame
                                            // end of prolog
        ...
        sp = alloca                         // more alloca() in body
        ...
                                            // beginning of epilog
        mov    sp,r29                       // sp points to top of local area
        ldp    d10,d11, [sp,64],
        ...
        ldp    r29, lr, [sp], -80           // post-indexed, reload <r29,lr>
    ```

## <a name="arm64-exception-handling-information"></a>ARM64 异常处理信息

### <a name="pdata-records"></a>.pdata 记录

.Pdata 记录是固定长度项描述 PE 二进制文件中每个堆栈操作的函数的有序的数组。 请仔细注意短语"堆栈操作": leaf 函数不需要任何本地存储并不需要保存/还原非易失寄存器不需要.pdata 记录;这些应显式省略以节省空间。 从这些函数之一的展开只是可以获得 LR 以向上移动到调用方的寄信人地址。

每个.pdata 记录的 ARM64 是 8 个字节的长度。 在第一个单词后, 跟与第二个函数的 32 位 RVA 启动的每个记录位置的一般格式包含指向长度可变的.xdata 块或已打包的字描述规范函数展开序列。

![.pdata 记录布局](../build/media/arm64-exception-handling-pdata-record.png ".pdata 记录布局")

字段是按如下所示：

- **函数启动 RVA**是函数开始的 32 位 RVA。

- **标志**是指示如何解释第二个.pdata 字的剩余 30 位的 2 位字段。 如果**标志**为 0，则剩余的位将形成**异常信息 RVA** (与低两位隐式 0)。 如果**标志**为非零，则剩余的位将形成**打包展开数据**结构。

- **异常信息 RVA**是存储在.xdata 部分中的长度可变的异常信息结构的地址。 此数据必须是对齐的 4 字节。

- **打包展开数据**是采用规范格式的函数从展开所需的操作的概括的说明。 在这种情况下，不需要任何 .xdata 记录。

### <a name="xdata-records"></a>.xdata 记录

当已打包的展开格式不足以描述函数的展开时，必须创建长度可变的 .xdata 记录。 该记录的地址存储在 .pdata 记录的第二个字中。 .Xdata 的格式是已打包的长度可变的组词语：

![.xdata 记录布局](../build/media/arm64-exception-handling-xdata-record.png ".xdata 记录布局")

此数据被分为四个部分：

1. 1 或 2 个字标头描述结构的总体大小并提供密钥函数数据。 第二个字中才显示如果这两个**Epilog 计数**并**代码字**字段设置为 0。 这些是标头中的位域：

   a. **函数长度**是一个 18 位字段，指示以字节为单位，除以 4 函数的总长度。 如果函数是大于 1 百万，然后必须使用多个 pdata 和 xdata 记录来描述该函数。 请参阅[大型函数](#large-functions)部分，了解更多详细信息。

   b. **Vers**是描述剩余 xdata 的版本 2 位字段。 撰写本文时，定义仅版本 0，并因此不允许的 1-3 的值。

   c. **X**是 1 位字段，该值指示是否存在 (1) 或不存在 (0) 的异常数据。

   d. **E**是一个 1 位字段指示的信息描述单个 epilog 打包到标头 (1) 上，而不是需要其他作用域的词更高版本 (0)。

   e. **Epilog 计数**是具有两种含义，具体取决于状态 5 位字段**E**位：

      1. 如果**E**设置为 0： 它指定在第 2 节中所述异常范围总数的计数。 如果超过 31 个范围存在于在函数中，则**代码字**字段必须设置为 0，以指示需要一个扩展字。

      2. 如果**E**设置为 1，则此字段指定的描述和仅 epilog 的第一个展开代码索引。

   f. **代码字**是指定的 32 位字包含第 4 节中的展开代码的所有所需数目的 5 位字段。 如果需要多个 31 词 （即，超过 124 展开代码字节），则此字段必须设置为 0，以指示需要一个扩展字。

   g. **扩展 Epilog 计数**并**扩展代码字**分别为 16 位和 8 位字段、，提供更多空间来编码极大量的 epilog 或极大量的展开代码字。 包含这些字段的扩展字中才显示如果这两个**Epilog 计数**并**代码字**第一个标头字中的字段设置为 0。

2. 异常数据之后, 如果**Epilog 计数**不为零，则是一系列有关 epilog 作用域的信息打包一个字，并存储起始偏移量递增的顺序。 每个作用域包含以下位：

   a. **Epilog 开始偏移量**是一个 18 位字段，描述以字节为单位，除以 4，相对于函数的开始 epilog 的偏移量

   b. **Res**是为将来扩展保留一个 4 位字段。 其值必须为 0。

   c. **Epilog 开始的索引**为 10 位 (比 2 更多的比特**扩展代码字**) 字段，指示第一个的字节索引展开描述此 epilog 代码。

3. Epilog 作用域的列表是包含展开代码的字节数组后，在后面的部分中的详细信息中所述。 在最接近的全字边界的末尾处填充此数组。 按 Little-Endian 的顺序存储字节，以便可以直接在 Little-Endian 模式下提取它们。

4. 最后，在展开代码字节后 (如果**X**标头中的位已设置为 1) 出现的异常处理程序信息。 这包含单个**异常处理程序 RVA**提供地址的异常处理程序本身，后面紧跟将长度可变数量的异常处理程序所需的数据。

上述.xdata 记录的设计，这样就可以提取前 8 个字节，并从该计算记录 （减去之后的可变的异常数据的长度） 的完整大小。 下面的代码段计算该记录大小：

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

应注意的是，尽管 prolog 和 epilog 每个具有其自己展开代码的索引，但它们之间共享表并且它完全有可能 （并不完全罕见），它们都可以共享相同的代码 （请参阅下面附录 A 中的示例 2）。 编译器编写器应优化这种情况下，特别是因为可以指定的最大索引为 255，从而限制为特定函数的展开代码的总数。

### <a name="unwind-codes"></a>展开代码

展开代码数组是介绍如何撤消序言中，操作需要撤消的顺序的效果的序列的池。 展开代码可以看作微型指令集，编码为字节的字符串。 执行完成后，调用函数的返回地址在 lr 寄存器中，并在调用该函数时所有非易失寄存器将还原为其值。

如果确保异常仅出现在函数主体 （和永远不会与 prolog 或任何 epilog），单个序列有必要。 但是，Windows 展开模式需要，我们必须能够从部分执行的 prolog 或 epilog 中展开。 为了适应此要求，展开代码已仔细设计，以便它们明确将 1 对 1 映射到在 prolog 和 epilog 中每个相关操作码。 这具有几方面的含义：

1. 通过计算展开代码的次数，就可以计算的 prolog 和 epilog 的长度。

2. 通过计算过去的 epilog 范围的开始指令的次数，则可以跳过同等数量的展开代码并执行用于完成部分执行的序列的其余部分展开 epilog 正在执行。

3. 方法是计算序言末尾之前对指令数，则可以跳过同等数量的展开代码并执行撤消只是那些部分的序言中的已完成执行的序列的其余部分。

展开代码是根据下表进行编码。 所有展开代码是一个单/双字节，只分配一个巨大的堆栈。 完全有 21 展开代码。 每个展开代码映射一个指令在 prolog/epilog 中以便为展开的部分执行的 prolog 和 epilog。

展开代码|Bits 和解释
|-|-|
`alloc_s`|000xxxxx： 分配小型堆栈大小 < 512 (2 ^5 * 16)。
`save_r19r20_x`|    001zzzzz： 保存\<r19，r20 > 对在 [sp #Z * 8] ！，预索引偏移量 > =-248
`save_fplr`|        01zzzzzz： 保存\<r29，lr > 对在 [sp + #Z * 8]，偏移量 < = 504。
`save_fplr_x`|        10zzzzzz： 保存\<r29，lr > 对在 [sp-（#Z + 1） * 8] ！，预索引偏移量 > =-512
`alloc_m`|        11000xxx\|xxxxxxxx： 分配大堆栈大小 < 16k (2 ^11 * 16)。
`save_regp`|        110010xx\|xxzzzzzz： 保存 r(19+#X) 对在 [sp + #Z * 8]，偏移量 < = 504
`save_regp_x`|        110011xx\|xxzzzzzz： 保存对 r(19+#X) 在 [sp-（#Z + 1） * 8] ！，预索引偏移量 > =-512
`save_reg`|        110100xx\|xxzzzzzz： 保存 reg r(19+#X) 在 [sp + #Z * 8]，偏移量 < = 504
`save_reg_x`|        1101010 x\|xxxzzzzz： 保存 reg r(19+#X) 在 [sp-（#Z + 1） * 8] ！，预索引偏移量 > =-256
`save_lrpair`|         1101011 x\|xxzzzzzz： 保存对\<r19 + 2 *#X，lr > 在 [sp + #Z*8]，偏移量 < = 504
`save_fregp`|        1101100 x\|xxzzzzzz： 保存对 d(8+#X) 在 [sp + #Z * 8]，偏移量 < = 504
`save_fregp_x`|        1101101 x\|xxzzzzzz： 在保存对 d(8+#X) [sp-（#Z + 1） * 8] ！，预索引偏移量 > =-512
`save_freg`|        1101110 x\|xxzzzzzz： 保存 reg d(8+#X) 在 [sp + #Z * 8]，偏移量 < = 504
`save_freg_x`|        11011110\|xxxzzzzz： 保存 reg d(8+#X) 在 [sp-（#Z + 1） * 8] ！，预索引偏移量 > =-256
`alloc_l`|         11100000\|xxxxxxxx\|xxxxxxxx\|xxxxxxxx： 分配大堆栈大小 < 256 M (2 ^24 * 16)
`set_fp`|        11100001： 设置 r29： 与： mov r29 sp
`add_fp`|        11100010\|xxxxxxxx： 设置 r29 与： 添加 r29、 sp、 #x * 8
`nop`|            11100011： 不展开操作是必需的。
`end`|            11100100： 展开代码的末尾。 表示已在 epilog 中。
`end_c`|        11100101： 当前链接作用域中的展开代码的末尾。
`save_next`|        11100110： 保存下一个非易失性 Int 或 FP 注册对。
`arithmetic(add)`|    11100111\| 000zxxxx： 将 cookie reg(z) 添加到 lr (0 = x28，1 = sp); 添加 lr，lr，reg(z)
`arithmetic(sub)`|    11100111\| 001zxxxx: sub cookie reg(z) lr 从 (0 = x28，1 = sp); 子 lr，lr，reg(z)
`arithmetic(eor)`|    11100111\| 010zxxxx： 使用 cookie reg(z) eor lr (0 = x28，1 = sp); eor lr，lr，reg(z)
`arithmetic(rol)`|    11100111\| 0110xxxx： 使用 cookie reg (x28) lr 的模拟的 rol; xip0 = neg x28; ror lr，xip0
`arithmetic(ror)`|    11100111\| 100zxxxx： 使用 cookie reg(z) ror lr (0 = x28，1 = sp); ror lr，lr，reg(z)
||            11100111: xxxz---:-保留
||              11101xxx： 对于自定义堆栈情况下才会生成 asm 例程的保留
||              11101001: MSFT_OP_TRAP_FRAME 的自定义堆栈
||              11101010: MSFT_OP_MACHINE_FRAME 的自定义堆栈
||              11101011: MSFT_OP_CONTEXT 的自定义堆栈
||              1111xxxx： 保留

在具有涵盖多个字节的大值的说明，第一次存储最高有效位。 上面的展开代码经过专门设计，以便通过只需查找代码的第一个字节，就可以知道以字节为单位的展开代码的总大小。 考虑到每个展开代码完全映射到在 prolog/epilog 中的指令，来计算的大小 prolog 或 epilog 中，需要完成的是引导从序列的开始到结束时，使用查找表或类似的设备来确定多长时间 cor响应操作码。

请注意在 prolog 中不允许后索引偏移量寻址。 所有的偏移量的范围 (#Z) 匹配除 STP/STR 寻址的编码`save_r19r20_x`在哪些 248 就足够了所有的存储区域 （10 Int 寄存器 + 8 FP 寄存器 + 8 输入的寄存器）。

`save_next` 必须遵循的 Int 保存或 FP 易失性注册对： `save_regp`， `save_regp_x`， `save_fregp`， `save_fregp_x`， `save_r19r20_x`，或另一个`save_next`。 它将在下一个 16 字节段的下一步注册对保存在"长大"顺序。 `save-next` 以下`save_next`，表示最后一个 Int 寄存器对指的是第一个 FP 寄存器对。

由于的常规大小返回，并跳转指令相同，因此没有必要的分隔`end`展开尾调用方案的代码。

`end_c` 旨在处理非连续函数片段出于优化目的。 一个`end_c`它指示在当前作用域中的展开代码的结尾必须后跟另一系列的展开代码已结束，但实际`end`。 展开代码之间`end_c`和`end`表示在父区域 ("影子"prolog) 中的序言操作。  更多详细信息和示例所述下面一节。

### <a name="packed-unwind-data"></a>打包展开数据

函数的规范格式如下所述的 prolog 和 epilog 按照打包展开数据可以使用，完全无需.xdata 记录，并显著降低了成本提供展开数据。 规范的 prolog 和 epilog 旨在满足简单函数的不需要异常处理程序，然后按照标准顺序执行其设置和清除操作的常见要求。

具有已打包的.pdata 记录的格式展开数据如下所示：

![.pdata 记录的已打包展开数据](../build/media/arm64-exception-handling-packed-unwind-data.png ".pdata 记录的已打包展开数据")

字段是按如下所示：

- **函数启动 RVA**是函数开始的 32 位 RVA。
- **标志**是一个 2 位字段，上文所述，使用以下含义：
  - 00 = 已打包展开数据未使用;剩余的位指向.xdata 记录如下
  - 01 = 已打包展开数据使用如下所述使用单一的 prolog 和 epilog 开头和末尾作用域
  - 10 = 已打包展开数据使用如下所述的代码而无需任何 prolog 和 epilog;这是可用于描述分隔的函数段。
  - 11 = 保留;
- **函数长度**是一个 11 位字段，提供以字节为单位，除以 4 的整个函数的长度。 如果该函数值大于 8k，必须改为使用完整的.xdata 记录。
- **帧大小**是一个 9 位域，指示堆栈为 16 除此函数分配的字节数。 大于 (8k-16) 字节的堆栈分配的函数必须使用完整的.xdata 记录。 这包括本地变量的区域，传出参数区域、 被调用方保存 Int 和 FP 区域和家庭参数区域，但不包括动态分配区域。
- **CR**是一个 2 位标志，指示函数是否包括额外的指令，若要设置帧链和返回链接：
  - 00 = 非链接的函数\<r29，lr > 对未保存在堆栈中。
  - 01 = 非链接的函数\<lr > 保存在堆栈中
  - 10 = 保留;
  - 11 = 链接的函数 prolog/epilog 中使用的存储/加载对指令\<r29，lr >
- **H**是一个 1 位标志，指示函数是否寻址整数参数寄存器 (r0-r7) 将它们存储在该函数的开始。 (0 = 不承载寄存器，1 = 家庭寄存器)。
- **RegI**是 4 位字段，该值指示的非易失性 INT 寄存器 (r19 r28) 保存在规范的堆栈位置数。
- **RegF** ，该值指示的非易失性 FP 寄存器 (d8 d15) 保存在规范的堆栈位置数是 3 位域。 (0 = 没有 FP 寄存器保存，m > 0: m + 1 FP 寄存器保存)。 保存只有一个 FP 寄存器，打包展开的函数不能应用数据。

属于类别 1、 2 （不带传出参数区域）、 3 和 4 上面部分中的规范 prolog 可以由已打包的展开格式表示。  Epilog 规范函数按照非常类似的形式，除非**H**不起作用，`set_fp`省略指令，和步骤，以及每个步骤中的说明的顺序反转在 epilog 中。 下表中详细介绍这些步骤为已打包的 xdata 的算法：

步骤 0： 执行每个区域的大小预先计算。

步骤 1： 保存 Int 被调用方保存的寄存器。

步骤 2： 此步骤是特定于类型 4 早期部分中。 lr 保存 Int 区域的末尾。

步骤 3： 保存 FP 被调用方保存的寄存器。

步骤 4： 将输入的参数保存在主参数区域。

步骤 5： 分配剩余堆栈，包括本地区域中， \<r29，lr > 对，并且传出参数区域。 5a 对应于规范类型 1。 图 5b 和 5 c 是规范类型 2。 5d 和 5e 针对这两个类型 3 且键入 4。

步骤 #|标志值|# of 说明|操作码|展开代码
-|-|-|-|-
0|||`#intsz = RegI * 8;`<br/>`if (CR==01) #intsz += 8; // lr`<br/>`#fpsz = RegF * 8;`<br/>`if(RegF) #fpsz += 8;`<br/>`#savsz=((#intsz+#fpsz+8*H)+0xf)&~0xf)`<br/>`#locsz = #famsz - #savsz`|
1|0 < **regI** < = 10|RegI / 2 + **RegI** %2|`stp r19,r20,[sp,#savsz]!`<br/>`stp r21,r22,[sp,16]`<br/>`...`|`save_regp_x`<br/>`save_regp`<br/>`...`
2|**CR**= = 01 *|1|`str lr,[sp, #intsz-8]`\*|`save_reg`
3|0 < **RegF** < = 7|(RegF + 1）/2 +<br/>(RegF + 1) %2）。|`stp d8,d9,[sp, #intsz]`\*\*<br/>`stp d10,d11,[sp, #intsz+16]`<br/>`...`<br/>`str d(8+RegF),[sp, #intsz+#fpsz-8]`|`save_fregp`<br/>`...`<br/>`save_freg`
4|**H** = = 1|4|`stp r0,r1,[sp, #intsz+#fpsz]`<br/>`stp r2,r3,[sp, #intsz+#fpsz+16]`<br/>`stp r4,r5,[sp, #intsz+#fpsz+32]`<br/>`stp r6,r7,[sp, #intsz+#fpsz+48]`|`nop`<br/>`nop`<br/>`nop`<br/>`nop`
5a|**CR** = = 11 & & #locsz<br/> < = 512|2|`stp r29,lr,[sp,-#locsz]!`<br/>`mov r29,sp`\*\*\*|`save_fplr_x`<br/>`set_fp`
5b|**CR** = = 11 &AMP; &AMP;<br/>512 < #locsz < = 4088|3|`sub sp,sp, #locsz`<br/>`stp r29,lr,[sp,0]`<br/>`add r29, sp, 0`|`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5c|**CR** = = 11 & & #locsz > 4088|4|`sub sp,sp,4088`<br/>`sub sp,sp, (#locsz-4088)`<br/>`stp r29,lr,[sp,0]`<br/>`add r29, sp, 0`|`alloc_m`<br/>`alloc_s`/`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5d|(**CR** = = 00 \| \| **CR**= = 01) &AMP; &AMP;<br/>#locsz < = 4088|1|`sub sp,sp, #locsz`|`alloc_s`/`alloc_m`
5e|(**CR** = = 00 \| \| **CR**= = 01) &AMP; &AMP;<br/>#locsz > 4088|2|`sub sp,sp,4088`<br/>`sub sp,sp, (#locsz-4088)`|`alloc_m`<br/>`alloc_s`/`alloc_m`

\*： 如果**CR** = = 01 和**RegI**数为奇数，步骤 2 和步骤 1 中的最后一个 save_rep 合并到一个 save_regp。

\*\* 如果**RegI** == **CR** = = 0，并且**RegF** ！ = 0，第一个 stp 浮点不前置。

\*\*\* 对应于没有指令`mov r29, sp`在 epilog 中存在。 如果函数需要从 r29 还原 sp，则我们不能使用打包展开数据。

### <a name="unwinding-partial-prologs-and-epilogs"></a>展开部分的 prolog 和 epilog

最常见的展开情况是函数的一个或多个调用，远离序言和所有 epilog 的正文中的发生位置。 在此情况下，展开非常简单： 展开器只是开始的索引 0 处开始并继续执行之前检测到结束操作码的指向展开数组中执行代码。

更难以正确展开在其中出现异常或中断执行 prolog 或 epilog 时的情况下它。 在这些情况下，仅部分构造的堆栈帧，和技巧就是确定完全什么做是为了正确地撤消它。

例如，采用此 prolog 和 epilog 序列：

```asm
0000:    stp    r29, lr, [sp, -256]!        // save_fplr_x  256 (pre-indexed store)
0004:    stp    d8,d9,[sp,224]              // save_fregp 0, 224
0008:    stp    r19,r20,[sp,240]            // save_regp 0, 240
000c:    mov    r29,sp                      // set_fp
         ...
0100:    mov    sp,r29                      // set_fp
0104:    ldp    r19,r20,[sp,240]            // save_regp 0, 240
0108:    ldp    d8,d9,[sp,224]              // save_fregp 0, 224
010c:    ldp    r29, lr, [sp, -256]!        // save_fplr_x  256 (post-indexed load)
0110:    ret     lr                         // end
```

每个操作码旁边是相应的展开代码描述此操作。 第一件事要注意是序言的展开代码的一系列是 epilog （不包括 epilog 最后一条指令） 的展开代码完全相同的镜像映像。 这是常见的情况，并为此展开的序言代码始终被认为与序言的执行顺序相反的顺序存储。

因此，对于 prolog 和 epilog，我们仍然面临着一组通用的展开代码：

`set_fp`, `save_regp 0,240`, `save_fregp,0,224`, `save_fplr_x_256`, `end`

与 epilog 案例 （更多简单直接原样按正常顺序），偏移量 0 开始 epilog （的起价为 0x100 函数中的偏移量） 中，我们可能希望执行完全展开的序列，正如尚未在任何清理。 如果我们发现自己在一条指令 （在 epilog 中的偏移量 2），我们可以成功通过跳过第一个展开代码进行展开。 通用化这种情况下，假设之间的操作码的 1 对 1 映射并展开代码，是否我们是从指令 n 在 epilog 中，我们应跳过第一个 n 个展开代码并开始执行从此处，我们可以状态。

事实证明，类似的逻辑适用于序言中，除非按相反的顺序。 如果我们是从偏移量为 0 在序言中，我们想要执行执行任何操作。 如果我们展开从偏移量为 2，这是一条指令中，然后我们想要开始执行展开序列一个展开代码从结束 （请记住，代码将按相反的顺序存储）。 和此处过我们可以通用化，如果我们在序言中的指令 n 从展开的我们应该开始从代码的列表的末尾执行 n 个展开代码。

现在，它并不总是完全匹配的 prolog 和 epilog 代码的情况。 出于此原因，可能需要展开数组以包含几个代码序列。 若要确定从何处开始处理代码的偏移量，请使用以下逻辑：

1. 如果从内部展开的函数的正文只需开始执行展开代码位于索引 0 处，并继续，直到达到"结束"操作码。

2. 如果从展开在 epilog 中，使用与作为起始点的 epilog 范围提供的特定于 epilog 的起始索引。 计算 PC 相关的字节数是从 epilog 开头。 然后向前移动向前跳过展开代码，直到所有已执行的指令都考虑在内的展开代码。 然后，执行在该点开始。

3. 如果从展开序言中，使用索引 0 作为起点。 然后计算 PC 相关的字节数是从序言结束和计算的序列中的 prolog 代码的长度。 然后向前移动向前跳过展开代码，直到所有尚未执行的指令都考虑在内的展开代码。 然后，执行在该点开始。

因此这些规则的序言的展开代码必须始终为数组中的第一个，也要用于常规用例的主体内部展开从展开的代码。 立即后应遵循任何特定于的 epilog 代码序列。

### <a name="function-fragments"></a>函数片段

对于代码优化目的和其他原因，它可能更可取的方法将函数拆分为单独的片段 （也称为区域）。 完成此操作后，每个生成的函数片段都需要其自己单独的.pdata （和可能是.xdata） 记录。

具有其自己的 prolog 的分隔辅助片段，应未进行堆栈调整在其 prolog 中完成。 所有堆栈空间所需的辅助副本必须由其父区域 （或称为的主机区域） 预分配的区域。 这会使堆栈指针操作严格函数的原始序言中。

函数片段的一个典型情况是"代码分离"，使用该编译器可能会移出其主机函数代码的区域。 有三种可以通过单独的代码产生的异常情况。

#### <a name="example"></a>示例:

- (区域 1： 开始)

    ```asm
        stp     r29, lr, [sp, -256]!    // save_fplr_x  256 (pre-indexed store)
        stp     r19,r20,[sp,240]        // save_regp 0, 240
        mov     r29,sp                  // set_fp
        ...
    ```

- (区域 1： 结束)
- (区域 3： 开始)

    ```asm
        ...
    ```

- (区域 3： 结束)
- (区域 2： 开始)

    ```asm
    ...
        mov     sp,r29                  // set_fp
        ldp     r19,r20,[sp,240]        // save_regp 0, 240
        ldp     r29, lr, [sp, -256]!    // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- (区域 2： 结束)

1. 仅 Prolog (区域 1： 所有 epilog 都位于单独的区域):

   仅在 prolog 需要进行描述。 这不能通过精简的.pdata 格式表示。 在完整的.xdata 情况下，这可以表示的 Epilog 计数设置 = 0。 请参阅上面的示例中的区域 1。

   展开代码： `set_fp`， `save_regp 0,240`， `save_fplr_x_256`， `end`。

2. 仅 Epilog (区域 2: prolog 位于主机区域)

   假定，跳转到此区域的时间控制，通过所有 prolog 代码已都执行。 部分展开可能发生在 epilog 中相同的方式与普通函数一样。 不能通过精简的.pdata 表示此类型的区域。 在完整的 xdata 记录中，它可以用进行编码"影子"序言中，通过括起来`end_c`和`end`展开代码对。  前导`end_c`指示序言的大小为零。 Epilog 的起始索引的单个 epilog 点`set_fp`。

   展开代码区域 2: `end_c`， `set_fp`， `save_regp 0,240`， `save_fplr_x_256`， `end`。

3. 没有 prolog 或 epilog (区域 3: prolog 和 epilog 所有是其他片段中):

   可以通过设置标志应用精简的.pdata 格式 = 10。 使用完整的.xdata 记录，Epilog 计数 = 1。 展开代码是相同的区域 2 更高版本，但 Epilog 开始索引还指向`end_c`。 在此区域的代码中，部分展开将永远不会发生。

另一个更复杂的用例的函数片段是"收缩换行"，使用该编译器可以选择延迟保存直到外部函数入口 prolog 某些被调用方保存的寄存器。

- (区域 1： 开始)

    ```asm
        stp     r29, lr, [sp, -256]!    // save_fplr_x  256 (pre-indexed store)
        stp     r19,r20,[sp,240]        // save_regp 0, 240
        mov     r29,sp                  // set_fp
        ...
    ```

- (区域 2： 开始)

    ```asm
        stp     r21,r22,[sp,224]        // save_regp 2, 224
        ...
        ldp     r21,r22,[sp,224]        // save_regp 2, 224
    ```

- (区域 2： 结束)

    ```asm
        ...
        mov     sp,r29                  // set_fp
        ldp     r19,r20,[sp,240]        // save_regp 0, 240
        ldp     r29, lr, [sp, -256]!    // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- (区域 1： 结束)

在区域 1 的序言中，堆栈空间是预先分配。 请注意该区域 2 将具有相同的展开代码甚至不移出其主机功能。

区域 1: `set_fp`， `save_regp 0,240`， `save_fplr_x_256`， `end` Epilog 开始的索引指向`set_fp`像往常一样。

区域 2: `save_regp 2, 224`， `end_c`， `set_fp`， `save_regp 0,240`， `save_fplr_x_256`， `end`。 Epilog 启动索引点首先展开代码`save_regp 2, 224`。

### <a name="large-functions"></a>较大的函数

可以利用片段来描述大小超过.xdata 标头中位字段为 1 百万的限制的函数。 若要描述此类非常大的函数，它只需要拆分为若干段小于 1 百万。 应调整每个片段，以便它不会不拆分为多个部分的 epilog。

仅在函数的第一个片段包含序言;所有其他片段都被标记为没有序言。 具体取决于 epilog 存在数量，每个片段可能包含零个或多个 epilog。 请记住，片段中的每个 epilog 作用域指定相对于开始的片段，而非该函数的开始的起始偏移量。

如果片段没有序言和没有结语，它仍需要其自己的.pdata （和可能是.xdata） 记录，以描述如何从展开的函数体中。

## <a name="examples"></a>示例

### <a name="example-1-frame-chained-compact-form"></a>示例 1： 链接框架，compact 的窗体

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

### <a name="example-2-frame-chained-full-form-with-mirror-prolog--epilog"></a>示例 2： 帧的链接后，完整格式使用镜像 Prolog 和 Epilog

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

请注意，EpilogStart 索引 [0] 指向相同的序言展开代码序列。

### <a name="example-3-variadic-unchained-function"></a>示例 3： 非链接可变参数函数

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

注意： EpilogStart 索引 [4] 指向序言展开代码 （部分重用展开数组） 的中间。

## <a name="see-also"></a>请参阅

[ARM64 ABI 约定概述](arm64-windows-abi-conventions.md)  
[ARM 异常处理](../build/arm-exception-handling.md)  
