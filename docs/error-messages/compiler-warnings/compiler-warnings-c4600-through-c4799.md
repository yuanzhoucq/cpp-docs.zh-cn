---
title: "编译器警告 C4600 到 C4799 |Microsoft 文档"
ms.date: 11/17/2017
ms.technology: cpp-tools
ms.topic: error-reference
f1_keywords:
- C4602
- C4603
- C4609
- C4612
- C4613
- C4620
- C4622
- C4629
- C4631
- C4634
- C4635
- C4636
- C4637
- C4638
- C4645
- C4646
- C4655
- C4657
- C4658
- C4662
- C4670
- C4671
- C4672
- C4674
- C4676
- C4678
- C4681
- C4682
- C4685
- C4688
- C4689
- C4690
- C4693
- C4694
- C4695
- C4696
- C4718
- C4719
- C4720
- C4721
- C4722
- C4724
- C4725
- C4728
- C4729
- C4732
- C4739
- C4750
- C4751
- C4752
- C4754
- C4755
- C4757
- C4764
- C4767
- C4770
- C4792
- C4794
dev_langs: C++
ms.assetid: 22bd4392-f3be-445c-9f23-6126aebac901
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f5d7121e01b651e87630fe18bec21e3d999ed0e7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warnings-c4600-through-c4799"></a>编译器警告 C4600 到 C4799

本部分中的文档的文章说明由编译器生成警告消息的一个子集。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>警告消息

