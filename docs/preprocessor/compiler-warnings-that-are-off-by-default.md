---
title: 默认情况下处于关闭状态的编译器警告 |Microsoft 文档
ms.date: 05/30/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- warnings, compiler
- cl.exe compiler, setting options
ms.assetid: 69809cfb-a38a-4035-b154-283a61938df8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d311c730781aee70d4b77723ddec98a79407e42a
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705561"
---
# <a name="compiler-warnings-that-are-off-by-default"></a>默认情况下处于关闭状态的编译器警告

因为大多数开发人员不希望看到它们，编译器将包含默认情况下，关闭的警告。 在某些情况下，它们表示一个样式的选择，或在较旧的代码中，是常见惯用语或利用语言的 Microsoft 扩展。 在其他情况下，它们指示其中程序员通常做出错误假设，这可能导致意外或未定义行为的区域。 有些警告可能存在非常干扰库标头中。 C 运行时库和 c + + 标准库旨在不发出任何警告只能在警告级别[/W4](../build/reference/compiler-option-warning-level.md)。

## <a name="enable-warnings-that-are-off-by-default"></a>启用默认为关闭的警告

您可以启用通常默认为关闭的通过使用以下选项之一的警告：

- **#pragma 警告 (默认：** *warning_number* **)**

   指定的警告 (*warning_number*) 在其默认级别启用。 该警告的文档包含该警告的默认级别。

- **#pragma 警告 (** *warning_level* **:** *warning_number* **)**

   指定的警告 (*warning_number*) 在指定级别启用 (*warning_level*)。

- [/Wall](../build/reference/compiler-option-warning-level.md)

   **/ 墙壁**启用默认情况下处于关闭状态的所有警告。 如果你使用此选项，你可以通过将个别警告关闭[/wd](../build/reference/compiler-option-warning-level.md)选项。

- [/w*Lnnnn*](../build/reference/compiler-option-warning-level.md)

   这使警告*nnnn*级别*L*。

## <a name="warnings-that-are-off-by-default"></a>默认情况下处于关闭状态的警告

以下警告处于关闭状态，默认情况下，Visual Studio 2015 和更高版本中：

