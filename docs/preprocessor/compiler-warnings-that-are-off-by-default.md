---
title: 默认关闭的编译器警告
ms.date: 08/29/2019
helpviewer_keywords:
- warnings, compiler
- cl.exe compiler, setting options
ms.assetid: 69809cfb-a38a-4035-b154-283a61938df8
ms.openlocfilehash: d497886b22c7a90ab7cda47e46dc13daf297b192
ms.sourcegitcommit: b4572ffcc71e6bdb0ca23221f9476cfaf4528406
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/26/2019
ms.locfileid: "71314456"
---
# <a name="compiler-warnings-that-are-off-by-default"></a>默认关闭的编译器警告

编译器支持默认情况下处于关闭状态的警告，因为大多数开发人员都不会发现它们很有用。 在某些情况下，它们会警告样式选择，或者有关较旧代码中的常见惯例。 其他警告涉及到使用 Microsoft 扩展语言。 在其他情况下，它们表示程序员经常做出错误假设的区域，这可能导致意外或未定义的行为。 如果启用，某些警告可能会在库标头中出现多次。 C 运行时库和C++标准库旨在仅在警告级别[/W4](../build/reference/compiler-option-warning-level.md)发出警告。

## <a name="enable-warnings-that-are-off-by-default"></a>启用默认情况下处于关闭状态的警告

您可以通过使用以下选项之一，启用通常默认情况下处于关闭状态的警告：

- **#pragma warning(default :** *warning_number* **)**

   指定的警告（*warning_number*）在其默认级别启用。 该警告的文档包含该警告的默认级别。

- **#pragma warning(** *warning_level* **:** *warning_number* **)**

   指定的警告（*warning_number*）在指定的级别（*warning_level*）启用。

- [/Wall](../build/reference/compiler-option-warning-level.md)

   `/Wall` 将启用默认情况下禁用的所有警告。 如果使用此选项，则可以使用[/wd](../build/reference/compiler-option-warning-level.md)选项关闭单个警告。

- [/w*Lnnnn*](../build/reference/compiler-option-warning-level.md)

   此选项在级别*L*下启用警告*nnnn* 。

## <a name="warnings-that-are-off-by-default"></a>默认情况下处于关闭状态的警告

默认情况下，在 Visual Studio 2015 和更高版本中关闭以下警告：

