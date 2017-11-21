---
title: "编译器警告 C4800 通过 C5999 |Microsoft 文档"
ms.date: 10/25/2017
ms.technology: cpp-tools
ms.topic: error-reference
f1_keywords:
- C4806
- C4807
- C4808
- C4809
- C4810
- C4811
- C4812
- C4813
- C4816
- C4817
- C4822
- C4825
- C4827
- C4837
- C4840
- C4841
- C4842
- C4872
- C4880
- C4881
- C4882
- C4900
- C4910
- C4912
- C4913
- C4916
- C4918
- C4920
- C4921
- C4925
- C4926
- C4932
- C4934
- C4935
- C4936
- C4937
- C4938
- C4939
- C4944
- C4947
- C4950
- C4951
- C4952
- C4953
- C4954
- C4955
- C4956
- C4957
- C4958
- C4959
- C4960
- C4961
- C4962
- C4963
- C4966
- C4970
- C4971
- C4972
- C4973
- C4974
- C4981
- C4985
- C4987
- C4988
- C4989
- C4990
- C4991
- C4992
- C4997
- C4998
- C4999
- C5022
- C5023
- C5024
- C5025
- C5026
- C5027
- C5028
- C5029
- C5030
- C5031
- C5032
- C5033
- C5034
- C5035
- C5036
- C5037
- C5038
dev_langs: C++
ms.assetid: c3182430-8b3b-4ab2-a532-5cd436707dc8
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1bf919fbb1959af6fad031a7f32262466f6f49ff
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/11/2017
---
# <a name="compiler-warnings-c4800-through-c5999"></a>编译器警告 C4800 通过 C5999

文档的此部分中的文章包含有关子集的 Visual c + + 编译器警告的信息。 你可以访问此处的信息，或在 Visual Studio 中的输出窗口中，您可以选择错误号，然后按 F1 键。

