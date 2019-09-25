---
title: 编译器警告 C4800 - C5999
ms.date: 04/21/2019
f1_keywords:
- C4808
- C4809
- C4825
- C4827
- C4837
- C4841
- C4842
- C4843
- C4844
- C4845
- C4846
- C4847
- C4848
- C4872
- C4880
- C4881
- C4882
- C4910
- C4916
- C4921
- C4934
- C4951
- C4954
- C4955
- C4963
- C4966
- C4970
- C4971
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
- C4998
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
- C5039
- C5040
- C5041
- C5042
- C5043
- C5044
- C5047
- C5048
- C5049
- C5050
- C5100
- C5101
- C5102
- C5103
- C5104
- C5106
- C5107
helpviewer_keywords:
- C4808
- C4809
- C4825
- C4827
- C4837
- C4841
- C4842
- C4843
- C4844
- C4845
- C4846
- C4847
- C4848
- C4872
- C4880
- C4881
- C4882
- C4910
- C4916
- C4921
- C4934
- C4951
- C4954
- C4955
- C4963
- C4966
- C4970
- C4971
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
- C4998
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
- C5039
- C5040
- C5041
- C5042
- C5043
- C5044
- C5047
- C5048
- C5049
- C5050
- C5100
- C5101
- C5102
- C5103
- C5104
- C5106
- C5107
ms.openlocfilehash: 7e715dcbac9dc59fe09ee1f917c02a23b3c4db14
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230477"
---
# <a name="compiler-warnings-c4800-through-c5999"></a>编译器警告 C4800 - C5999

文档的本节中的文章介绍了编译器生成的一小部分警告消息。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>警告消息