|警告|消息|
|-------------|-------------|
|[编译器警告（等级 1）C4600](../../error-messages/compiler-warnings/compiler-warning-level-1-c4600.md)|#pragma macro name： 应为有效的非空字符串|
|编译器警告 （等级 1） C4602|#pragma pop_macro: macro name 此标识符没有以前 #pragma push_macro|
|编译器警告 （等级 1） C4603|*标识符*： 未定义宏或在预编译标头使用后定义发生改变|
|编译器警告 （等级 1） C4604|*类型*： 在本机和托管的边界之间按值传递自变量需要有效的复制构造函数。 否则，运行时行为是不确定|
|编译器警告 （等级 1） C4605|/D*宏*当前的命令行上指定但未指定时生成预编译标头|
|[编译器警告（等级 1）C4606](../../error-messages/compiler-warnings/compiler-warning-level-1-c4606.md)|#pragma 警告: 警告编号忽略;代码分析警告不与警告级别相关联|
|[编译器警告（等级 3）C4608](../../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)|“union_member”已被初始值设定项列表中的另一个联合成员“union_member”初始化|
|编译器警告 （等级 3，错误） C4609|*type1*派生自默认接口*接口*类型上*type2*。 使用适用于不同的默认界面*type1*，或中断的基/派生关系。|
|[编译器警告（等级 4）C4610](../../error-messages/compiler-warnings/compiler-warning-level-4-c4610.md)|对象 class 不能实例化-用户定义的所需的构造函数|
|[编译器警告（等级 4）C4611](../../error-messages/compiler-warnings/compiler-warning-level-4-c4611.md)|function 和 c + + 对象析构之间的交互是不可移植|
|编译器警告 （等级 1） C4612|包含文件名中有错误|
|编译器警告 （等级 1） C4613|*符号*： 无法更改段的类|
|[编译器警告（等级 1）C4615](../../error-messages/compiler-warnings/compiler-warning-level-1-c4615.md)|#pragma 警告： 未知的用户警告类型|
|[编译器警告（等级 1）C4616](../../error-messages/compiler-warnings/compiler-warning-level-1-c4616.md)|#pragma 警告： 警告编号 number 不是有效的编译器警告|
|[编译器警告（等级 1）C4618](../../error-messages/compiler-warnings/compiler-warning-level-1-c4618.md)|杂注参数包含一个空字符串;忽略杂注|
|[编译器警告（等级 3）C4619](../../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md)|#pragma warning: 无警告编号“number”|
|编译器警告 （等级 1） C4620|未找到类型“type”的“运算符 ++”后缀形式，请使用前缀形式|
|[编译器警告（等级 1）C4621](../../error-messages/compiler-warnings/compiler-warning-level-1-c4621.md)|operator-找到类型 type，以使用前缀形式中没有任何后缀窗体|
|编译器警告 （等级 3） C4622|覆盖创建对象文件中的预编译头期间生成调试信息: file|
|[编译器警告（等级 4）C4623](../../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md)|derived class： 默认构造函数隐式定义为已删除，因为基类默认构造函数不可访问或已删除|
|[编译器警告（等级 1）C4624](../../error-messages/compiler-warnings/compiler-warning-level-1-c4624.md)|derived class： 析构函数隐式定义为已删除，因为基类析构函数不可访问或已删除|
|[编译器警告（等级 4）C4625](../../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md)|derived class： 复制构造函数隐式定义为已删除，因为基类复制构造函数不可访问或已删除|
|[编译器警告（等级 4）C4626](../../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md)|derived class： 赋值运算符已隐式定义为删除，因为基类赋值运算符是不可访问或已删除|
|[编译器警告（等级 1）C4627](../../error-messages/compiler-warnings/compiler-warning-level-1-c4627.md)|\<标识符 >： 在查找预编译标头使用时跳过|
|[编译器警告（等级 1）C4628](../../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md)|-Ze 不支持二合字母。 字符序列 digraph 未解释为 %s 的替换标记|
|编译器警告 （等级 4） C4629|使用了有向图，字符序列“digraph”解释为标记“char”（如果这不是你想要的，请在这两个字符之间插入一个空格）|
|[编译器警告（等级 1）C4630](../../error-messages/compiler-warnings/compiler-warning-level-1-c4630.md)|symbol: 外部存储类说明符在成员定义上非法|
|编译器警告 （等级 2） C4631|MSXML 或 XPath 不可用，将不会处理 XML 文档注释。 原因|
|[编译器警告（等级 1）C4632](../../error-messages/compiler-warnings/compiler-warning-level-1-c4632.md)|XML 文档注释： 文件的路径-访问被拒绝： 原因|
|[编译器警告（等级 3）C4633](../../error-messages/compiler-warnings/compiler-warning-level-3-c4633.md)|XML 文档注释目标： 错误： 原因|
|编译器警告 （等级 4） C4634|XML 文档注释目标： 不能应用： 原因|
|编译器警告 （等级 3） C4635|XML 文档注释目标: XML 格式不正确: 原因|
|编译器警告 （等级 3） C4636|用于构造的 XML 文档注释： 标记需要非空 attribute 特性。|
|编译器警告 （等级 3 和等级 4） C4637|XML 文档注释目标：\<包括 > 丢弃的标记。 原因|
|编译器警告 （等级 3） C4638|XML 文档注释目标： 引用未知符号 symbol。|
|[编译器警告（等级 4）C4639](../../error-messages/compiler-warnings/compiler-warning-level-4-c4639.md)|MSXML 错误，将不会处理注释的 XML 文档。 原因|
|[编译器警告（等级 3）C4640](../../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md)|“instance”: 本地静态对象的结构是非线程安全的|
|[编译器警告（等级 3）C4641](../../error-messages/compiler-warnings/compiler-warning-level-3-c4641.md)|XML 文档注释中有明确的交叉引用：|
|编译器警告 （等级 3） C4645|用 __declspec(noreturn) 声明的函数有返回语句|
|编译器警告 （等级 3） C4646|用 __declspec(noreturn) 声明的函数有非 void 返回类型|
|编译器警告 （等级 3） C4647|行为更改： __is_pod (*类型*) 在以前版本中具有不同的值|
|编译器警告 （等级 3） C4648|忽略标准属性 carries_dependency|
|编译器警告 （等级 3） C4649|在此上下文中，则忽略属性|
|[编译器警告（等级 1）C4650](../../error-messages/compiler-warnings/compiler-warning-level-1-c4650.md)|不在预编译标头; 调试信息将可仅全局符号从标头|
|[编译器警告（等级 1）C4651](../../error-messages/compiler-warnings/compiler-warning-level-1-c4651.md)|指定有关预编译标头而不是当前的编译的定义|
|[编译器警告（等级 1）C4652](../../error-messages/compiler-warnings/compiler-warning-level-1-c4652.md)|编译器选项 option 与预编译标头; 不一致当前的命令行选项将重写预编译标头中定义|
|[编译器警告（等级 2）C4653](../../error-messages/compiler-warnings/compiler-warning-level-2-c4653.md)|编译器选项 option 与预编译标头; 不一致忽略当前命令行选项|
|编译器警告 （等级 4） C4654|前后放置的代码包含预编译标头的行将被忽略。 将代码添加到预编译标头。|
|编译器警告 （等级 1） C4655|symbol： 变量类型是新以来的最新版本，或在其他地方以不同方式定义|
|[编译器警告（等级 1）C4656](../../error-messages/compiler-warnings/compiler-warning-level-1-c4656.md)|symbol： 数据类型是新或自从最新版本，或在其他地方以不同方式定义|
|编译器警告 （等级 1） C4657|表达式涉及以来的最新生成新的数据类型|
|编译器警告 （等级 1） C4658|function： 函数原型是最新版本，因为新的或在其他地方以不同的方式声明|
|[编译器警告（等级 1）C4659](../../error-messages/compiler-warnings/compiler-warning-level-1-c4659.md)|#pragma 杂注： 使用保留的段领域具有未定义的行为，请使用 #pragma 注释 （链接器，...）|
|[编译器警告（等级 1）C4661](../../error-messages/compiler-warnings/compiler-warning-level-1-c4661.md)|identifier： 提供显式模板实例化请求没有适当的定义|
|编译器警告 （等级 1） C4662|显式实例化；模板类“identifier1”无用于专用化“identifier2”的定义|
|[编译器警告（等级 1）C4667](../../error-messages/compiler-warnings/compiler-warning-level-1-c4667.md)|function： 没有匹配的函数模板定义强制实例化|
|[编译器警告（等级 4）C4668](../../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md)|symbol 未定义为预处理器宏，用"0"替换为指令|
|[编译器警告（等级 1）C4669](../../error-messages/compiler-warnings/compiler-warning-level-1-c4669.md)|cast： 不安全的转换: class 是一个托管的类型的对象|
|编译器警告 （等级 4） C4670|identifier： 此基类不可访问|
|编译器警告 （等级 4） C4671|identifier： 复制构造函数不可访问|
|编译器警告 （等级 4） C4672|identifier1： 不明确。 首先被看作“identifier2”|
|[编译器警告（等级 4）C4673](../../error-messages/compiler-warnings/compiler-warning-level-4-c4673.md)|引发以下类型的 identifier 不会被视为在 catch 站点|
|编译器警告 （等级 1） C4674|“方法”应声明为“静态”，而且只能有一个参数|
|编译器警告 （等级 4） C4676|%s: 析构函数不可访问|
|[编译器警告（等级 1）C4677](../../error-messages/compiler-warnings/compiler-warning-level-1-c4677.md)|function： 非私有成员的签名包含程序集私有类型 private_type|
|编译器警告 （等级 1） C4678|基类“base_type”的可访问性比“derived_type”低|
|[编译器警告（等级 1）C4679](../../error-messages/compiler-warnings/compiler-warning-level-1-c4679.md)|member： 无法导入成员|
|[编译器警告（等级 4）C4680](../../error-messages/compiler-warnings/compiler-warning-level-4-c4680.md)|class： 组件类不指定的默认接口。|
|编译器警告 （等级 4） C4681|class： 组件类不指定是事件源的默认接口|
|编译器警告 （等级 4） C4682|parameter： 指定，默认为 [in] 未方向参数特性|
|[编译器警告（等级 1）C4683](../../error-messages/compiler-warnings/compiler-warning-level-1-c4683.md)|function： 事件源具有输出的参数;将多个事件处理程序挂钩时应格外小心|
|[编译器警告（等级 1）C4684](../../error-messages/compiler-warnings/compiler-warning-level-1-c4684.md)|attribute： 警告!! 属性可能会导致无效的代码生成： 谨慎使用|
|编译器警告 （等级 1） C4685|分析模板参数时需要“> >”，却找到了“>>”|
|[编译器警告（等级 3）C4686](../../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)|“user-defined type”: 行为可能有更改，UDT 中的更改返回调用约定|
|[编译器警告 （错误） C4687](../../error-messages/compiler-warnings/compiler-warning-c4687.md)|class： 密封的抽象类不能实现接口 interface|
|编译器警告 （等级 1） C4688|“constraint”：约束列表包含程序集私有类型“type”|
|编译器警告 （等级 1） C4689|%c： 不受支持的 #pragma detect_mismatch; 中的字符忽略 #pragma|
|编译器警告 （等级 4） C4690|[emitidl (pop)]: 详细栈比入|
|[编译器警告（等级 1）C4691](../../error-messages/compiler-warnings/compiler-warning-level-1-c4691.md)|type： 在未引用程序集 file，而是使用了当前翻译单元中定义的类型应引用的类型|
|[编译器警告（等级 1）C4692](../../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)|“function”: 非私有成员的签名包含程序集私有本机类型“native_type”|
|[编译器警告 （等级 1，错误） C4693](../../error-messages/compiler-warnings/compiler-warning-c4693.md)|class： 密封的抽象类不能具有任何实例成员实例 member|
|[编译器警告 （等级 1，错误） C4694](../../error-messages/compiler-warnings/compiler-warning-c4694.md)|class： 密封的抽象类不能有基类 base_class|
|编译器警告 （等级 1） C4695|#pragma execution_character_set: 字符集不是受支持的参数： 支持当前仅 utf-8|
|编译器警告 （等级 1） C4696|/ 超出范围; ZBvalue1 选项假设 'value2'|
|[编译器警告（等级 1 和等级 4）C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|未初始化的局部变量 name，然后使用|
|[编译器警告（等级 4）C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)|可能未初始化的本地变量 name，然后使用|
|[编译器警告（等级 4）C4702](../../error-messages/compiler-warnings/compiler-warning-level-4-c4702.md)|无法访问的代码|
|[编译器警告（等级 4）C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|可能未初始化的局部指针变量 %s 使用|
|[编译器警告（等级 4）C4706](../../error-messages/compiler-warnings/compiler-warning-level-4-c4706.md)|条件表达式中的分配|
|[编译器警告（等级 4）C4709](../../error-messages/compiler-warnings/compiler-warning-level-4-c4709.md)|数组索引表达式中的逗号运算符|
|[编译器警告（等级 4）C4710](../../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md)|“function”: 函数未内联|
|[编译器警告（等级 1）C4711](../../error-messages/compiler-warnings/compiler-warning-level-1-c4711.md)|函数 function，为自动内联展开选定|
|[编译器警告（等级 4）C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)|函数 function 标记为 __forceinline 不内联|
|[编译器警告（等级 1）C4715](../../error-messages/compiler-warnings/compiler-warning-level-1-c4715.md)|function： 并非所有控制路径都返回值|
|[编译器警告 （等级 1，错误） C4716](../../error-messages/compiler-warnings/compiler-warning-level-1-c4716.md)|function： 必须返回值|
|[编译器警告（等级 1）C4717](../../error-messages/compiler-warnings/compiler-warning-level-1-c4717.md)|function： 所有控制路径的递归，函数将导致运行时堆栈溢出|
|编译器警告 （等级 4） C4718|function call： 递归调用没有任何副作用，删除|
|编译器警告 （等级 1） C4719|指定 Qfast 时发现-使用 f 作为后缀，以指示单精度的双精度常量|
|编译器警告 （等级 2） C4720|内联汇编程序报告: message|
|编译器警告 （等级 1） C4721|function： 不可用作内部函数|
|编译器警告 （等级 1） C4722|function： 析构函数永远不会返回时，可能存在内存泄漏|
|[编译器警告（等级 3）C4723](../../error-messages/compiler-warnings/compiler-warning-level-3-c4723.md)|潜在的被 0 除|
|编译器警告 （等级 3） C4724|潜在的以 0 求模|
|编译器警告 （等级 3） C4725|在一些 Pentium 中，指令可能不准确|
|[编译器警告（等级 1）C4727](../../error-messages/compiler-warnings/compiler-warning-level-1-c4727.md)|相同的时间戳 obj_file_1 和 obj_file_2 中找到的名为 pch_file PCH。  使用第一个 PCH。|
|编译器警告 （等级 1） C4728|/ Yl 选项被忽略，因为所需 PCH 引用|
|编译器警告 （等级 4） C4729|根据警告，函数对于流图形太大|
|[编译器警告 (等级 1) C4730](../../error-messages/compiler-warnings/compiler-warning-level-1-c4730.md)编译器警告 （等级 1） C4730|main： 混合 _m64 和浮点表达式可能会导致代码不正确|
|[编译器警告（等级 1）C4731](../../error-messages/compiler-warnings/compiler-warning-level-1-c4731.md)|指针： 帧指针寄存器注册修改通过内联程序集代码|
|编译器警告 （等级 1） C4732|内部函数 %s 不支持在此体系结构|
|[编译器警告（等级 1）C4733](../../error-messages/compiler-warnings/compiler-warning-level-1-c4733.md)|内联 asm 将分配给"fs: 0": 未注册为安全的处理程序的处理程序|
|[编译器警告（等级 3）C4738](../../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md)|将 32 位浮点型结果存储在内存中，可能会降低性能|
|编译器警告 （等级 1） C4739|对变量“var”的引用超过了其存储空间|
|[编译器警告（等级 4）C4740](../../error-messages/compiler-warnings/compiler-warning-level-4-c4740.md)|流在代码或跳出内联 asm 代码会取消全局优化|
|[编译器警告（等级 1）C4742](../../error-messages/compiler-warnings/compiler-warning-level-1-c4742.md)|var 具有 file1 和 file2 中的不同对齐方式： 编号和编号|
|[编译器警告（等级 1）C4743](../../error-messages/compiler-warnings/compiler-warning-level-1-c4743.md)|type 具有 file1 和 file2 中的不同大小： 数量和字节数|
|[编译器警告（等级 1）C4744](../../error-messages/compiler-warnings/compiler-warning-level-1-c4744.md)|var 具有 file1 和 file2 中的不同类型: type1 和 type2|
|[编译器警告 C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)|可变访问*表达式*受到 /volatile:\<iso &#124; ms > 设置; 请考虑使用 __iso_volatile_load/store 内部函数|
|[编译器警告（等级 1）C4747](../../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)|调用托管入口点： 不会在有加载程序锁，包括 DLL 入口点和调用从 DLL 入口点达到运行托管的代码|
|编译器警告 （等级 4） C4749|有条件地支持： offsetof 应用于 non standard 布局类型*类型*|
|编译器警告 （等级 1） C4750|“identifier”：函数 with _alloca() 内嵌到循环中|
|编译器警告 （等级 4） C4751|/arch: avx 不适用于 intel （） 流式处理 SIMD 扩展中内联 ASM|
|编译器警告 （等级 4） C4752|找到 intel （） 高级矢量扩展;请考虑使用 /arch: avx|
|编译器警告 （等级 4） C4754|在 %s(%d) 的比较中的算术运算的转换规则意味着无法执行一个分支。 将 %s 转换为 %s （或 %d 字节的相似类型）。|
|编译器警告 C4755|在 %s(%d) 的比较中的算术运算的转换规则意味着无法执行一个分支中的内联函数。 将 %s 转换为 %s （或 %d 字节的相似类型）。|
|[编译器警告（等级 2）C4756](../../error-messages/compiler-warnings/compiler-warning-level-2-c4756.md)|常量的算术溢出|
|编译器警告 （等级 4） C4757|下标是较大的无符号的值，是否有意用负常量的？|
|编译器警告 （等级 4） C4764|可以不对齐大于 16 个字节的捕获对象|
|编译器警告 （等级 4） C4767|节名称 %s 的长度超过 8 个字符，以及将被链接器截断|
|编译器警告 （等级 3） C4768|则将忽略链接规范的前面的 __declspec 属性|
|编译器警告 C4770|部分验证枚举*名称*用作索引|
|编译器警告 C4771|必须使用简单的指针; 创建边界忽略 MPX 内部函数|
|[编译器警告 （等级 1，错误） C4772](../../error-messages/compiler-warnings/compiler-warning-level-1-c4772.md)|#import 从缺少的类型库; 引用了类型missing_type 用作占位符|
|编译器警告 （等级 4） C4774|*字符串*： 格式字符串中自变量应*数*不是字符串文本|
|编译器警告 （等级 3） C4775|在格式字符串中使用的非标准扩展*字符串*of function*函数*|
|编译器警告 （等级 1） C4776|%*字符*'函数的格式字符串中不允许*函数*|
|编译器警告 （等级 4） C4777|*函数*： 格式字符串*字符串*要求类型自变量*type1*，但可变参数自变量*数*具有类型*type2*|
|编译器警告 （等级 3） C4778|*函数*： 格式字符串未终止*字符串*|
|[编译器警告（等级 1）C4788](../../error-messages/compiler-warnings/compiler-warning-level-1-c4788.md)|identifier： 标识符被截断为 number 个字符|
|[编译器警告（等级 1）C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|缓冲区“identifier”(大小为 N 字节)将溢出；M 字节将在偏移 L 时开始写入|
|编译器警告 （等级 2） C4792|函数 %s 使用 sysimport 声明并从本机代码; 引用需要链接导入库|
|[编译器警告（等级 1 和 3）C4793](../../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)|function： 函数编译为本机： \n\t'reason|
|编译器警告 （等级 1） C4794|线程本地存储区变量 %s 从 %s 更改为 %s 的段|
|[编译器警告（等级 1）C4799](../../error-messages/compiler-warnings/compiler-warning-level-1-c4799.md)|函数 function 具有不 EMMS 指令|