---
title: 默认情况下处于关闭状态的编译器警告
ms.date: 05/30/2018
helpviewer_keywords:
- warnings, compiler
- cl.exe compiler, setting options
ms.assetid: 69809cfb-a38a-4035-b154-283a61938df8
ms.openlocfilehash: 0f306ef11b17ac94281dc9a5fdba55a34d236eb1
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400927"
---
# <a name="compiler-warnings-that-are-off-by-default"></a>默认关闭的编译器警告

编译器支持默认情况下，关闭的警告，因为大多数开发人员不发现它们很有用。 在某些情况下，它们发出警告有关样式的选择，或在较旧代码中常见的惯用语言。 有关使用语言的 Microsoft 扩展的其他警告。 在其他情况下，它们指示程序员经常做出错误的假设，这可能会导致意外的或未定义行为的区域。 如果启用，有些警告可能会很多时候显示库标头中。 C 运行时库和C++标准库旨在不发出任何警告仅在警告级别[/w4](../build/reference/compiler-option-warning-level.md)。

## <a name="enable-warnings-that-are-off-by-default"></a>启用默认情况下处于关闭状态的警告

您可以启用警告，方法是通常情况下关闭默认情况下使用以下选项之一：

- **#pragma warning(default :** *warning_number* **)**

   指定的警告 (*warning_number*) 在其默认级别启用。 该警告的文档包含该警告的默认级别。

- **#pragma warning(** *warning_level* **:** *warning_number* **)**

   指定的警告 (*warning_number*) 在指定级别启用 (*warning_level*)。

- [/Wall](../build/reference/compiler-option-warning-level.md)

   `/Wall` 将启用默认情况下禁用的所有警告。 如果使用此选项，您可以通过使用将关闭单个警告[/wd](../build/reference/compiler-option-warning-level.md)选项。

- [/w*Lnnnn*](../build/reference/compiler-option-warning-level.md)

   此选项将启用警告*nnnn*级别*L*。

## <a name="warnings-that-are-off-by-default"></a>默认情况下处于关闭状态的警告

在 Visual Studio 2015 及更高版本中默认情况下，下列警告被禁用:

|||
|-|-|
|[C4061](../error-messages/compiler-warnings/compiler-warning-level-4-c4061.md) （级别 4）|枚举器*标识符*的 switch 中的*枚举*没有被 case 标签显式处理|
|[C4062](../error-messages/compiler-warnings/compiler-warning-level-4-c4062.md) （级别 4）|枚举器*标识符*的 switch 中的*枚举*未处理|
| [C4165](../error-messages/compiler-warnings/compiler-warning-level-1-c4165.md) （级别 1） | HRESULT 正在转换为 bool;是否确定这是你想？ |
| [C4191](../error-messages/compiler-warnings/compiler-warning-level-3-c4191.md) （级别 3）|'*运算符*： 从不安全转换*type_of_expression*to*type_required*|
|[C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) （级别 4）|'*标识符*： 从转换*type1*to*type2*，可能丢失数据|
|[C4254](../error-messages/compiler-warnings/compiler-warning-level-4-c4254.md) （级别 4）|'*运算符*： 从转换*type1*to*type2*，可能丢失数据|
|[C4255](../error-messages/compiler-warnings/compiler-warning-level-4-c4255.md) （级别 4）|'*函数*： 未给出函数原型： 将转换为 (void)|
|[C4263](../error-messages/compiler-warnings/compiler-warning-level-4-c4263.md) （级别 4）|'*函数*： 成员函数不重写任何基类虚拟成员函数|
|[C4264](../error-messages/compiler-warnings/compiler-warning-level-1-c4264.md) （级别 1）|'*virtual_function*： 不重写虚拟成员函数从基本的'*类*; 函数被隐藏|
|[C4265](../error-messages/compiler-warnings/compiler-warning-level-3-c4265.md) （级别 3）|'*类*： 类有虚函数，但析构函数不是虚拟|
|[C4266](../error-messages/compiler-warnings/compiler-warning-level-4-c4266.md) （级别 4）|'*函数*： 不重写虚拟成员函数从基本的'*类型*; 函数被隐藏|
|[C4287](../error-messages/compiler-warnings/compiler-warning-level-3-c4287.md) （级别 3）|'*operator*': unsigned/negative constant mismatch|
|[C4289](../error-messages/compiler-warnings/compiler-warning-level-4-c4289.md) （级别 4）|使用了非标准扩展:*var*： 在 for 循环中声明的循环控制变量用在 for 循环范围外|
|[C4296](../error-messages/compiler-warnings/compiler-warning-level-4-c4296.md) （级别 4）|'*运算符*： 表达式始终为 false|
|[C4339](../error-messages/compiler-warnings/compiler-warning-level-4-c4339.md) （级别 4）|'*类型*： 未定义的类型检测到使用了在 CLR 元数据-使用此类型可能导致运行时异常|
|[C4342](../error-messages/compiler-warnings/compiler-warning-level-1-c4342.md) （级别 1）|行为更改: '*函数*调用，但在以前的版本中，称为成员运算符|
|[C4350](../error-messages/compiler-warnings/compiler-warning-level-1-c4350.md) （级别 1）|行为更改: '*member1*而不是名为*member2*|
|[C4355](../error-messages/compiler-warnings/compiler-warning-c4355.md)|“this”: 用于基成员初始值设定项列表|
|[C4365](../error-messages/compiler-warnings/compiler-warning-level-4-c4365.md) （级别 4）|'*操作*： 从转换*type_1*to*type_2*，有符号/无符号不匹配|
|C4370 （级别 3）|为了更好地封装，类的布局与早期版本的编译器已有所不同|
|[C4371](../error-messages/compiler-warnings/c4371.md) （级别 3）|'*classname*： 类的布局可能已更改从以前版本的编译器更好地封装成员*成员*|
|C4388 （级别 4）|有符号/无符号不匹配|
|[C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md) （级别 2）|'*函数*： 函数签名包含类型*类型*';C++对象是不安全纯代码之间传递与混合或本机|
|C4426 （级别 1）|优化标志发生更改后包括标头，可能是由于 #pragma optimize （） 超出<sup>14.1</sup>|
|[C4435](../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md) （级别 4）|'*class1*:/ Vd2 下的对象布局将因虚拟基而更改*class2*|
|[C4437](../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md) （级别 4）|从虚拟基的 dynamic_cast '*class1*到*class2*在某些上下文中可能会失败|
|C4444 （级别 3）|顶级“__unaligned”没有在该上下文中实现|
|[C4464](../error-messages/compiler-warnings/c4464.md) （级别 4）|相对包含路径包含..|
|[C4471](../error-messages/compiler-warnings/compiler-warning-level-4-c4471.md) （级别 4）|无范围枚举的前向声明必须有基础类型 (假定为 int)<sup>为永久</sup>|
|C4472 （级别 1）|'*标识符*是本机枚举： 添加访问说明符 (private/public) 以声明托管的枚举|
|[C4514](../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md) （级别 4）|'*函数*： 未引用的内联函数已移除|
|[C4536](../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md) （级别 4）|type name： 类型名超出了元数据限制*限制*字符|
|[C4545](../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md) （级别 1）|逗号前的表达式计算为缺少自变量列表的函数|
|[C4546](../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md) （级别 1）|逗号前的函数调用缺少自变量列表|
|[C4547](../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md) （级别 1）|'*运算符*： 运算符之前逗号不起任何作用; 应输入带副作用的运算符|
|[C4548](../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md) （级别 1）|逗号前的表达式不起任何作用；应输入带副作用的表达式|
|[C4549](../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md) （级别 1）|'*operator1*： 逗号前的运算符不起作用; 是否打算'*operator2*？|
|[C4555](../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md) （级别 1）|表达式无效；应输入带副作用的表达式|
|[C4557](../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md) （级别 3）|__assume 包含效果*效果*|
|[C4571](../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md) （级别 4）|信息性： 自 Visual 更改自语义C++7.1;不再捕获结构化的异常 (SEH)|
|C4574 （级别 4）|'*标识符*定义为"0： 您是否希望使用 #if*标识符*？|
|C4577 （级别 1）|noexcept 与任何异常处理模式，以指定; 一起使用不能保证在异常终止。 指定 /EHsc|
|C4582 （级别 4）|'*类型*： 构造函数未隐式调用|
|C4583 （级别 4）|'*类型*： 析构函数未隐式调用|
|C4587 （级别 1）|'*anonymous_structure*： 行为更改： 不再隐式调用构造函数|
|C4588 （级别 1）|'*anonymous_structure*： 行为更改： 不再隐式调用析构函数|
|C4596 （级别 4）|'*标识符*： 成员声明中的非法限定的名<sup>14.3</sup> <sup>为永久</sup>|
|C4598 （级别 1 和等级 3）|#include"*标头*"： 标头数*数量*预编译标头中不匹配该位置处的当前编译<sup>14.3</sup>|
|C4599 （级别 3）|'*选项* *路径*： 命令行参数号*数*与预编译标头不匹配<sup>14.3</sup>|
|C4605 （级别 1）|/D*宏*当前的命令行上指定但未指定生成预编译标头时|
|[C4608](../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md) （级别 3）|'*union_member*已初始化的另一个联合成员初始值设定项列表中，'*union_member*<sup>为永久</sup>|
|[C4619](../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md) （级别 3）|#pragma 警告： 无警告编号*数*|
|[C4623](../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md) （级别 4）|“derived class”: 未能生成默认构造函数，因为基类默认构造函数不可访问|
|[C4625](../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md) （级别 4）|“derived class”: 未能生成复制构造函数，因为基类复制构造函数不可访问|
|[C4626](../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md) （级别 4）|“derived class”: 未能生成赋值运算符，因为基类赋值运算符不可访问|
|[C4628](../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md) （级别 1）|-Ze 不支持二合字母。 字符序列*有向图时会*未解释的替换标记为*char*|
|[C4640](../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md) （级别 3）|'*实例*： 本地静态对象的结构不是线程安全|
| C4643 （级别 4） | 向前声明 '*标识符*不允许 std 命名空间中C++标准。 <sup>15.8</sup> |
|C4647 （级别 3）|行为更改： __is_pod (*类型*) 在早期版本中具有不同的值|
|C4654 （级别 4）|代码放在包含的预编译标头行中将被忽略。 将代码添加到预编译标头。 <sup>14.1</sup>|
|[C4668](../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md) （级别 4）|'*符号*未定义为预处理器宏，用"0"替换为中'*指令*|
|[C4682](../error-messages/compiler-warnings/compiler-warning-level-4-c4682.md) （级别 4）|'*符号*： 指定，默认为 [in] 未方向参数特性|
|[C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md) （级别 3）|'*用户定义类型*： 行为可能有更改，UDT 中的更改返回调用约定|
|[C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) （级别 1）|'*函数*： 非私有成员的签名包含程序集私有本机类型*native_type*|
|[C4710](../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md) （级别 4）|'*函数*： 函数未内联|
|[C4738](../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md) （级别 3）|将 32 位浮点型结果存储在内存中，可能会降低性能|
|[C4746](../error-messages/compiler-warnings/compiler-warning-c4746.md)|可变访问*表达式*' 受 /volatile:\<iso&#124;ms > 设置; 请考虑使用 __iso_volatile_load/store 内部函数|
|C4749 （级别 4）|有条件地支持： offsetof 应用于非布局类型*类型*|
|C4767 （级别 4）|节名称*符号*的长度超过 8 个字符并将由链接器截断|
|C4768 （级别 3）|已忽略链接规范前的 __declspec 特性|
|C4774 （级别 4）|'*字符串*： 格式字符串参数中的预期*数*不是字符串文字|
|C4777 （级别 4）|'*函数*： 格式字符串*字符串*要求类型的自变量*type1*，但可变参数参数*数*具有类型*type2*|
|C4786 （级别 3）|'*符号*： 对象名被截断为*数*中的调试信息的字符|
| [C4800](../error-messages/compiler-warnings/compiler-warning-level-3-c4800.md) （级别 4） | 从隐式转换*类型*为布尔值。 可能会丢失信息<sup>16.0</sup> |
|[C4820](../error-messages/compiler-warnings/compiler-warning-level-4-c4820.md) （级别 4）|'*字节*字节填充添加在构造之后*member_name*|
| [C4822](../error-messages/compiler-warnings/compiler-warning-level-1-c4822.md) （级别 1） | '*成员*： 局部类成员函数没有正文 |
|C4826 （级别 2）|从转换*type1*到*type2*将进行符号扩展。 这可能会导致意外的运行时行为。|
|C4837 （级别 4）|检测到三元祖:??*字符*替换为*字符*|
|C4841 （级别 4）|使用非标准扩展： offsetof 中使用的复合成员指示符|
|C4842 （级别 4）|offsetof 应用于使用多重继承的类型的结果不能保证编译器版本之间保持一致|
|[C4868](../error-messages/compiler-warnings/compiler-warning-c4868.md) （级别 4）|'_文件_(*line_number*) 编译器不会强制在括号内的初始化列表中的从左到右计算顺序|
|[C4905](../error-messages/compiler-warnings/compiler-warning-level-1-c4905.md) （级别 1）|宽字符串强制转换为“LPSTR”|
|[C4906](../error-messages/compiler-warnings/compiler-warning-level-1-c4906.md) （级别 1）|字符串强制转换为“LPWSTR”|
|[C4917](../error-messages/compiler-warnings/compiler-warning-level-1-c4917.md) （级别 1）|'*声明符*: GUID 只能与类、 接口或命名空间相关联|
|[C4928](../error-messages/compiler-warnings/compiler-warning-level-1-c4928.md) （级别 1）|副本初始化非法；隐式应用了多个用户定义的转换|
|[C4931](../error-messages/compiler-warnings/compiler-warning-level-4-c4931.md) （级别 4）|我们假定类型库是为 number 位指针生成的|
|[C4946](../error-messages/compiler-warnings/compiler-warning-level-1-c4946.md) （级别 1）|reinterpret_cast 在相关类之间使用:*class1*和*class2*|
|C4962|'*函数*： 已禁用在于优化导致了配置文件数据变得不一致的按配置优化|
|[C4986](../error-messages/compiler-warnings/compiler-warning-c4986.md) （级别 4）|'*符号*： 异常规范与前面的声明不匹配|
|C4987 （级别 4）|使用了非标准扩展：“throw (...)”|
|C4988 （级别 4）|'*符号*： 类/函数范围外声明了变量|
|C5022|'*类型*： 指定了多个移动构造函数|
|C5023|'*类型*： 指定的多个移动赋值运算符|
|C5024 （级别 4）|'*类型*： 移动构造函数被隐式定义为已删除|
|C5025 （级别 4）|'*类型*： 移动赋值运算符已隐式定义为已删除|
|C5026 （级别 1 和级别 4）|'*类型*： 移动构造函数被隐式定义为已删除|
|C5027 （级别 1 和级别 4）|'*类型*： 移动赋值运算符已隐式定义为已删除|
|C5029 （级别 4）|使用了非标准扩展： 对齐方式中的属性C++适用于变量、 数据成员和仅标记类型|
|C5031 （第 4 层）|#pragma warning （pop): 可能不匹配，弹出推入不同文件的警告状态<sup>14.1</sup>|
|C5032 （级别 4）|检测到 #pragma warning (push) 测试 warning （没有相应 #pragma pop) <sup>14.1</sup>|
|C5034|使用的内部函数*内部函数*将导致函数*函数*编译为来宾代码<sup>15.3</sup>|
|C5035|使用功能*功能*将导致函数*函数*编译为来宾代码<sup>15.3</sup>|
|C5036 （级别 1）|将/hybrid:x86arm64 编译时的 varargs 函数指针转换*type1*到*type2* <sup>15.3</sup>|
|[C5038](../error-messages/compiler-warnings/c5038.md) （级别 4）|数据成员*member1*将之后被初始化数据成员*member2* <sup>15.3</sup>|
|C5039 （级别 4）|'*函数*： 指针或引用可能引发函数传递到-EHc 下 extern C 函数。 如果此函数将引发异常，则可能会出现未定义的行为。 <sup>15.5</sup>|
|C5042 （级别 3）|'*函数*： 在块范围内的函数声明不能为标准中的指定内联C++; 中删除内联说明符<sup>15.5</sup>|
|[C5045](../error-messages/compiler-warnings/c5045.md)|如果指定 /Qspectre 开关，编译器将插入内存负载的 Spectre 缓解<sup>15.7</sup>|