|||
|-|-|
|[C4061](../error-messages/compiler-warnings/compiler-warning-level-4-c4061.md)（级别4）|枚举 "*enumeration*" 的 switch 中的枚举器 "*identifier*" 未由 case 标签显式处理|
|[C4062](../error-messages/compiler-warnings/compiler-warning-level-4-c4062.md)（级别4）|未处理枚举 "*enumeration*" 的 switch 中的枚举器 "*identifier*"|
| [C4165](../error-messages/compiler-warnings/compiler-warning-level-1-c4165.md)（等级1） | "HRESULT" 正在转换为 "bool";是否确实要这样做？ |
| [C4191](../error-messages/compiler-warnings/compiler-warning-level-3-c4191.md)（等级3）|"*operator*"：从 "*type_of_expression*" 到 "*type_required*" 的不安全转换|
|[C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md)（级别4）|"*identifier*"：从 "*type1*" 转换到 "*type2*"，可能丢失数据|
|[C4254](../error-messages/compiler-warnings/compiler-warning-level-4-c4254.md)（级别4）|"*operator*"：从 "*type1*" 转换到 "*type2*"，可能丢失数据|
|[C4255](../error-messages/compiler-warnings/compiler-warning-level-4-c4255.md)（级别4）|"*function*"：未给出函数原型：将 "（）" 转换为 "（void）"|
|[C4263](../error-messages/compiler-warnings/compiler-warning-level-4-c4263.md)（级别4）|"*function*"：成员函数不重写任何基类虚拟成员函数|
|[C4264](../error-messages/compiler-warnings/compiler-warning-level-1-c4264.md)（等级1）|"*virtual_function*"：不能重写基 "*class*" 中的虚拟成员函数;函数被隐藏|
|[C4265](../error-messages/compiler-warnings/compiler-warning-level-3-c4265.md)（等级3）|"*class*"：类有虚函数，但析构函数不是虚拟的|
|[C4266](../error-messages/compiler-warnings/compiler-warning-level-4-c4266.md)（级别4）|"*function*"：不能重写基 "*type*" 中的虚拟成员函数;函数被隐藏|
|[C4287](../error-messages/compiler-warnings/compiler-warning-level-3-c4287.md)（等级3）|"*operator*"：无符号/负常量不匹配|
|[C4289](../error-messages/compiler-warnings/compiler-warning-level-4-c4289.md)（级别4）|使用了非标准扩展： "*var*"：在 for 循环中声明的循环控制变量用在了 for 循环范围之外|
|[C4296](../error-messages/compiler-warnings/compiler-warning-level-4-c4296.md)（级别4）|"*operator*"： expression 始终为 false|
|[C4339](../error-messages/compiler-warnings/compiler-warning-level-4-c4339.md)（级别4）|"*type*"：在 CLR 元数据中检测到使用了未定义的类型-使用此类型可能导致运行时异常|
|[C4342](../error-messages/compiler-warnings/compiler-warning-level-1-c4342.md)（等级1）|行为更改：调用了 "*function*"，但在以前的版本中调用了成员运算符|
|[C4350](../error-messages/compiler-warnings/compiler-warning-level-1-c4350.md)（等级1）|行为更改：调用了 "*member1*" 而不是 "*member2*"|
|[C4355](../error-messages/compiler-warnings/compiler-warning-c4355.md)|“this”: 用于基成员初始值设定项列表|
|[C4365](../error-messages/compiler-warnings/compiler-warning-level-4-c4365.md)（级别4）|"*action*"：从 "*type_1*" 转换为 "*type_2*"，有符号/无符号不匹配|
|C4370 （等级3）|为了更好地封装，类的布局与早期版本的编译器已有所不同|
|[C4371](../error-messages/compiler-warnings/c4371.md)（等级3）|"*classname*"：类的布局可能与早期版本的编译器发生了变化，因为更好地封装了成员 "*member*"|
|C4388 （级别4）|有符号/无符号不匹配|
|[C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md)（级别2）|"*function*"：函数签名包含类型 "*type*";C++对象不安全地在纯代码与混合或本机之间传递|
|C4426 （等级1）|包含标头后更改了优化标志，原因可能是 #pragma optimize （） <sup>14.1</sup>|
|[C4435](../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md)（级别4）|"*class1*"：/Vd2 下的对象布局将因虚拟基 "*class2*" 而更改|
|[C4437](../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)（级别4）|从虚拟基 "*class1*" 到 "*class2*" 的 dynamic_cast 在某些上下文中可能会失败|
|C4444 （等级3）|顶级“__unaligned”没有在该上下文中实现|
|[C4464](../error-messages/compiler-warnings/c4464.md)（级别4）|相对包含路径包含 ".."|
|[C4471](../error-messages/compiler-warnings/compiler-warning-level-4-c4471.md)（级别4）|未区分范围的枚举的前向声明必须有基础类型（假定为 int）<sup>永久状态</sup>|
|C4472 （等级1）|"*identifier*" 是本机枚举：添加访问说明符（private/public）以声明托管枚举|
|[C4514](../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md)（级别4）|"*function*"：未引用的内联函数已移除|
|[C4536](../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md)（级别4）|"type name"：类型名称超出了 "*限制*" 字符的元数据限制|
|[C4545](../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md)（等级1）|逗号前的表达式计算为缺少自变量列表的函数|
|[C4546](../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md)（等级1）|逗号前的函数调用缺少自变量列表|
|[C4547](../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md)（等级1）|"*operator*"：逗号前的运算符不起任何作用;应有副作用的运算符|
|[C4548](../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md)（等级1）|逗号前的表达式不起任何作用；应输入带副作用的表达式|
|[C4549](../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md)（等级1）|"*operator1*"：逗号前的运算符不起任何作用;是否想要 "*operator2*"？|
|[C4555](../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md)（等级1）|表达式无效；应输入带副作用的表达式|
|[C4557](../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md)（等级3）|"__assume" 包含效果 "*效果*"|
|[C4571](../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md)（级别4）|信息：自 Visual C++ 7.1 以来，catch （...）语义发生了变化;不再捕获结构化的异常（SEH）|
|C4574 （级别4）|"*identifier*" 被定义为 "0"：您是否希望使用 "#if*标识符*"？|
|C4577 （等级1）|在未指定异常处理模式的情况下使用 "noexcept";不保证异常终止。 指定/EHsc|
|C4582 （级别4）|"*type*"：构造函数未隐式调用|
|C4583 （级别4）|"*type*"：析构函数未隐式调用|
|C4587 （等级1）|"*anonymous_structure*"：行为更改：不再隐式调用构造函数|
|C4588 （等级1）|"*anonymous_structure*"：行为更改：不再隐式调用析构函数|
|[C4596](../error-messages/compiler-warnings/c4596.md)（级别4）|"*identifier*"：成员声明中的非法限定名<sup>14.3</sup> <sup>永久状态</sup>|
|C4598 （等级1和等级3）|"#include"*标头*""：预编译标头中的标头编号*号*与该位置的当前编译不匹配<sup>14.3</sup>|
|C4599 （等级3）|'*选项* *路径*： 命令行参数号*数*与预编译标头不匹配<sup>14.3</sup>|
|C4605 （等级1）|在当前命令行上指定了 "/d*宏*"，但未在生成预编译标头时指定|
|[C4608](../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)（等级3）|"*union_member*" 已被初始值设定项列表 "*union_member*" 中的另一个联合成员初始化<sup>永久状态</sup>|
|[C4619](../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md)（等级3）|#pragma 警告：无警告编号 "*number*"|
|[C4623](../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md)（级别4）|“derived class”: 未能生成默认构造函数，因为基类默认构造函数不可访问|
|[C4625](../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md)（级别4）|“derived class”: 未能生成复制构造函数，因为基类复制构造函数不可访问|
|[C4626](../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md)（级别4）|“derived class”: 未能生成赋值运算符，因为基类赋值运算符不可访问|
|[C4628](../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md)（等级1）|-Ze 不支持二合字母。 字符序列 "*连字*" 未解释为 "*char*" 的替换标记|
|[C4640](../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md)（等级3）|"*instance*"：局部静态对象的构造不是线程安全的|
| C4643 （级别4） | 标准不允许在命名空间 std 中使用前向声明 "identifier"。 C++ <sup>15.8</sup> |
|C4647 （等级3）|行为更改： __is_pod （*类型*）在以前的版本中具有不同的值|
|C4654 （级别4）|将忽略在预编译标头行的包含之前放置的代码。 将代码添加到预编译头。 <sup>14.1</sup>|
|[C4668](../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md)（级别4）|"*symbol*" 未定义为预处理器宏，用 "0" 替换 "*指令*"|
|[C4682](../error-messages/compiler-warnings/compiler-warning-level-4-c4682.md)（级别4）|"*symbol*"：未指定方向参数特性，默认为 [in]|
|[C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)（等级3）|"*用户定义类型*"：行为可能有更改，UDT 中的更改返回调用约定|
|[C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)（等级1）|"*function*"：非私有成员的签名包含程序集私有本机类型 "*native_type*"|
|[C4710](../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md)（级别4）|"*function*"：函数未内联|
|[C4738](../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md)（等级3）|将 32 位浮点型结果存储在内存中，可能会降低性能|
|[C4746](../error-messages/compiler-warnings/compiler-warning-c4746.md)|"*expression*" 的可变访问受/volatile：\<iso&#124;ms > 设置的限制; 请考虑使用 __iso_volatile_load/存储内部函数|
|C4749 （级别4）|有条件支持： offsetof 应用于非标准布局类型 "*type*"|
|C4767 （级别4）|节名称 "*symbol*" 的长度超过8个字符，将被链接器截断|
|C4768 （等级3）|忽略链接规范前的 __declspec 特性|
|C4774 （级别4）|"*string*"：参数*号*中应为格式字符串不是字符串文本|
|C4777 （级别4）|"*function*"：格式字符串 "*string*" 需要类型为 "*type1*" 的参数，但可变参数参数*号*的类型为 "*type2*"|
|C4786 （等级3）|"*symbol*"：对象名被截断为调试信息中的 "*number*" 个字符|
| [C4800](../error-messages/compiler-warnings/compiler-warning-level-3-c4800.md)（级别4） | 从 "*type*" 到布尔值的隐式转换。 可能的信息丢失<sup>16.0</sup> |
|[C4820](../error-messages/compiler-warnings/compiler-warning-level-4-c4820.md)（级别4）|在构造 "*member_name*" 之后添加了 "*bytes*" 字节填充|
| [C4822](../error-messages/compiler-warnings/compiler-warning-level-1-c4822.md)（等级1） | "*member*"：局部类成员函数没有主体 |
|C4826 （级别2）|从 "*type1*" 到 "*type2*" 的转换是带符号扩展的。 这可能导致意外的运行时行为。|
|C4837 （级别4）|检测到三元组： "？*字符*"替换为"*character*"|
|C4841 （级别4）|使用的非标准扩展： offsetof 中使用的复合成员指示符|
|C4842 （级别4）|使用多重继承应用到类型的 "offsetof" 结果不保证在编译器版本之间保持一致|
|[C4868](../error-messages/compiler-warnings/compiler-warning-c4868.md)（级别4）|"_file_（*line_number*）" 编译器不能在大括号内初始化列表中强制执行从左到右的计算顺序|
|[C4905](../error-messages/compiler-warnings/compiler-warning-level-1-c4905.md)（等级1）|宽字符串强制转换为“LPSTR”|
|[C4906](../error-messages/compiler-warnings/compiler-warning-level-1-c4906.md)（等级1）|字符串强制转换为“LPWSTR”|
|[C4917](../error-messages/compiler-warnings/compiler-warning-level-1-c4917.md)（等级1）|"*声明符*"： GUID 只能与类、接口或命名空间关联|
|[C4928](../error-messages/compiler-warnings/compiler-warning-level-1-c4928.md)（等级1）|副本初始化非法；隐式应用了多个用户定义的转换|
|[C4931](../error-messages/compiler-warnings/compiler-warning-level-4-c4931.md)（级别4）|我们假定类型库是为 number 位指针生成的|
|[C4946](../error-messages/compiler-warnings/compiler-warning-level-1-c4946.md)（等级1）|reinterpret_cast 在相关类之间使用： "*class1*" 和 "*class2*"|
|C4962|"*function*"：已禁用按配置文件优化，因为优化导致配置文件数据变得不一致|
|[C4986](../error-messages/compiler-warnings/compiler-warning-c4986.md)（级别4）|"*symbol*"：异常规范与前面的声明不匹配|
|C4987 （级别4）|使用了非标准扩展：“throw (...)”|
|C4988 （级别4）|"*symbol*"：在类/函数范围外声明的变量|
|C5022|"*type*"：指定了多个移动构造函数|
|C5023|"*type*"：指定了多个移动赋值运算符|
|C5024 （级别4）|"*type*"：移动构造函数被隐式定义为已删除|
|C5025 （级别4）|"*type*"：移动赋值运算符被隐式定义为已删除|
|C5026 （等级1和等级4）|"*type*"：移动构造函数被隐式定义为已删除|
|C5027 （等级1和等级4）|"*type*"：移动赋值运算符被隐式定义为已删除|
|C5029 （级别4）|使用了非标准扩展：中C++的对齐特性仅适用于变量、数据成员和标记类型|
|C5031 （级别4）|#pragma warning （pop）：可能不匹配，正在弹出的警告状态已推送到不同文件<sup>14.1</sup>|
|C5032 （级别4）|检测到 #pragma warning （push），没有对应的 #pragma 警告（pop） <sup>14.1</sup>|
|C5034|使用内部 "*内部*" 导致函数*函数*编译为来宾代码<sup>15.3</sup>|
|C5035|使用功能 "*feature*" 会导致函数*函数*编译为来宾代码<sup>15.3</sup>|
|C5036 （等级1）|将/hybrid： x86arm64 "*type1*" 编译为 "*type2*" <sup>15.3</sup>时，varargs 函数指针转换|
|[C5038](../error-messages/compiler-warnings/c5038.md)（级别4）|数据成员 "*member1*" 将在数据成员 "*member2*" <sup>15.3</sup>后初始化|
|C5039 （级别4）|"*function*"：指向在-EHc 下传递到 extern C 函数的可能引发函数的指针或引用。 如果此函数引发异常，则可能出现未定义的行为。 <sup>15.5</sup>|
|C5042 （等级3）|"*function*"：不能在标准C++中指定块范围内的函数声明;删除 "inline" 说明符<sup>15.5</sup>|
|[C5045](../error-messages/compiler-warnings/c5045.md)|如果/Qspectre 开关指定<sup>15.7</sup> ，编译器将插入内存加载的 Spectre 缓解|