|||
|-|-|
|[C4061](../error-messages/compiler-warnings/compiler-warning-level-4-c4061.md) （级别 4）|枚举器*标识符*中枚举的交换机*枚举*没有被 case 标签显式处理|
|[C4062](../error-messages/compiler-warnings/compiler-warning-level-4-c4062.md) （级别 4）|枚举器*标识符*中枚举的交换机*枚举*未处理|
|C4191（级别 3）|*运算符*： 从不安全转换*type_of_expression*到*type_required*|
|[C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) （级别 4）|*标识符*： 从转换*type1*到*type2*，可能丢失数据|
|[C4254](../error-messages/compiler-warnings/compiler-warning-level-4-c4254.md) （级别 4）|*运算符*： 从转换*type1*到*type2*，可能丢失数据|
|[C4255](../error-messages/compiler-warnings/compiler-warning-level-4-c4255.md) （级别 4）|*函数*： 函数原型给定： 转换到 (void) 的 ' （）'|
|[C4263](../error-messages/compiler-warnings/compiler-warning-level-4-c4263.md) （级别 4）|*函数*： 成员函数不重写任何基类虚拟成员函数|
|[C4264](../error-messages/compiler-warnings/compiler-warning-level-1-c4264.md) （级别 1）|*virtual_function*： 不重写基的虚拟成员函数的*类*; 函数被隐藏|
|[C4265](../error-messages/compiler-warnings/compiler-warning-level-3-c4265.md) （级别 3）|*类*： 类具有虚函数，但析构函数不是虚拟|
|[C4266](../error-messages/compiler-warnings/compiler-warning-level-4-c4266.md) （级别 4）|*函数*： 不重写基的虚拟成员函数的*类型*; 函数被隐藏|
|[C4287](../error-messages/compiler-warnings/compiler-warning-level-3-c4287.md) （级别 3）|*运算符*： 无符号/负常量不匹配|
|[C4289](../error-messages/compiler-warnings/compiler-warning-level-4-c4289.md) （级别 4）|使用的非标准扩展:*var*： 在 for 循环中声明的循环控制变量用在了 for 循环范围外|
|[C4296](../error-messages/compiler-warnings/compiler-warning-level-4-c4296.md) （级别 4）|*运算符*： 表达式始终为 false|
|[C4339](../error-messages/compiler-warnings/compiler-warning-level-4-c4339.md) （级别 4）|*类型*： 未定义的类型检测到使用在 CLR 元数据-使用此类型可能导致运行时异常|
|[C4342](../error-messages/compiler-warnings/compiler-warning-level-1-c4342.md) （级别 1）|行为更改:*函数*调用，但在早期版本中调用时是成员运算符|
|[C4350](../error-messages/compiler-warnings/compiler-warning-level-1-c4350.md) （级别 1）|行为更改:*member1*而不是调用*member2*|
|[C4355](../error-messages/compiler-warnings/compiler-warning-c4355.md)|“this”: 用于基成员初始值设定项列表|
|[C4365](../error-messages/compiler-warnings/compiler-warning-level-4-c4365.md) （级别 4）|*操作*： 从转换*type_1*到*type_2*，有符号/无符号不匹配|
|C4370 （级别 3）|为了更好地封装，类的布局与早期版本的编译器已有所不同|
|[C4371](../error-messages/compiler-warnings/c4371.md) （级别 3）|*classname*： 类的布局可能已更改从早期版本的编译器由于更好地封装成员*成员*|
|C4388 （级别 4）|有符号/无符号不匹配|
|[C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md) （2 级）|*函数*： 函数签名包含类型*类型*';不安全的时间间隔纯代码和混合或本机 c + + 对象是|
|C4426 （级别 1）|包含标头后, 更改的优化标志可能是由于 #pragma optimize （） 超出<sup>14.1</sup>|
|[C4435](../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md) （级别 4）|*class1*: /vd2 下的对象布局将因虚拟基而更改*class2*|
|[C4437](../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md) （级别 4）|从虚拟基的 dynamic_cast*class1*到*class2*可能会在某些上下文中失败|
|C4444 （级别 3）|顶级“__unaligned”没有在该上下文中实现|
|[C4464](../error-messages/compiler-warnings/c4464.md) （级别 4）|相对包含路径包含..|
|[C4471](../error-messages/compiler-warnings/compiler-warning-level-4-c4471.md) （级别 4）|未区分范围的枚举的前向声明必须具有基础类型 (假定为 int) <sup>Perm</sup>|
|C4472 （级别 1）|*标识符*是本机枚举： 添加访问说明符 (private/public) 来声明托管的枚举|
|[C4514](../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md) （级别 4）|*函数*： 在删除未引用的内联函数|
|[C4536](../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md) （级别 4）|type name： 类型名超出了元数据限制为*限制*' 字符|
|[C4545](../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md) （级别 1）|逗号前的表达式计算为缺少自变量列表的函数|
|[C4546](../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md) （级别 1）|逗号前的函数调用缺少自变量列表|
|[C4547](../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md) （级别 1）|*运算符*： 逗号不起任何作用; 前的运算符预期带副作用的运算符|
|[C4548](../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md) （级别 1）|逗号前的表达式不起任何作用；应输入带副作用的表达式|
|[C4549](../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md) （级别 1）|*operator1*： 逗号前的运算符起任何作用; 是否要使用*operator2*？|
|[C4555](../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md) （级别 1）|表达式无效；应输入带副作用的表达式|
|[C4557](../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md) （级别 3）|__assume 包含效果*效果*|
|[C4571](../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md) （级别 4）|自 Visual c + + 7.1; 以来更改的信息： 之后语义不再捕获结构化的异常 (SEH)|
|C4574 （级别 4）|*标识符*定义为"0： 你是否希望使用 #if*标识符*？|
|C4577 （级别 1）|noexcept 用于没有异常处理模式，以指定;不保证异常终止。 指定 /EHsc|
|C4582 （级别 4）|*类型*： 不隐式调用构造函数|
|C4583 （级别 4）|*类型*： 不隐式调用析构函数|
|C4587 （级别 1）|*anonymous_structure*： 行为更改： 不再隐式调用构造函数|
|C4588 （级别 1）|*anonymous_structure*： 行为更改： 不再隐式调用析构函数|
|C4596 （级别 4）|*标识符*： 非法的限定的名称，在成员声明<sup>14.3</sup> <sup>Perm</sup>|
|C4598 （级别 1 和等级 3）|#include"*标头*"： 标头编号*数*预编译标头不匹配当前的编译中的该位置<sup>14.3</sup>|
|C4599 （级别 3）|*选项**路径*： 命令行自变量数量*数*与预编译标头不匹配<sup>14.3</sup>|
|C4605 （级别 1）|/D*宏*当前的命令行上指定但未指定时生成预编译标头|
|[C4608](../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md) （级别 3）|*union_member*已初始化在初始值设定项列表中，另一个联合成员*union_member* <sup>Perm</sup>|
|[C4619](../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md) （级别 3）|#pragma 警告： 没有警告编号*数*|
|[C4623](../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md) （级别 4）|“derived class”: 未能生成默认构造函数，因为基类默认构造函数不可访问|
|[C4625](../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md) （级别 4）|“derived class”: 未能生成复制构造函数，因为基类复制构造函数不可访问|
|[C4626](../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md) （级别 4）|“derived class”: 未能生成赋值运算符，因为基类赋值运算符不可访问|
|[C4628](../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md) （级别 1）|-Ze 不支持二合字母。 字符序列*digraph*未解释为用于替换标记*char*|
|[C4640](../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md) （级别 3）|*实例*： 本地静态对象的构造不是线程安全|
|C4647 （级别 3）|行为更改： __is_pod (*类型*) 在以前版本中具有不同的值|
|C4654 （级别 4）|前后放置的代码包含预编译标头的行将被忽略。 将代码添加到预编译标头。 <sup>14.1</sup>|
|[C4668](../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md) （级别 4）|*符号*未定义为预处理器宏，用"0"替换为中*指令*|
|[C4682](../error-messages/compiler-warnings/compiler-warning-level-4-c4682.md) （级别 4）|*符号*： 指定，默认为 [in] 未方向参数特性|
|[C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md) （级别 3）|*用户定义类型*： 行为可能有更改，UDT 中的更改返回调用约定|
|[C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) （级别 1）|*函数*： 非私有成员的签名包含程序集私有本机类型*native_type*|
|[C4710](../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md) （级别 4）|*函数*： 函数未内联|
|[C4738](../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md) （级别 3）|将 32 位浮点型结果存储在内存中，可能会降低性能|
|[C4746](../error-messages/compiler-warnings/compiler-warning-c4746.md)|可变访问*表达式*受到 /volatile:\<iso&#124;ms > 设置; 请考虑使用 __iso_volatile_load/store 内部函数|
|C4749 （级别 4）|有条件地支持： offsetof 应用于 non standard 布局类型*类型*|
|C4767 （级别 4）|节名称*符号*的长度超过 8 个字符，将链接器截断|
|C4768 （级别 3）|则将忽略链接规范的前面的 __declspec 属性|
|C4774 （级别 4）|*字符串*： 格式字符串中自变量应*数*不是字符串文本|
|C4777 （级别 4）|*函数*： 格式字符串*字符串*要求类型自变量*type1*，但可变参数自变量*数*具有类型*type2*|
|C4786 （级别 3）|*符号*： 对象名称被截断为*数*中的调试信息的字符|
|[C4820](../error-messages/compiler-warnings/compiler-warning-level-4-c4820.md) （级别 4）|*字节*字节填充添加在构造之后*member_name*|
|C4826 （2 级）|从*type1*到*type2*进行符号扩展。 这可能导致意外的运行时行为。|
|C4837 （级别 4）|检测到的三元组:??*字符*替换为*字符*|
|C4841 （级别 4）|使用的非标准扩展： offsetof 中使用的复合成员指示符|
|C4842 （级别 4）|offsetof 应用于使用多重继承的类型的结果不是保证是编译器版本之间一致|
|[C4868](../error-messages/compiler-warnings/compiler-warning-c4868.md) （级别 4）|_文件_(*line_number*) 编译器可能会不强制实施在大括号内的初始化列表中从左到右计算顺序|
|[C4905](../error-messages/compiler-warnings/compiler-warning-level-1-c4905.md) （级别 1）|宽字符串强制转换为“LPSTR”|
|[C4906](../error-messages/compiler-warnings/compiler-warning-level-1-c4906.md) （级别 1）|字符串强制转换为“LPWSTR”|
|[C4917](../error-messages/compiler-warnings/compiler-warning-level-1-c4917.md) （级别 1）|*声明符*: GUID 只能与类、 接口或命名空间关联|
|[C4928](../error-messages/compiler-warnings/compiler-warning-level-1-c4928.md) （级别 1）|副本初始化非法；隐式应用了多个用户定义的转换|
|[C4931](../error-messages/compiler-warnings/compiler-warning-level-4-c4931.md) （级别 4）|我们假定类型库是为 number 位指针生成的|
|[C4946](../error-messages/compiler-warnings/compiler-warning-level-1-c4946.md) （级别 1）|reinterpret_cast 在相关类之间使用:*class1*和*class2*|
|C4962|*函数*： 已禁用在于优化导致了配置文件数据变得不一致的按配置文件优化|
|[C4986](../error-messages/compiler-warnings/compiler-warning-c4986.md) （级别 4）|*符号*： 异常规范与前面的声明不匹配|
|C4987 （级别 4）|使用了非标准扩展：“throw (...)”|
|C4988 （级别 4）|*符号*： 声明外部类/函数范围变量|
|C5022|*类型*： 指定了多个移动构造函数|
|C5023|*类型*： 指定的多个移动赋值运算符|
|C5024 （级别 4）|*类型*： 移动构造函数隐式定义，为已删除|
|C5025 （级别 4）|*类型*： 移动赋值运算符已隐式定义为已删除|
|C5026 （级别 1 和等级 4）|*类型*： 移动构造函数隐式定义，为已删除|
|C5027 （级别 1 和等级 4）|*类型*： 移动赋值运算符已隐式定义为已删除|
|C5029 （级别 4）|使用的非标准扩展： c + + 中的对齐方式属性应用于变量、 数据成员和仅适用于标记类型|
|C5031 （级别 4）|#pragma warning （pop): 可能不匹配，弹出推入不同的文件的警告状态<sup>14.1</sup>|
|C5032 （级别 4）|检测到与测试 warning （没有相应 #pragma pop） #pragma warning （push） <sup>14.1</sup>|
|C5034|使用内部函数的*内部*将导致函数*函数*编译为访客代码<sup>15.3</sup>|
|C5035|使用的功能*功能*将导致函数*函数*编译为访客代码<sup>15.3</sup>|
|C5036 （级别 1）|varargs 函数指针转换使用 /hybrid:x86arm64 编译时*type1*到*type2* <sup>15.3</sup>|
|[C5038](../error-messages/compiler-warnings/c5038.md) （级别 4）|数据成员*member1*将数据成员后初始化*member2* <sup>15.3</sup>|
|C5039 （级别 4）|*函数*： 指针或对可能引发函数引用传递给下-EHc extern C 函数。 如果此函数将引发异常，则可能出现未定义的行为。 <sup>15.5</sup>|
|C5042 （级别 3）|*函数*： 在块范围的函数声明不能指定为内联，在标准 c + +; 中删除内联说明符<sup>15.5</sup>|