> [!NOTE]
> 不是每个[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]错误或警告记录在 MSDN 中。 在许多情况下，诊断消息将提供的所有可用信息。 如果你认为某个错误消息需要更多说明，请通知我们。 你可以在此页上，使用反馈表单或转到 Visual Studio 中的菜单栏，然后选择**帮助**，**报告 Bug**，或可以在提交建议或 bug 报表[Microsoft Connect](http://connect.microsoft.com/VisualStudio).

错误和警告的 MSDN 公共论坛，可能会发现更多帮助。 [Visual c + + 语言](http://go.microsoft.com/fwlink/?LinkId=158195)论坛是有关问题和讨论有关[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]语言语法和编译器。 [Visual c + + 常规](http://go.microsoft.com/fwlink/?LinkId=158194)论坛的问题是有关[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]其他论坛中未涉及。 你还可能上查找有关错误和警告的帮助[堆栈溢出](http://stackoverflow.com/)。

## <a name="in-this-section"></a>本节内容

|警告|消息|
|-------------|-------------|
|[编译器警告（等级 3）C4800](compiler-warning-level-3-c4800.md)|type: bool 'true' 或 'false' （性能警告） 到强制值|
|[编译器警告（等级 1）C4803](compiler-warning-level-1-c4803.md)|method： 引发方法具有不同的存储类，该事件，从 event|
|[编译器警告（等级 1）C4804](compiler-warning-level-1-c4804.md)|operation： 类型为 bool 操作中的不安全地使用|
|[编译器警告（等级 1）C4805](compiler-warning-level-1-c4805.md)|operation： 类型 type 混合不安全和类型 type 中操作|
|编译器警告 （等级 1） C4806|operation： 不安全的操作： 类型 type 提升到类型 type 没有值可以为给定的常量|
|编译器警告 （等级 1） C4807|operation： 类型 type 和类型 type 的有符号的位域的混合不安全|
|编译器警告 （等级 1） C4808|用例 'value' 不是类型的有效的值的切换条件为 bool|
|编译器警告 （等级 1） C4809|switch 语句有多余的 default 标签;提供所有可能的 case 标签|
|编译器警告 （等级 1） C4810|杂注 pack(show) 的值 == n|
|编译器警告 （等级 1） C4811|杂注 conform(forScope, show) 的值 == value|
|编译器警告 （等级 1） C4812|过时的声明样式：请改用“new_syntax”|
|编译器警告 （等级 1） C4813|function： 局部类的友元函数必须之前被声称|
|编译器警告 （等级 4） C4816|param： 参数具有一个零大小的数组，它将被截断 （除非通过引用传递的对象）|
|编译器警告 （等级 1） C4817|member： 非法使用。 ' 若要访问该成员;编译器替换为->|
|[编译器警告（等级 1）C4819](compiler-warning-level-1-c4819.md)|该文件包含不能在当前代码页（数字）中表示的字符。 保存该文件以 Unicode 格式，以防止数据丢失|
|[编译器警告（等级 4）C4820](compiler-warning-level-4-c4820.md)|“bytes”字节填充添加在构造“member_name”之后|
|[编译器警告（等级 1）C4821](compiler-warning-level-1-c4821.md)|无法确定 Unicode 编码类型，请保存签名 (清单 BOM) 文件|
|编译器警告 （等级 1） C4822|member function： 局部类成员函数没有正文|
|[编译器警告（等级 3）C4823](compiler-warning-level-3-c4823.md)|function： 使用钉住指针但展开语义不会启用。 请考虑使用 /EHa|
|编译器警告 （等级 2） C4826|从*type1*到*type2*进行符号扩展。 这可能导致意外的运行时行为。|
|编译器警告 （等级 3） C4827|具有 0 参数的公共 ToString 方法应标记为虚拟和重写|
|[编译器警告（等级 1）C4829](compiler-warning-level-1-c4829.md)|函数 main 的参数可能不正确。 请考虑 int main (platform:: array\<platform:: string ^ > ^ argv)|
|[编译器警告（等级 1）C4835](compiler-warning-level-1-c4835.md)|variable： 在宿主程序集首次执行托管的代码之前，不会运行导出的数据的初始值设定项|
|编译器警告 （等级 4） C4837|检测到的三元组:??*字符*替换为*字符*|
|[编译器警告（等级 1）C4838](compiler-warning-level-1-c4838.md)|从 type_1 类型到 type_2 转换需要收缩转换|
|[编译器警告 （等级 3） C4839](compiler-warning-level-3-c4839.md)|类的非标准使用*类型*作为可变参数函数的自变量|
|编译器警告 （等级 4） C4840|类的非可移植使用*类型*作为可变参数函数的自变量|
|编译器警告 （等级 4） C4841|使用的非标准扩展： offsetof 中使用的复合成员指示符|
|编译器警告 （等级 4） C4842|offsetof 应用于使用多重继承的类型的结果不是保证是编译器版本之间一致|
|[编译器警告 （错误） C4867](compiler-warning-c4867.md)|function： 函数调用缺少自变量列表;使用调用创建指向成员的指针|
|[编译器警告 （等级 4） C4868](compiler-warning-c4868.md)|_文件_(*line_number*) 编译器可能会不强制实施在大括号内的初始化列表中从左到右计算顺序|
|编译器警告 （等级 2） C4872|浮点编译在 concurrency:: parallel_for_each 的调用关系图时检测到的零除以:*位置*|
|编译器警告 （等级 1） C4880|从 const type_1 类型到 type_2 执行强制转换： 转换掉 constness 从指针或引用可能会导致未定义的行为，在 amp 限制函数|
|编译器警告 （等级 4） C4881|构造函数和/或析构函数将不会调用 tile_static 变量 variable|
|编译器警告 （等级 1） C4882|将使用非 const 调用运算符函子传递给 concurrency:: parallel_for_each 已弃用|
|编译器警告 C4900|Tool1 版本 version1 和 tool2 版本 version2 之间的 Il 不匹配|
|[编译器警告（等级 1）C4905](compiler-warning-level-1-c4905.md)|宽字符串强制转换为“LPSTR”|
|[编译器警告（等级 1）C4906](compiler-warning-level-1-c4906.md)|字符串强制转换为“LPWSTR”|
|编译器警告 （等级 1） C4910|\<标识符 >: __declspec （dllexport） 和 extern 不兼容的显式实例化上|
|编译器警告 （等级 1） C4912|“attribute”：在嵌套 UDT 上，特性有未定义的行为|
|编译器警告 （等级 4） C4913|存在用户定义的二进制运算符“,”，但没有重载可以转换所有操作数，使用了默认的内置二进制运算符“,”|
|编译器警告 （等级 1） C4916|为了具有 dispid*说明*： 必须引入由接口|
|[编译器警告（等级 1）C4917](compiler-warning-level-1-c4917.md)|declarator: GUID 只能与类、 接口或命名空间关联|
|编译器警告 （等级 4） C4918|character： 杂注优化列表中的无效字符|
|编译器警告 （等级 1） C4920|枚举枚举成员 member_1 = value_1 已在 enum enum 中视为 member_2 = value_2|
|编译器警告 （等级 3） C4921|*说明*： 属性值*属性*不应累积指定|
|编译器警告 （等级 1） C4925|“method”：不能从脚本调用调度接口方法|
|编译器警告 （等级 1） C4926|“identifier”：已定义符号：忽略特性|
|[编译器警告（等级 1）C4927](compiler-warning-level-1-c4927.md)|非法转换则隐式应用了多个用户定义的转换|
|[编译器警告（等级 1）C4928](compiler-warning-level-1-c4928.md)|副本初始化非法；隐式应用了多个用户定义的转换|
|[编译器警告（等级 1）C4929](compiler-warning-level-1-c4929.md)|file： 类型库包含联合;忽略 embedded_idl 限定符|
|[编译器警告（等级 1）C4930](compiler-warning-level-1-c4930.md)|原型： 未调用原型函数 （是有意用变量定义？）|
|[编译器警告（等级 4）C4931](compiler-warning-level-4-c4931.md)|我们假定类型库是为 number 位指针生成的|
|编译器警告 （等级 4） C4932|__identifier (*标识符*) 和\__identifier (*标识符*) 时不可区分|
|编译器警告 （等级 1） C4934|__delegate(multicast) 已弃用，请使用\__delegate 改为|
|编译器警告 （等级 1） C4935|程序集访问说明符已从“access”修改|
|编译器警告 （等级 1，错误） C4936|只有使用 /clr 或 /clr:pure 编译时，才支持此 __declspec|
|编译器警告 （等级 4） C4937|“text1”和“text2”作为“directive”的参数时不可区分|
|编译器警告 （等级 4） C4938|var： 浮点型 reduction 变量可能会导致不一致的结果在 /fp: strict 或 #pragma fenv_access|
|编译器警告 C4939|#pragma vtordisp 已被否决，并将在 Visual C++ 将来的版本移除|
|编译器警告 （等级 1） C4944|symbol： 无法导入从 assembly1 的符号： 因为内当前作用域已存在 symbol|
|[编译器警告（等级 1）C4945](compiler-warning-level-1-c4945.md)|symbol： 无法导入符号从 assembly1： 如 symbol 具有已导入从另一个程序集 assembly2|
|[编译器警告（等级 1）C4946](compiler-warning-level-1-c4946.md)|reinterpret_cast 在相关类之间使用:“class1”和“class2”|
|编译器警告 （等级 1） C4947|type_or_member： 标记为过时|
|[编译器警告（等级 2）C4948](compiler-warning-level-2-c4948.md)|accessor 的返回类型与相应的 setter 的最后一个参数类型不匹配|
|[编译器警告（等级 1 和等级 4）C4949](compiler-warning-level-1-and-level-4-c4949.md)|托管和非托管杂注为仅在使用编译时，才有意义 / clr [: 选项]|
|编译器警告 （等级 1，错误） C4950|type_or_member： 标记为过时|
|编译器警告 （等级 1） C4951|收集配置文件数据后已编辑过“函数”，没有使用函数配置文件数据|
|编译器警告 （等级 1） C4952|function： 在程序数据库 pgd_file 中找到任何配置文件数据|
|编译器警告 （等级 1） C4953|在收集配置文件数据后已编辑过内联“function”，没有使用配置文件数据|
|编译器警告 C4954|function： 不会分析 （包含 __int64 switch 表达式）|
|编译器警告 C4955|import2： 忽略; 的导入已从 import1 导入|
|编译器警告 （等级 1，错误） C4956|type： 此类型不是可验证|
|编译器警告 （等级 1，错误） C4957|cast： 从 'cast 从' 到 cast_to 的显式强制转换是不可验证|
|编译器警告 （等级 1，错误） C4958|operation： 指针算法是不可验证|
|编译器警告 （等级 1，错误） C4959|无法因为访问其成员会产生不可验证的代码在 /clr: safe 中定义非托管的类型 type|
|编译器警告 （等级 4） C4960|“function”太大，无法配置|
|编译器警告 （等级 1） C4961|没有将任何配置文件数据合并到“.pgd file”，因此已禁用按配置文件优化|
|编译器警告 （等级 4） C4962|function： 已禁用在于优化导致了配置文件数据变得不一致的按配置文件优化|
|编译器警告 （等级 1） C4963|*说明*： 找到任何配置文件数据; 检测的生成中使用不同的编译器选项|
|[编译器警告（等级 1）C4964](compiler-warning-level-1-c4964.md)|未不指定任何优化选项;将不会收集配置文件信息|
|[编译器警告（等级 1）C4965](compiler-warning-level-1-c4965.md)|隐式框中的整数 0;使用 nullptr 或显式强制转换|
|编译器警告 （等级 1） C4966|*函数*具有不受支持的段名称，忽略的批注与 __code_seg 批注|
|编译器警告 C4970|委托构造函数： 目标对象忽略自*类型*是静态的|
|编译器警告 （等级 1） C4971|参数顺序：\<目标对象 >，\<目标函数 > 委托构造函数已弃用，对于使用\<目标函数 >，\<目标对象 ="">|
|编译器警告 （等级 1，错误） C4972|直接修改取消装箱操作的结果或将其视为左值是不可验证的|
|编译器警告 （等级 1） C4973|*符号*： 标记为已弃用|
|编译器警告 （等级 1） C4974|*符号*： 标记为已弃用|
|编译器警告 （等级 3） C4981|Warbird： 函数*函数*标记为 __forceinline 不内联因为它包含异常语义|
|编译器警告 （等级 3） C4985|符号名： 先前声明中不存在特性。|
|[编译器警告 C4986](compiler-warning-c4986.md)|*声明*： 异常规范与前面的声明不匹配|
|编译器警告 （等级 4） C4987|使用了非标准扩展：“throw (...)”|
|编译器警告 （等级 4） C4988|*变量*： 声明外部类/函数范围变量|
|编译器警告 （等级 4） C4989|*类型*： 类型具有冲突定义。|
|编译器警告 （等级 3） C4990|Warbird:*消息*|
|编译器警告 （等级 3） C4991|Warbird： 函数*函数*标记为 __forceinline 不内联因为被内联方的保护级别大于父级|
|编译器警告 （等级 3） C4992|Warbird： 函数*函数*标记为 __forceinline 不内联因为它包含内联程序集不能受保护的|
|[编译器警告（等级 3）C4995](compiler-warning-level-3-c4995.md)|function： 名称被标记为弃用 #pragma|
|[编译器警告（等级 3）C4996](compiler-warning-level-3-c4996.md)|*说明*:*消息*|
|编译器警告 （等级 1） C4997|“class”：组件类不实现 COM 接口或伪接口|
|编译器警告 （等级 1） C4998|预期失败：*假定条件下*(*值*)|
|编译器警告 C4999|请未知警告选择技术支持命令的 Visual c + + 帮助菜单上，或打开技术支持帮助文件了解详细信息|
|编译器警告 C5022|*类型*： 指定了多个移动构造函数|
|编译器警告 C5023|*类型*： 指定的多个移动赋值运算符|
|编译器警告 （等级 4） C5024|*类型*： 移动构造函数隐式定义，为已删除|
|编译器警告 （等级 4） C5025|*类型*： 移动赋值运算符已隐式定义为已删除|
|编译器警告 （等级 1 和等级 4） C5026|*类型*： 移动构造函数隐式定义，为已删除|
|编译器警告 （等级 1 和等级 4） C5027|*类型*： 移动赋值运算符已隐式定义为已删除|
|编译器警告 （等级 1） C5028|*名称*： 先前声明中指定的对齐方式 (*数*) 定义中未指定|
|编译器警告 （等级 4） C5029|使用的非标准扩展： c + + 中的对齐方式属性应用于变量、 数据成员和仅适用于标记类型|
|编译器警告 （等级 3） C5030|属性*属性*无法识别|
|编译器警告 （等级 4） C5031|#pragma warning （pop): 可能不匹配，弹出推入不同的文件的警告状态|
|编译器警告 （等级 4） C5032|检测到与测试 warning （没有相应 #pragma pop） #pragma warning （push）|
|编译器警告 （等级 1） C5033|*存储类*不再受支持的存储类|
|编译器警告 C5034|使用内部函数的*内部*将导致函数*函数*编译为访客代码|
|编译器警告 C5035|使用的功能*功能*将导致函数*函数*编译为访客代码|
|编译器警告 （等级 1） C5036|varargs 函数指针转换使用 /hybrid:x86arm64 编译时*type1*到*type2*|
|编译器警告 （错误） C5037|*成员函数*： 类模板的成员的超行定义不能具有默认自变量|