<sup>14.1</sup>从 Visual Studio 2015 Update 1 开始提供此警告。\\<sup>14.3</sup>从 Visual Studio 2015 Update 3 开始提供此警告。\\<sup>15.3</sup>从 Visual Studio 2017 版本15.3 开始，此警告已推出。\\<sup>15.5</sup>从 Visual Studio 2017 版本15.5 开始，此警告已推出。\\<sup>15.7</sup>从 Visual Studio 2017 版本15.7 开始，此警告已推出。\\<sup>15.8</sup>从 Visual Studio 2017 版本15.8 开始，此警告已推出。\\<sup>16.0</sup>从 Visual STUDIO 2019 RTM 开始，此警告已推出。\\<sup>永久状态</sup>除非设置了[/permissive-](../build/reference/permissive-standards-conformance.md)编译器选项，否则将关闭此警告。

## <a name="warnings-off-by-default-in-earlier-versions"></a>默认情况下，在早期版本中关闭警告

默认情况下，在 Visual Studio 2015 之前的编译器版本中关闭这些警告：

|||
|-|-|
|[C4302](../error-messages/compiler-warnings/compiler-warning-level-2-c4302.md)（级别2）|"*转换*"：从 "*type1*" 到 "*type2*" 的截断|
|[C4311](../error-messages/compiler-warnings/compiler-warning-level-1-c4311.md)（等级1）|"*variable*"：从 "*type*" 到 "*type*" 的指针截断|
|[C4312](../error-messages/compiler-warnings/compiler-warning-level-1-c4312.md)（等级1）|"*operation*"：从 "*type1*" 转换为 "*type2*" 的大小更大|
|[C4319](../error-messages/compiler-warnings/compiler-warning-level-1-c4319.md)（等级1）|"*operator*"：将 "*type1*" 扩展到更大的 "*type2*" 时为零|

Visual Studio 2012 之前的编译器版本中默认关闭此警告：

|||
|-|-|
|[C4431](../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md)（级别4）|缺少类型说明符 - 假定为 int。 注意:C 不再支持默认值-int|

## <a name="see-also"></a>请参阅

[warning](../preprocessor/warning.md)