|警告|消息|
|-------------|------------|
|[编译器警告（等级4） C4800](compiler-warning-level-3-c4800.md)| 从 "*type*" 到布尔值的隐式转换。 可能的信息丢失 |
|[编译器警告（等级1） C4803](compiler-warning-level-1-c4803.md)|"*method*"： raise 方法的存储类与事件 "*event*" 的存储类不同|
|[编译器警告（等级1） C4804](compiler-warning-level-1-c4804.md)|"*operation*"：在操作中使用类型 "bool" 不安全|
|[编译器警告（等级1） C4805](compiler-warning-level-1-c4805.md)|"*operation*"：在操作中类型 "*type1*" 和类型 "*type2*" 的混合不安全|
|[编译器警告（等级1） C4806](compiler-warning-level-1-c4806.md)|"*operation*"：不安全的操作：不能将类型 "*type1*" 的值提升为类型 "*type2*"，不能等于给定的常量|
|[编译器警告（等级1） C4807](compiler-warning-level-1-c4807.md)|"*operation*"：类型 "*type1*" 和 "*type2*" 类型的带符号位域的混合不安全|
|编译器警告（等级1） C4808|case "*value*" 不是类型 "bool" 的切换条件的有效值|
|编译器警告（等级1） C4809|switch 语句有多余的 "default" 标签;给定所有可能的 "case" 标签|
|[编译器警告（等级1） C4810](compiler-warning-level-1-c4810.md)|杂注 pack(show) 的值 == n|
|[编译器警告（等级1） C4811](compiler-warning-level-1-c4811.md)|杂注 conform(forScope, show) 的值 == value|
|[编译器警告（等级1） C4812](compiler-warning-level-1-c4812.md)|过时的声明样式：请改用 "*new_syntax*"|
|[编译器警告（等级1） C4813](compiler-warning-level-1-c4813.md)|"*function*"：局部类的友元函数以前必须已经声明|
|[编译器警告（等级4） C4816](compiler-warning-level-4-c4816.md)|"*param*"：参数具有一个零大小的数组，该数组将被截断（除非该对象通过引用传递）|
|[编译器警告（等级1） C4817](compiler-warning-level-1-c4817.md)|"*member*"：非法使用 "." 访问此成员;编译器替换为 "->"|
|[编译器警告（等级1） C4819](compiler-warning-level-1-c4819.md)|该文件包含不能在当前代码页（数字）中表示的字符。 以 Unicode 格式保存该文件以防止数据丢失|
|[编译器警告（等级4） C4820](compiler-warning-level-4-c4820.md)|在构造 "*member_name*" 之后添加了 "*bytes*" 字节填充|
|[编译器警告（等级1） C4821](compiler-warning-level-1-c4821.md)|无法确定 Unicode 编码类型，请用签名（BOM）保存文件|
|[编译器警告（等级1） C4822](compiler-warning-level-1-c4822.md)|"成员函数"：局部类成员函数没有主体|
|[编译器警告（等级3） C4823](compiler-warning-level-3-c4823.md)|"*function*"：使用钉住指针，但未启用展开语义。 考虑使用/EHa|
|编译器警告（等级2） C4826|从 "*type1*" 到 "*type2*" 的转换是带符号扩展的。 这可能导致意外的运行时行为。|
|编译器警告（等级3） C4827|应将具有0个参数的公共 "ToString" 方法标记为虚拟和重写|
|[编译器警告（等级1） C4829](compiler-warning-level-1-c4829.md)|函数 main 的参数可能不正确。 请考虑 "int main （Platform：：\<Array Platform：： String ^ > ^ argv）"|
|[编译器警告（等级1） C4835](compiler-warning-level-1-c4835.md)|"*variable*"：在主机程序集中首次执行托管代码时，导出数据的初始值设定项将不会运行|
|编译器警告（等级4） C4837|检测到三元组： "？*字符*"替换为"*character*"|
|[编译器警告（等级1） C4838](compiler-warning-level-1-c4838.md)|从 "*type_1*" 到 "*type_2*" 的转换需要收缩转换|
|[编译器警告（等级3） C4839](compiler-warning-level-3-c4839.md)|类 "*type*" 作为可变参数函数的参数的非标准用法|
|[编译器警告（等级4） C4840](compiler-warning-level-4-c4840.md)|类 "*type*" 作为可变参数函数的参数的不可移植使用|
|编译器警告（等级4） C4841|使用的非标准扩展： offsetof 中使用的复合成员指示符|
|编译器警告（等级4） C4842|使用多重继承应用到类型的 "offsetof" 结果不保证在编译器版本之间保持一致|
|编译器警告 C4843|"*type1*"：对数组或函数类型的引用的异常处理程序不可访问，请改用 "*type2*"|
|编译器警告 C4844|"export module *module_name*;" 现在是用于声明模块接口的首选语法|
| 编译器警告（等级4） C4845 | 如果\_未在命令\_行\_上指定 "/d1initall\[0\_\|1\|23]"，则将忽略"declspec（无初始化全部）"\| |
| 编译器警告（等级4） C4846 | "*value*" 不是 "/d1initall" 的有效参数：忽略了命令行标志 |
| 编译器警告（等级4） C4847 | "\_declspec\_（无\_初始化\_全部）" 只能应用于函数、类类型或局部变量：已忽略 |
| 编译器警告（等级1） C4848 | c + + 17 及更\_早\_版本中对标准特性 "无唯一地址" 的支持是一个供应商扩展 |
|[编译器警告（等级4） C4866](c4866.md)| 对于对*operator_name*的调用，编译器可能不强制执行从左到右的计算顺序|
|[编译器警告（错误） C4867](compiler-warning-c4867.md)|"*function*"：函数调用缺少参数列表;使用 "*call*" 创建指向成员的指针|
|[编译器警告（等级4） C4868](compiler-warning-c4868.md)|"_file_（*line_number*）" 编译器不能在大括号内初始化列表中强制执行从左到右的计算顺序|
|编译器警告（等级2） C4872|编译 arallel_for_each 的调用关系:p 图时，检测到浮点数被零除： "*location*"|
|编译器警告（等级1） C4880|从 "const *type_1*" 强制转换为 "*type_2*"：从指针或引用强制转换离开 constness 可能会导致 amp 限制函数中出现未定义的行为|
|编译器警告（等级4） C4881|不会为 tile_static 变量 "*variable*" 调用构造函数和/或析构函数|
|编译器警告（等级1） C4882|将函子与非常量调用运算符一起传递给并发：不推荐使用 arallel_for_each:p|
|[编译器警告 C4900](compiler-warning-level-1-c4900.md)|"*Tool1*" 版本 "*version1*" 和 "*tool2*" 版本 "*version2*" 之间的 Il 不匹配|
|[编译器警告（等级1） C4905](compiler-warning-level-1-c4905.md)|宽字符串强制转换为“LPSTR”|
|[编译器警告（等级1） C4906](compiler-warning-level-1-c4906.md)|字符串强制转换为“LPWSTR”|
|[编译器警告（等级1） C4910](compiler-warning-level-1-c4910.md)|"\<标识符 >：" __declspec （dllexport） "和" extern "在显式实例化上不兼容|
|[编译器警告（等级1） C4912](compiler-warning-level-1-c4912.md)|"*attribute*"：特性在嵌套 UDT 上具有未定义的行为|
|[编译器警告（等级4） C4913](compiler-warning-level-4-c4913.md)|存在用户定义的二进制运算符“,”，但没有重载可以转换所有操作数，使用了默认的内置二进制运算符“,”|
|编译器警告（等级1） C4916|为了使 dispid "*description*"：必须通过接口引入|
|[编译器警告（等级1） C4917](compiler-warning-level-1-c4917.md)|"*声明符*"： GUID 只能与类、接口或命名空间关联|
|[编译器警告（等级4） C4918](compiler-warning-level-4-c4918.md)|"*character*"：杂注优化列表中的无效字符|
|[编译器警告（等级1） C4920](compiler-warning-level-1-c4920.md)|enum enum member member_1 = value_1 在 enum enum 中被视为 member_2 = value_2|
|编译器警告（等级3） C4921|"*description*"：不应多次指定特性值 "*attribute*"|
|[编译器警告（等级1） C4925](compiler-warning-level-1-c4925.md)|"*method*"：不能从脚本调用调度接口方法|
|[编译器警告（等级1） C4926](compiler-warning-level-1-c4926.md)|"*identifier*"：已定义符号：忽略特性|
|[编译器警告（等级1） C4927](compiler-warning-level-1-c4927.md)|非法转换;已隐式应用了多个用户定义的转换|
|[编译器警告（等级1） C4928](compiler-warning-level-1-c4928.md)|副本初始化非法；隐式应用了多个用户定义的转换|
|[编译器警告（等级1） C4929](compiler-warning-level-1-c4929.md)|"*file*"：类型库包含联合;忽略 "embedded_idl" 限定符|
|[编译器警告（等级1） C4930](compiler-warning-level-1-c4930.md)|"*原型*"：未调用原型函数（是否是有意用变量定义的？）|
|[编译器警告（等级4） C4931](compiler-warning-level-4-c4931.md)|我们假定类型库是为 number 位指针生成的|
|[编译器警告（等级4） C4932](compiler-warning-level-4-c4932.md)|__identifier （*标识符*）和\__identifier （*标识符*）不可区分|
|编译器警告（等级1） C4934|"__delegate （多播）" 已弃用，请改用\_"_delegate"|
|[编译器警告（等级1） C4935](compiler-warning-level-1-c4935.md)|程序集访问说明符已从 "*access*" 修改|
|[编译器警告（等级1，错误） C4936](compiler-warning-c4936.md)|只有使用 /clr 或 /clr:pure 编译时，才支持此 __declspec|
|[编译器警告（等级4） C4937](compiler-warning-level-4-c4937.md)|"*text1*" 和 "*文本 2*" 作为 "*指令*" 的参数不可区分|
|[编译器警告（等级4） C4938](compiler-warning-level-4-c4938.md)|"*var*"：浮点缩减变量可能导致在/fp： strict 或 #pragma fenv_access 下出现不一致的结果|
|[编译器警告 C4939](compiler-warning-level-1-c4939.md)|#pragma vtordisp 已被否决，并将在 Visual C++ 将来的版本移除|
|[编译器警告（等级1） C4944](compiler-warning-level-1-c4944.md)|"*symbol*"：无法从 "*assembly1*" 导入符号：因为当前范围内已存在 "*symbol*"|
|[编译器警告（等级1） C4945](compiler-warning-level-1-c4945.md)|"*symbol*"：无法从 "*assembly1*" 导入符号：因为 "*symbol*" 已从另一个程序集 "*assembly2*" 导入|
|[编译器警告（等级1） C4946](compiler-warning-level-1-c4946.md)|reinterpret_cast 在相关类之间使用： "*class1*" 和 "*class2*"|
|[编译器警告（等级1） C4947](compiler-warning-level-1-c4947.md)|"*type_or_member*"：标记为过时|
|[编译器警告（等级2） C4948](compiler-warning-level-2-c4948.md)|"*访问器*" 的返回类型与相应的 setter 的最后一个参数类型不匹配|
|[编译器警告（等级1和等级4） C4949](compiler-warning-level-1-and-level-4-c4949.md)|仅当用 "/clr [： option]" 编译时，pragma "managed" 和 "非托管" 才有意义|
|[编译器警告（等级1，错误） C4950](compiler-warning-c4950.md)|"*type_or_member*"：标记为过时|
|[编译器警告（等级1） C4951](compiler-warning-level-1-c4951.md)|自收集配置文件数据后已编辑过 "*函数*"，未使用函数配置文件数据|
|[编译器警告（等级1） C4952](compiler-warning-level-1-c4952.md)|"*function*"：在程序数据库 "*pgd_file*" 中找不到配置文件数据|
|[编译器警告（等级1） C4953](compiler-warning-level-1-c4953.md)|自收集配置文件数据后已编辑被内联方 "*function*"，未使用配置文件数据|
|编译器警告 C4954|"*function*"：未配置（包含 __int64 switch 表达式）|
|编译器警告 C4955|"*import2*"：忽略导入;已从 "*import1*" 导入|
|[编译器警告（等级1，错误） C4956](compiler-warning-c4956.md)|"*type*"：此类型是不可验证的|
|[编译器警告（等级1，错误） C4957](compiler-warning-c4957.md)|"*cast*"：从 "*cast_from*" 到 "*cast_to*" 的显式强制转换是不可验证的|
|[编译器警告（等级1，错误） C4958](compiler-warning-c4958.md)|"*operation*"：指针算法是不可验证的|
|[编译器警告（等级1，错误） C4959](compiler-warning-c4959.md)|无法在/clr： safe 中定义非托管类型 "*type*"，因为访问其成员会产生不可验证的代码|
|[编译器警告（等级4） C4960](compiler-warning-level-4-c4960.md)|"*function*" 太大，无法进行分析|
|[编译器警告（等级1） C4961](compiler-warning-c4961.md)|没有将任何配置文件数据合并到“.pgd file”，因此已禁用按配置文件优化|
|[编译器警告（等级4） C4962](compiler-warning-c4962.md)|"*function*"：禁用按配置文件优化，因为优化导致配置文件数据变得不一致|
|编译器警告（等级1） C4963|"*description*"：未找到配置文件数据;在检测的生成中使用了不同的编译器选项|
|[编译器警告（等级1） C4964](compiler-warning-level-1-c4964.md)|未指定优化选项;不会收集配置文件信息|
|[编译器警告（等级1） C4965](compiler-warning-level-1-c4965.md)|整数0的隐式框;使用 nullptr 或显式强制转换|
|编译器警告（等级1） C4966|"*function*" 的 __code_seg 批注具有不受支持的段名称，已忽略批注|
|编译器警告 C4970|委托构造函数：由于 "*type*" 是静态的，因此忽略了目标对象|
|编译器警告（等级1） C4971|参数顺序： \<目标对象 >， \<委托构造函数的目标函数 > 已弃用， \<请使用目标 function \<>，目标 object = "" >|
|[编译器警告（等级1，错误） C4972](compiler-warning-c4972.md)|直接修改取消装箱操作的结果或将其视为左值是不可验证的|
|编译器警告（等级1） C4973|"*symbol*"：标记为已弃用|
|编译器警告（等级1） C4974|"*symbol*"：标记为已弃用|
|编译器警告（等级3） C4981|Warbird：标记为 __forceinline 的函数 "*function*" 未内联，因为该函数包含异常语义|
|[编译器警告 C4984](compiler-warning-c4984.md)|"if constexpr" 是 c + + 17 语言扩展|
|编译器警告（等级3） C4985|"*symbol_name*"：以前的声明中不存在特性。|
|[编译器警告 C4986](compiler-warning-c4986.md)|"*声明*"：异常规范与前面的声明不匹配|
|编译器警告（等级4） C4987|使用了非标准扩展：“throw (...)”|
|编译器警告（等级4） C4988|"*variable*"：在类/函数范围外声明的变量|
|编译器警告（等级4） C4989|"*type*"：类型包含冲突的定义。|
|编译器警告（等级3） C4990|Warbird：*消息*|
|编译器警告（等级3） C4991|Warbird：标记为 __forceinline 的函数 "*function*" 未内联，因为被内联方的保护级别大于父级|
|编译器警告（等级3） C4992|Warbird：标记为 __forceinline 的函数 "*function*" 未内联，因为该函数包含无法保护的内联程序集|
|[编译器警告（等级3） C4995](compiler-warning-level-3-c4995.md)|"*function*"：名称被标记为 #pragma 不推荐使用|
|[编译器警告（等级3） C4996](compiler-warning-level-3-c4996.md)|"已*弃用-声明*"：*弃用消息*（或 "已声明为不推荐使用"）|
|[编译器警告（等级1） C4997](compiler-warning-level-1-c4997.md)|"*class*"：组件类不实现 COM 接口或伪接口|
|编译器警告（等级1） C4998|预期失败：*预期*（*值*）|
|[编译器警告 C4999](compiler-warning-level-1-c4999.md)|未知警告请选择 "视觉C++帮助" 菜单上的 "技术支持" 命令，或打开技术支持帮助文件以获取详细信息|
|编译器警告 C5022|"*type*"：指定了多个移动构造函数|
|编译器警告 C5023|"*type*"：指定了多个移动赋值运算符|
|编译器警告（等级4） C5024|"*type*"：移动构造函数被隐式定义为已删除|
|编译器警告（等级4） C5025|"*type*"：移动赋值运算符被隐式定义为已删除|
|编译器警告（等级1和等级4） C5026|"*type*"：移动构造函数被隐式定义为已删除|
|编译器警告（等级1和等级4） C5027|"*type*"：移动赋值运算符被隐式定义为已删除|
|编译器警告（等级1） C5028|"*name*"：在定义中未指定先前声明（*number*）中指定的对齐方式|
|编译器警告（等级4） C5029|使用了非标准扩展：中C++的对齐特性仅适用于变量、数据成员和标记类型|
|编译器警告（等级3） C5030|无法识别属性 "*attribute*"|
|编译器警告（等级4） C5031|#pragma warning （pop）：可能不匹配，正在弹出的警告状态已推送到不同文件中|
|编译器警告（等级4） C5032|检测到 #pragma 警告（push），但没有相应的 #pragma 警告（pop）|
|编译器警告（等级1） C5033|"*存储类*" 不再是受支持的存储类|
|编译器警告 C5034|使用内部 "*内部*" 导致函数*函数*编译为来宾代码|
|编译器警告 C5035|使用功能 "*feature*" 会将函数*函数*编译为来宾代码|
|编译器警告（等级1） C5036|在用/hybrid： x86arm64 "*type1*" 编译为 "*type2*" 时，varargs 函数指针转换|
|编译器警告（错误） C5037|"*member function*"：类模板成员的外定义不能有默认参数|
|[编译器警告（等级4） C5038](c5038.md)|数据成员 "*member1*" 将在数据成员 "*member2*" 后初始化|
|编译器警告（等级4） C5039|"*function*"：指向在-EHc 下传递到 extern C 函数的可能引发函数的指针或引用。 如果此函数引发异常，则可能出现未定义的行为。|
|编译器警告（等级3） C5040|动态异常规范仅在 c + + 14 及更早版本中有效;视为 noexcept （false）|
|编译器警告（等级1） C5041|"*定义*"：不需要对 constexpr 静态数据成员进行外定义，且在 c + + 17 中已弃用|
|编译器警告（等级3） C5042|"*声明*"：不能在标准C++中指定块范围内的函数声明;删除 "内联" 说明符|
|编译器警告（等级2） C5043|"*规范*"：异常规范与前面的声明不匹配|
|编译器警告（等级4） C5044|命令行选项*选项*的参数指向不存在的路径 "*path*"|
| [编译器警告 C5045](c5045.md) | 如果指定了/Qspectre 开关，编译器将为内存加载插入 Spectre 缓解措施 |
| [编译器警告（等级2） C5046](c5046.md) | "*function*"：未定义带有内部链接的类型的符号 |
| 编译器警告（等级1） C5047 | 不支持使用\_非\_标准\_if with 模块 |
| 编译器警告（等级1） C5048 | 使用宏 "*macroname*" 可能会导致非确定性输出 |
| 编译器警告（等级1） C5049 | "*string*"：嵌入完整路径可能导致依赖于计算机的输出 |
| 编译器警告（等级1） C5050 | 导入模块 "*module_name*" 时可能不兼容的环境：*问题* |
| 编译器警告（等级1） C5100 | \_\_VA\_参数\_ 保留用于可变参数\_宏 |
| 编译器警告（等级1） C5101 | 类似于函数的宏参数列表中的预处理器指令的用法是未定义的行为 |
| 编译器警告（等级1） C5102 | 忽略无效的命令行宏定义 "*value*" |
| 编译器警告（等级1） C5103 | 粘贴 "*token1*" 和 "*token2*" 不会生成有效的预处理令牌 |
| 编译器警告（等级1） C5104 | 在宏替换列表中找到了 "*string1*#*string2*"，是否表示 "*string1*" "#*string2*"？ |
| [编译器警告（等级1） C5105](c5105.md) | 生成 "已定义" 的宏扩展具有未定义的行为 |
| 编译器警告（等级1） C5106 | 用不同的参数名称重新定义了宏 |
| 编译器警告（等级1） C5107 | 缺少终止 "*char*" 字符 |

## <a name="see-also"></a>请参阅

[C/C++编译器和生成工具错误和警告](../compiler-errors-1/c-cpp-build-errors.md) \
[编译器警告 C4000-C5999](compiler-warnings-c4000-c5999.md)
