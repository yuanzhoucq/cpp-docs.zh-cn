---
title: 编译器警告 C4600 - C4799
ms.date: 04/21/2019
f1_keywords:
- C4609
- C4658
- C4671
- C4676
- C4689
- C4695
- C4696
- C4719
- C4720
- C4721
- C4728"
- C4732
- C4751
- C4752
- C4755
- C4757
- C4767
- C4770
helpviewer_keywords:
- C4609
- C4658
- C4671
- C4676
- C4689
- C4695
- C4696
- C4719
- C4720
- C4721
- C4728"
- C4732
- C4751
- C4752
- C4755
- C4757
- C4767
- C4770
ms.assetid: 22bd4392-f3be-445c-9f23-6126aebac901
ms.openlocfilehash: 3df17b115797f4d68621854d072c41aca14a0fd8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62227026"
---
# <a name="compiler-warnings-c4600-through-c4799"></a>编译器警告 C4600 - C4799

在本部分文档中的文章说明了由编译器生成警告消息的一个子集。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>警告消息

|警告|消息|
|-------------|-------------|
|[编译器警告 （等级 1） C4600](../../error-messages/compiler-warnings/compiler-warning-level-1-c4600.md)|#pragma macro name： 应为有效的非空字符串|
|[编译器警告 （等级 1） C4602](compiler-warning-level-1-c4602.md)|#pragma pop_macro: macro name 前面没有 #pragma push_macro 此标识符|
|[编译器警告 （等级 1） C4603](compiler-warning-level-1-c4603.md)|'*标识符*： 未定义宏或在预编译的头使用后定义发生改变|
|编译器警告 （等级 1） C4604|'*类型*： 跨本机和托管边界按值传递参数要求有效的复制构造函数。 否则是不确定的运行时行为|
|编译器警告 （等级 1） C4605|/D*宏*当前的命令行上指定但未指定生成预编译标头时|
|[编译器警告 （等级 1） C4606](../../error-messages/compiler-warnings/compiler-warning-level-1-c4606.md)|#pragma 警告: 警告编号被忽略;代码分析警告与警告等级无关|
|[编译器警告 （等级 3） C4608](../../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)|“union_member”已被初始值设定项列表中的另一个联合成员“union_member”初始化|
|编译器警告 （等级 3，错误） C4609|'*type1*派生默认接口*界面*类型上*type2*。 使用适用于不同的默认界面 '*type1*，或中断基/派生关系。|
|[编译器警告 （等级 C4610](../../error-messages/compiler-warnings/compiler-warning-level-4-c4610.md)|对象 class 不能实例化-用户定义的所需的构造函数|
|[编译器警告 （等级 C4611](../../error-messages/compiler-warnings/compiler-warning-level-4-c4611.md)|function 之间的交互和C++对象析构是不可移植|
|[编译器警告 （等级 1） C4612](compiler-warning-level-1-c4612.md)|包含文件名中有错误|
|[编译器警告 （等级 1） C4613](compiler-warning-level-1-c4613.md)|'*符号*： 无法更改段的类|
|[编译器警告 （等级 1） C4615](../../error-messages/compiler-warnings/compiler-warning-level-1-c4615.md)|#pragma 警告： 未知的用户警告类型|
|[编译器警告 （等级 1） C4616](../../error-messages/compiler-warnings/compiler-warning-level-1-c4616.md)|#pragma 警告： 警告编号 number 不是有效的编译器警告|
|[编译器警告 （等级 1） C4618](../../error-messages/compiler-warnings/compiler-warning-level-1-c4618.md)|pragma 参数包括一个空字符串;忽略杂注|
|[编译器警告 （等级 3） C4619](../../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md)|#pragma warning: 无警告编号“number”|
|[编译器警告 （等级 1） C4620](compiler-warning-level-1-c4620.md)|未找到类型“type”的“运算符 ++”后缀形式，请使用前缀形式|
|[编译器警告 （等级 1） C4621](../../error-messages/compiler-warnings/compiler-warning-level-1-c4621.md)|任何后缀形式的 operator--找到类型 type，使用前缀形式|
|[编译器警告 （等级 3） C4622](compiler-warning-level-3-c4622.md)|覆盖创建对象文件中的预编译头期间生成调试信息: file|
|[编译器警告 （等级 C4623](../../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md)|derived class： 默认构造函数隐式定义为已删除，因为基类默认构造函数不可访问或已删除|
|[编译器警告 （等级 1） C4624](../../error-messages/compiler-warnings/compiler-warning-level-1-c4624.md)|derived class： 析构函数隐式定义为已删除，因为基类析构函数不可访问或已删除|
|[编译器警告 （等级 C4625](../../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md)|derived class： 复制构造函数隐式定义为已删除，因为基类复制构造函数不可访问或已删除|
|[编译器警告 （等级 C4626](../../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md)|derived class： 赋值运算符已隐式定义为已删除，因为基类赋值运算符不可访问或已删除|
|[编译器警告 （等级 1） C4627](../../error-messages/compiler-warnings/compiler-warning-level-1-c4627.md)|\<标识符 >： 在查找预编译标头使用时跳过|
|[编译器警告 （等级 1） C4628](../../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md)|-Ze 不支持二合字母。 字符序列 digraph 未解释为 %s 的替换标记|
|[编译器警告 （等级 C4629](compiler-warning-level-4-c4629.md)|使用了有向图，字符序列“digraph”解释为标记“char”（如果这不是你想要的，请在这两个字符之间插入一个空格）|
|[编译器警告 （等级 1） C4630](../../error-messages/compiler-warnings/compiler-warning-level-1-c4630.md)|symbol: extern 存储类说明符在成员定义上非法|
|编译器警告 （等级 2） C4631|MSXML 或 XPath 不可用，将不会处理 XML 文档注释。 原因|
|[编译器警告 （等级 1） C4632](../../error-messages/compiler-warnings/compiler-warning-level-1-c4632.md)|XML 文档注释： 文件的访问被拒绝： 原因|
|[编译器警告 （等级 3） C4633](../../error-messages/compiler-warnings/compiler-warning-level-3-c4633.md)|XML 文档注释目标： 错误： 原因|
|[编译器警告 （等级 C4634](compiler-warning-level-4-c4634.md)|XML 文档注释目标： 不能应用： 原因|
|[编译器警告 （等级 3） C4635](compiler-warning-level-3-c4635.md)|XML 文档注释目标: XML 格式不正确: 原因|
|[编译器警告 （等级 3） C4636](compiler-warning-level-3-c4636.md)|应用于构造的 XML 文档注释： 标记需要非空 attribute 特性。|
|[编译器警告 （等级 3 和 4） C4637](compiler-warning-level-3-c4637.md)|XML 文档注释目标：\<包括 > 标记被丢弃。 原因|
|[编译器警告 （等级 3） C4638](compiler-warning-level-3-c4638.md)|XML 文档注释目标： 引用未知符号 symbol。|
|[编译器警告 （等级 C4639](../../error-messages/compiler-warnings/compiler-warning-level-4-c4639.md)|MSXML 错误，不会处理注释的 XML 文档。 原因|
|[编译器警告 （等级 3） C4640](../../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md)|“instance”: 本地静态对象的结构是非线程安全的|
|[编译器警告 （等级 3） C4641](../../error-messages/compiler-warnings/compiler-warning-level-3-c4641.md)|XML 文档注释含有不明确的交叉引用：|
|[编译器警告 （等级 3） C4645](compiler-warning-level-3-c4645.md)|用 __declspec(noreturn) 声明的函数有返回语句|
|[编译器警告 （等级 3） C4646](compiler-warning-level-3-c4646.md)|用 __declspec(noreturn) 声明的函数有非 void 返回类型|
|编译器警告 （等级 3） C4647|行为更改： __is_pod (*类型*) 在早期版本中具有不同的值|
|编译器警告 （等级 3） C4648|忽略标准属性 carries_dependency|
|编译器警告 （等级 3） C4649|此上下文中忽略了属性|
|[编译器警告 （等级 1） C4650](../../error-messages/compiler-warnings/compiler-warning-level-1-c4650.md)|调试信息不在预编译标头;将可仅从标头的全局符号|
|[编译器警告 （等级 1） C4651](../../error-messages/compiler-warnings/compiler-warning-level-1-c4651.md)|指定有关预编译标头而不是当前编译的定义|
|[编译器警告 （等级 1） C4652](../../error-messages/compiler-warnings/compiler-warning-level-1-c4652.md)|编译器选项 option 与预编译标头; 不一致当前命令行选项将重写预编译标头中定义的|
|[编译器警告 （等级 2） C4653](../../error-messages/compiler-warnings/compiler-warning-level-2-c4653.md)|编译器选项 option 与预编译标头; 不一致忽略当前命令行选项|
|编译器警告 （等级 C4654|代码放在包含的预编译标头行中将被忽略。 将代码添加到预编译标头。|
|[编译器警告 （等级 1） C4655](compiler-warning-level-1-c4655.md)|symbol： 变量类型是最新版本，因为新的或在其他地方以不同的方式定义|
|[编译器警告 （等级 1） C4656](../../error-messages/compiler-warnings/compiler-warning-level-1-c4656.md)|symbol： 数据类型新增功能或自最后生成以来已更改或在其他地方以不同的方式定义|
|[编译器警告 （等级 1） C4657](compiler-warning-level-1-c4657.md)|表达式涉及从最新生成以来的新的数据类型|
|编译器警告 （等级 1） C4658|function： 函数原型是最新版本，因为新的或在其他地方以不同的方式声明|
|[编译器警告 （等级 1） C4659](../../error-messages/compiler-warnings/compiler-warning-level-1-c4659.md)|#pragma 杂注： 行为未定义的保留段领域的使用，请使用 #pragma comment (linker，...)|
|[编译器警告 （等级 1） C4661](../../error-messages/compiler-warnings/compiler-warning-level-1-c4661.md)|identifier： 没有提供显式模板实例化请求适当的定义|
|[编译器警告 （等级 1） C4662](compiler-warning-level-1-c4662.md)|显式实例化；模板类“identifier1”无用于专用化“identifier2”的定义|
|[编译器警告 （等级 1） C4667](../../error-messages/compiler-warnings/compiler-warning-level-1-c4667.md)|function： 没有匹配的函数模板定义与强制实例化|
|[编译器警告 （等级 C4668](../../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md)|symbol 未定义为预处理器宏，用"0"替换为 directive|
|[编译器警告 （等级 1） C4669](../../error-messages/compiler-warnings/compiler-warning-level-1-c4669.md)|cast： 不安全的转换: class 是托管的类型对象|
|[编译器警告 （等级 C4670](compiler-warning-level-4-c4670.md)|identifier： 此基类不可访问|
|编译器警告 （等级 C4671|identifier： 复制构造函数不可访问|
|[编译器警告 （等级 C4672](compiler-warning-level-4-c4672.md)|identifier1： 不明确。 首先被看作“identifier2”|
|[编译器警告 （等级 C4673](../../error-messages/compiler-warnings/compiler-warning-level-4-c4673.md)|引发以下类型的 identifier 不会被视为在 catch 站点|
|[编译器警告 （等级 1） C4674](compiler-warning-level-1-c4674.md)|“方法”应声明为“静态”，而且只能有一个参数|
|编译器警告 （等级 C4676|%s: 析构函数不可访问|
|[编译器警告 （等级 1） C4677](../../error-messages/compiler-warnings/compiler-warning-level-1-c4677.md)|function： 非私有成员的签名包含程序集私有类型 private_type|
|[编译器警告 （等级 1） 可能出现 c4678 错误](compiler-warning-level-1-c4678.md)|基类“base_type”的可访问性比“derived_type”低|
|[编译器警告 （等级 1） C4679](../../error-messages/compiler-warnings/compiler-warning-level-1-c4679.md)|member： 无法导入成员|
|[编译器警告 （等级 C4680](../../error-messages/compiler-warnings/compiler-warning-level-4-c4680.md)|class： 组件类不指定默认接口|
|[编译器警告 （等级 C4681](compiler-warning-level-4-c4681.md)|class： 组件类不指定是事件源的默认接口|
|[编译器警告 （等级 C4682](compiler-warning-level-4-c4682.md)|parameter： 指定，默认为 [in] 未方向参数特性|
|[编译器警告 （等级 1） C4683](../../error-messages/compiler-warnings/compiler-warning-level-1-c4683.md)|function： 事件源有输出的参数;挂接多个事件处理程序时应谨慎|
|[编译器警告 （等级 1） C4684](../../error-messages/compiler-warnings/compiler-warning-level-1-c4684.md)|attribute:警告!! 属性可能会导致生成无效代码： 小心使用|
|[编译器警告 （等级 1） C4685](compiler-warning-level-1-c4685.md)|分析模板参数时需要“> >”，却找到了“>>”|
|[编译器警告 （等级 3） C4686](../../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)|“user-defined type”: 行为可能有更改，UDT 中的更改返回调用约定|
|[编译器警告 C4687 （错误）](../../error-messages/compiler-warnings/compiler-warning-c4687.md)|class： 密封的抽象类不能实现接口 interface|
|[编译器警告 （等级 1） C4688](../../error-messages/compiler-warnings/compiler-warning-level-1-c4688.md)|“constraint”：约束列表包含程序集私有类型“type”|
|编译器警告 （等级 1） C4689|%c： 不受支持的 #pragma 的 detect_mismatch; 中的字符忽略 #pragma|
|[编译器警告 （等级 C4690](../../error-messages/compiler-warnings/compiler-warning-level-4-c4690.md)|\[ emitidl (pop)]: 比入栈的多个|
|[编译器警告 （等级 1） C4691](../../error-messages/compiler-warnings/compiler-warning-level-1-c4691.md)|type： 在未引用程序集 file，而是使用了当前翻译单元中定义的类型应是引用类型|
|[编译器警告 （等级 1） C4692](../../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)|“function”: 非私有成员的签名包含程序集私有本机类型“native_type”|
|[编译器警告 （等级 1，错误） C4693](../../error-messages/compiler-warnings/compiler-warning-c4693.md)|class： 密封的抽象类不能有任何实例成员实例 member|
|[编译器警告 （等级 1，错误） C4694](../../error-messages/compiler-warnings/compiler-warning-c4694.md)|class： 密封的抽象类不能有基类 base_class|
|编译器警告 （等级 1） C4695|#pragma execution_character_set: 字符集不是受支持的参数： 支持当前仅 utf-8|
|编译器警告 （等级 1） C4696|/ 超出范围; ZBvalue1 选项假定 value2|
|[编译器警告 （等级 1 和 4） C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|未初始化的局部变量 name|
|[编译器警告 （等级 C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)|可能未初始化的局部变量 name|
|[编译器警告 （等级 C4702](../../error-messages/compiler-warnings/compiler-warning-level-4-c4702.md)|无法访问的代码|
|[编译器警告 （等级 C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|可能未初始化的局部指针变量 %s|
|[编译器警告 （等级 C4706](../../error-messages/compiler-warnings/compiler-warning-level-4-c4706.md)|条件表达式内的赋值|
|[编译器警告 （等级 C4709](../../error-messages/compiler-warnings/compiler-warning-level-4-c4709.md)|数组索引表达式中的逗号运算符|
|[编译器警告 （等级 C4710](../../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md)|“function”: 函数未内联|
|[编译器警告 （等级 1） C4711](../../error-messages/compiler-warnings/compiler-warning-level-1-c4711.md)|函数 function 为自动内联扩展选择|
|[编译器警告 （等级 C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)|函数 function 标记为 __forceinline 未内联|
|[编译器警告 （等级 1） C4715](../../error-messages/compiler-warnings/compiler-warning-level-1-c4715.md)|function： 并非所有控件路径都返回值|
|[编译器警告 （等级 1，错误） C4716](../../error-messages/compiler-warnings/compiler-warning-level-1-c4716.md)|function： 必须返回值|
|[编译器警告 （等级 1） C4717](../../error-messages/compiler-warnings/compiler-warning-level-1-c4717.md)|function： 递归的所有控件路径，函数将导致运行时堆栈溢出|
|[编译器警告 （等级 C4718](compiler-warning-level-4-c4718.md)|function call： 递归调用没有任何副作用，删除|
|编译器警告 （等级 1） C4719|指定 Qfast 时发现的使用 f 作为后缀以指示单精度的双精度常量|
|编译器警告 （等级 2） C4720|内联汇编程序报告: message|
|编译器警告 （等级 1） C4721|function： 不可用作内部函数|
|[编译器警告 （等级 1） C4722](compiler-warning-level-1-c4722.md)|function： 析构函数永远不会返回，可能会发生内存泄漏|
|[编译器警告 （等级 3） C4723](../../error-messages/compiler-warnings/compiler-warning-level-3-c4723.md)|潜在的被 0 除|
|[编译器警告 （等级 3） C4724](compiler-warning-level-3-c4724.md)|潜在的以 0 求模|
|编译器警告 （等级 3） C4725|在一些 Pentium 中，指令可能不准确|
|[编译器警告 （等级 1） C4727](../../error-messages/compiler-warnings/compiler-warning-level-1-c4727.md)|PCH 命名 pch_file obj_file_1 和 obj_file_2 中找到的相同时间戳。  使用第一个 PCH。|
|编译器警告 （等级 1） C4728|/Yl-选项被忽略，因为需要 PCH 引用|
|编译器警告 （等级 C4729|根据警告，函数对于流图形太大|
|[编译器警告 (级别 1) C4730](../../error-messages/compiler-warnings/compiler-warning-level-1-c4730.md)编译器警告 （等级 1） C4730|main： 混合 _m64 和浮点表达式可能会导致不正确的代码|
|[编译器警告 (级别 1) C4731](../../error-messages/compiler-warnings/compiler-warning-level-1-c4731.md)|指针： 框架指针寄存器注册被内联程序集代码修改|
|编译器警告 （等级 1） C4732|在此体系结构不支持内部函数 %s|
|[编译器警告 (级别 1) C4733](../../error-messages/compiler-warnings/compiler-warning-level-1-c4733.md)|内联 asm 分配到"fs: 0": 未注册为安全处理程序的处理程序|
|[编译器警告 (级别 3) C4738](../../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md)|将 32 位浮点型结果存储在内存中，可能会降低性能|
|[编译器警告 （等级 1） C4739](compiler-warning-level-1-c4739.md)|对变量“var”的引用超过了其存储空间|
|[编译器警告 (级别 4) C4740](../../error-messages/compiler-warnings/compiler-warning-level-4-c4740.md)|工作流中或出内联 asm 代码会取消全局优化|
|[编译器警告 (级别 1) C4742](../../error-messages/compiler-warnings/compiler-warning-level-1-c4742.md)|var 具有 file1 和 file2 中的不同对齐方式： 数字和数字|
|[编译器警告 (级别 1) C4743](../../error-messages/compiler-warnings/compiler-warning-level-1-c4743.md)|type 具有 file1 和 file2 中不同的大小： 数量和字节数|
|[编译器警告 (级别 1) C4744](../../error-messages/compiler-warnings/compiler-warning-level-1-c4744.md)|var 具有 file1 和 file2 中的不同类型: type1 和 type2|
|[编译器警告 C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)|可变访问*表达式*' 受 /volatile:\<iso&#124;ms > 设置; 请考虑使用 __iso_volatile_load/store 内部函数|
|[编译器警告 （等级 1） C4747](../../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)|调用托管 entrypoint:托管的代码可能无法运行在有加载程序锁，包括 DLL 入口点和调用从 DLL 入口点访问|
|编译器警告 （等级 C4749|有条件地支持： offsetof 应用于非布局类型*类型*|
|[编译器警告 （等级 1） C4750](compiler-warning-level-1-c4750.md)|“identifier”：函数 with _alloca() 内嵌到循环中|
|编译器警告 （等级 C4751|/arch: avx 不适用于 intel （） 流式处理 SIMD 扩展的内联 ASM 内|
|编译器警告 （等级 C4752|发现 intel （） 高级矢量扩展;请考虑使用 /arch: avx|
|[编译器警告 （等级 C4754](compiler-warning-level-4-c4754.md)|在 %s(%d) 的比较中的算术运算的转换规则意味着无法执行一个分支。 转换为 %s （或 %d 字节的相似类型） %s。|
|编译器警告 C4755|在 %s(%d) 的比较中的算术运算的转换规则意味着无法在内联函数中执行一个分支。 转换为 %s （或 %d 字节的相似类型） %s。|
|[编译器警告 （等级 2） C4756](../../error-messages/compiler-warnings/compiler-warning-level-2-c4756.md)|常量算法中溢出|
|编译器警告 （等级 C4757|下标是大无符号的值，是否负常量？|
|[编译器警告 （等级 C4764](compiler-warning-level-4-c4764.md)|无法对齐大于 16 个字节的捕获对象|
|编译器警告 （等级 C4767|节名称 '%s' 的长度超过 8 个字符，并将由链接器截断|
|编译器警告 （等级 3） C4768|已忽略链接规范前的 __declspec 特性|
|编译器警告 C4770|部分验证的枚举*名称*用作索引|
|编译器警告 C4771|必须使用简单的指针; 创建边界忽略了 MPX 内部函数|
|[编译器警告 （等级 1，错误） C4772](../../error-messages/compiler-warnings/compiler-warning-level-1-c4772.md)|#import 从缺少的类型库; 引用了类型missing_type 用作占位符|
|编译器警告 （等级 C4774|'*字符串*： 格式字符串参数中的预期*数*不是字符串文字|
|编译器警告 （等级 3） C4775|格式字符串中使用了非标准扩展*字符串*的函数*函数*|
|编译器警告 （等级 1） C4776|%*字符*'函数的格式字符串中不允许 '*函数*|
|编译器警告 （等级 C4777|'*函数*： 格式字符串*字符串*要求类型的自变量*type1*，但可变参数参数*数*具有类型*type2*|
|编译器警告 （等级 3） C4778|'*函数*： 未终止的格式字符串*字符串*|
|[编译器警告 (级别 1) C4788](../../error-messages/compiler-warnings/compiler-warning-level-1-c4788.md)|identifier： 标识符被截断为 number 个字符|
|[编译器警告 (级别 1) C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|缓冲区“identifier”(大小为 N 字节)将溢出；M 字节将在偏移 L 时开始写入|
|编译器警告 （等级 2） C4792|函数 %s 使用 sysimport 声明并从本机代码; 引用需要链接导入库|
|[编译器警告 （等级 1 和 3） C4793](../../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)|function： 函数编译为本机： \n\t'reason|
|[编译器警告 （等级 1） C4794](compiler-warning-level-1-c4794.md)|线程本地存储区变量 %s 从 '%s' 更改为 %s 的段|
|[编译器警告 （等级 1） C4799](../../error-messages/compiler-warnings/compiler-warning-level-1-c4799.md)|函数 function 有没有 EMMS 指令|

## <a name="see-also"></a>请参阅

[C /C++编译器和生成工具错误和警告](../compiler-errors-1/c-cpp-build-errors.md) \
[编译器警告 C4000-C5999](compiler-warnings-c4000-c5999.md)