<sup>第 14.1</sup>此警告是从 Visual Studio 2015 Update 1 开始，提供。<br/>
<sup>14.3</sup>此警告是从 Visual Studio 2015 Update 3 开始，提供。<br/>
<sup>15.3</sup>此警告是从 Visual Studio 2017 版本 15.3 开始，提供。<br/>
<sup>15.5</sup>此警告是从 Visual Studio 2017 版本 15.5 开始，提供。<br/>
<sup>15.7</sup>此警告是从 Visual Studio 2017 版本 15.7 中开始提供。<br/>
<sup>15.8</sup>此警告是在 Visual Studio 2017 版本 15.8 从开始提供。<br/>
::: moniker range=">= vs-2019"
<sup>16.0</sup>此警告是从开始在 Visual Studio 2019 RTM 中提供。<br/>
::: moniker-end
<sup>为永久</sup>此警告处于关闭状态，除非[触发-](../build/reference/permissive-standards-conformance.md)设置编译器选项。

## <a name="warnings-off-by-default-in-earlier-versions"></a>在早期版本中默认情况下关闭的警告

这些警告偏了 Visual Studio 2015 之前，编译器的版本中默认情况下：

|||
|-|-|
|[C4302](../error-messages/compiler-warnings/compiler-warning-level-2-c4302.md) （级别 2）|'*转换*： 从截断*type1*to*type2*|
|[C4311](../error-messages/compiler-warnings/compiler-warning-level-1-c4311.md) （级别 1）|'*变量*： 从指针截断*类型*to*类型*|
|[C4312](../error-messages/compiler-warnings/compiler-warning-level-1-c4312.md) （级别 1）|'*操作*： 从转换*type1*to*type2*更大的|
|[C4319](../error-messages/compiler-warnings/compiler-warning-level-1-c4319.md) （级别 1）|'*运算符*： 零扩展*type1*to*type2*更大的|

此警告已关闭 Visual Studio 2012 之前，编译器的版本中默认情况下：

|||
|-|-|
|[C4431](../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md) （级别 4）|缺少类型说明符 - 假定为 int。 注意:C 不再支持默认 int|

## <a name="see-also"></a>请参阅

[warning](../preprocessor/warning.md)