<sup>14.1</sup>此警告可从 Visual Studio 2015 Update 1 开始。<br>
<sup>14.3</sup>此警告是在 Visual Studio 2015 Update 3 中开始提供。<br>
<sup>15.3</sup>此警告是在 Visual Studio 2017 版本 15.3 中开始提供。<br>
<sup>15.5</sup>此警告是在 Visual Studio 2017 版本 15.5 中开始提供。<br>
<sup>Perm</sup>此警告处于关闭状态，除非[/ 宽松-](../build/reference/permissive-standards-conformance.md)设置编译器选项。

## <a name="warnings-off-by-default-in-earlier-versions"></a>默认情况下，在早期版本中关闭的警告

默认情况下，在版本的 Visual Studio 2015 之前编译器情况下，这些警告已关闭状态：

|||
|-|-|
|[C4302](../error-messages/compiler-warnings/compiler-warning-level-2-c4302.md) （2 级）|*转换*： 从截断*type1*到*type2*|
|[C4311](../error-messages/compiler-warnings/compiler-warning-level-1-c4311.md) （级别 1）|*变量*： 从的指针截断*类型*到*类型*|
|[C4312](../error-messages/compiler-warnings/compiler-warning-level-1-c4312.md) （级别 1）|*操作*： 从转换*type1*到*type2*更大的|
|[C4319](../error-messages/compiler-warnings/compiler-warning-level-1-c4319.md) （级别 1）|*运算符*： 零扩展*type1*到*type2*更大的|

此警告关闭时，默认情况下，在 Visual Studio 2012 之前的编译器的版本：

|||
|-|-|
|[C4431](../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md) （级别 4）|缺少类型说明符 - 假定为 int。 注意: C 不再支持默认的 int|

## <a name="see-also"></a>请参阅

[warning](../preprocessor/warning.md)
