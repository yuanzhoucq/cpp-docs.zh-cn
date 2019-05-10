---
title: 编译器错误 C3000 - C3099
ms.date: 04/21/2019
f1_keywords:
- C3051
- C3061
- C3064
- C3067
- C3074
- C3078
- C3079
- C3081
- C3082
- C3086
- C3088
- C3089
- C3090
- C3091
- C3092
- C3093
- C3098
helpviewer_keywords:
- C3051
- C3061
- C3064
- C3067
- C3074
- C3078
- C3079
- C3081
- C3082
- C3086
- C3088
- C3089
- C3090
- C3091
- C3092
- C3093
- C3098
ms.assetid: 01b7b9cb-b351-4b5a-8cb0-1fcddb08d2ab
ms.openlocfilehash: 08c7b691d6390e6c1070fc71dff116604731ebab
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64856928"
---
# <a name="compiler-errors-c3000-through-c3099"></a>编译器错误 C3000 - C3099

在本部分文档中的文章说明了由编译器生成的错误消息的子集。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>错误消息

|Error|消息|
|-----------|-------------|
|编译器错误 C3000|已过时。|
|[编译器错误 C3001](compiler-error-c3001.md)|'*消息*： 应为 OpenMP 指令名称|
|[编译器错误 C3002](compiler-error-c3002.md)|'*name1* *name2*： 多个 OpenMP 指令名称|
|[编译器错误 C3003](compiler-error-c3003.md)|'*指令*:在指令子句之后不允许使用 OpenMP 指令名称|
|[编译器错误 C3004](compiler-error-c3004.md)|'*子句*： 子句在 OpenMP 无效*指令*指令|
|[编译器错误 C3005](compiler-error-c3005.md)|'*消息*: OpenMP 上出现意外的标记'*指令*指令|
|[编译器错误 C3006](compiler-error-c3006.md)|'*子句*： 子句在 OpenMP*指令*指令缺少应有的参数|
|[编译器错误 C3007](compiler-error-c3007.md)|'*子句*： 子句在 OpenMP*指令*指令不采用自变量|
|[编译器错误 C3008](compiler-error-c3008.md)|*自变量*： 参数缺少右括号) 在 OpenMP*指令*指令|
|[编译器错误 C3009](compiler-error-c3009.md)|'*标签*： 跳转到 OpenMP 结构化块不允许|
|[编译器错误 C3010](compiler-error-c3010.md)|'*标签*： 跳出 OpenMP 结构化块不允许|
|[编译器错误 C3011](compiler-error-c3011.md)|并行区域内不允许直接使用内联程序集|
|[编译器错误 C3012](compiler-error-c3012.md)|'*函数*： 不允许并行区域内直接使用内部函数|
|[编译器错误 C3013](compiler-error-c3013.md)|'*子句*： 子句可能只能出现一次在 OpenMP*指令*指令|
|[编译器错误 C3014](compiler-error-c3014.md)|预期的 OpenMP 循环 '*指令*指令|
|[编译器错误 C3015](compiler-error-c3015.md)|OpenMP“for”语句中的初始化格式不正确|
|[编译器错误 C3016](compiler-error-c3016.md)|'*标识符*： 在 OpenMP for 语句的索引变量必须具有带符号的整型|
|[编译器错误 C3017](compiler-error-c3017.md)|OpenMP“for”语句中的终止测试格式不正确|
|[编译器错误 C3018](compiler-error-c3018.md)|'*标识符*:OpenMP for 测试或递增必须使用索引变量*变量*|
|[编译器错误 C3019](compiler-error-c3019.md)|在 OpenMP for 语句的增量具有格式不正确|
|[编译器错误 C3020](compiler-error-c3020.md)|'*变量*: OpenMP for 循环索引变量不能在循环体中修改|
|[编译器错误 C3021](compiler-error-c3021.md)|'*自变量*： 参数为空在 OpenMP*指令*指令|
|[编译器错误 C3022](compiler-error-c3022.md)|'*指令*： 无效的安排类型的'*指令*在 OpenMP*指令*指令|
|[编译器错误 C3023](compiler-error-c3023.md)|'*自变量*: OpenMP 的参数中遇到意外的标记'*指令*子句|
|[编译器错误 C3024](compiler-error-c3024.md)|schedule （runtime)： 不允许使用 chunk_size 表达式|
|[编译器错误 C3025](compiler-error-c3025.md)|'*子句*： 应为整型表达式|
|[编译器错误 C3026](compiler-error-c3026.md)|'*子句*： 常量表达式必须为正数|
|[编译器错误 C3027](compiler-error-c3027.md)|'*子句*： 应为算术或指针表达式|
|[编译器错误 C3028](compiler-error-c3028.md)|'*成员*： 只有变量或静态数据成员可以使用数据共享子句中|
|[编译器错误 C3029](compiler-error-c3029.md)|'*符号*： 只能出现一次在数据共享子句在 OpenMP 指令中|
|[编译器错误 C3030](compiler-error-c3030.md)|'*标识符*： 变量中*指令*子句/指令不能具有引用类型|
|[编译器错误 C3031](compiler-error-c3031.md)|'*标识符*: reduction 子句中的变量必须是标量算术类型|
|[编译器错误 C3032](compiler-error-c3032.md)|'*标识符*： 变量中*子句*'子句不能具有不完整类型*类型*|
|[编译器错误 C3033](compiler-error-c3033.md)|'*标识符*： 变量中*子句*' 子句不能具有常量限定类型|
|[编译器错误 C3034](compiler-error-c3034.md)|OpenMP*指令*指令不能直接嵌套在'*指令*指令|
|[编译器错误 C3035](compiler-error-c3035.md)|OpenMP“ordered”指令必须使用“ordered”子句直接绑定到“for”或“parallel for”指令|
|[编译器错误 C3036](compiler-error-c3036.md)|'*子句*: OpenMP reduction 子句中的无效的运算符标记|
|[编译器错误 C3037](compiler-error-c3037.md)|'*标识符*： 变量中*子句*子句必须在封闭上下文中共享|
|[编译器错误 C3038](compiler-error-c3038.md)|'*标识符*: private 子句中的变量不能是封闭上下文中的 reduction 变量|
|[编译器错误 C3039](compiler-error-c3039.md)|'*标识符*： 在 OpenMP for 语句的索引变量不能是 reduction 变量|
|[编译器错误 C3040](compiler-error-c3040.md)|'*标识符*: reduction 子句中的变量的类型与 reduction 运算符不兼容*运算符*|
|[编译器错误 C3041](compiler-error-c3041.md)|'*标识符*: copyprivate 子句中的变量必须是私有在封闭上下文中|
|[编译器错误 C3042](compiler-error-c3042.md)|copyprivate 和 nowait 子句不能同时出现在 OpenMP*指令*指令|
|[编译器错误 C3043](compiler-error-c3043.md)|OpenMP“critical”指令不能嵌套在同名的“critical”指令中|
|[编译器错误 C3044](compiler-error-c3044.md)|section： 仅允许直接嵌套在 OpenMP sections 指令|
|[编译器错误 C3045](compiler-error-c3045.md)|OpenMP “sections”指令后应为一个复合语句。 缺少“{”|
|[编译器错误 C3046](compiler-error-c3046.md)|OpenMP“#pragma omp sections”区域中缺少结构化块|
|[编译器错误 C3047](compiler-error-c3047.md)|OpenMP“sections”区域中的结构化块的前面必须是“#pragma omp section”|
|[编译器错误 C3048](compiler-error-c3048.md)|“#pragma omp atomic”后面的表达式格式不正确|
|[编译器错误 C3049](compiler-error-c3049.md)|'*自变量*: OpenMP default 子句中的参数无效|
|[编译器错误 C3050](compiler-error-c3050.md)|'*类*: ref 类不能继承'*标识符*|
|编译器错误 C3051|已过时。|
|[编译器错误 C3052](compiler-error-c3052.md)|'*标识符*: default （none） 子句下的数据共享子句中未出现变量|
|[编译器错误 C3053](compiler-error-c3053.md)|'*标识符*: threadprivate 只是对全局或静态数据项有效|
|[编译器错误 C3054](compiler-error-c3054.md)|当前在泛型类或函数中不支持“#pragma omp parallel”|
|[编译器错误 C3055](compiler-error-c3055.md)|'*标识符*: threadprivate 指令中使用之前，不能引用符号|
|[编译器错误 C3056](compiler-error-c3056.md)|'*标识符*： 符号不是在同一作用域 threadprivate 指令中|
|[编译器错误 C3057](compiler-error-c3057.md)|'*标识符*： 当前不支持 threadprivate 符号的动态初始化|
|[编译器错误 C3058](compiler-error-c3058.md)|'*标识符*： 符号用于 copyin 子句中之前，不能声明为 threadprivate|
|[编译器错误 C3059](compiler-error-c3059.md)|'*标识符*： 不能用于 threadprivate 符号*子句*子句|
|[编译器错误 C3060](compiler-error-c3060.md)|'*标识符*： 友元函数可能没有使用限定的名 （可能只声明了它） 在类内定义|
|编译器错误 C3061|运算符*运算符*： 不允许枚举 '*类型*与基础类型*类型*|
|[编译器错误 C3062](compiler-error-c3062.md)|'*标识符*： 枚举数需要值，因为基础类型为'*类型*|
|[编译器错误 C3063](compiler-error-c3063.md)|运算符*运算符*： 所有操作数必须都具有相同的枚举类型|
|编译器错误 C3064|'*标识符*： 必须是简单类型或可解析为|
|[编译器错误 C3065](compiler-error-c3065.md)|不允许在非类范围上声明属性|
|[编译器错误 C3066](compiler-error-c3066.md)|有很多方法可以调用此类型的对象用这些自变量|
|编译器错误 C3067|初始值设定项列表不能用于内置运算符]|
|[编译器错误 C3068](compiler-error-c3068.md)|'*标识符*: naked 函数不能包含对象会要求回退如果C++出现异常|
|[编译器错误 C3069](compiler-error-c3069.md)|运算符*运算符*： 不允许用于枚举类型|
|[编译器错误 C3070](compiler-error-c3070.md)|'*标识符*： 属性没有 set 方法|
|[编译器错误 C3071](compiler-error-c3071.md)|运算符*运算符*仅应用于 ref 类或值类型的实例|
|[编译器错误 C3072](compiler-error-c3072.md)|运算符*运算符*不能应用于 ref 类使用一元 %运算符将 ref 的实例转换到句柄类型的类的实例|
|[编译器错误 C3073](compiler-error-c3073.md)|'*标识符*: ref 类没有用户定义的复制构造函数|
|编译器错误 C3074|不能使用带括号的初始值设定项初始化数组|
|[编译器错误 C3075](compiler-error-c3075.md)|'*标识符*： 不能嵌入实例的引用类型，'*类型*，在值类型|
|[编译器错误 C3076](compiler-error-c3076.md)|'*标识符*： 不能嵌入实例的引用类型，'*类型*，在本机类型中|
|[编译器错误 C3077](compiler-error-c3077.md)|'*标识符*： 终结器只能是引用类型的成员|
|编译器错误 C3078|必须在新表达式中指定数组大小|
|编译器错误 C3079|初始值设定项列表不能用作此赋值运算符的右操作数|
|[编译器错误 C3080](compiler-error-c3080.md)|'*终结器*： 终结器不能具有存储类说明符|
|编译器错误 C3081|已过时。|
|编译器错误 C3082|已过时。|
|[编译器错误 C3083](compiler-error-c3083.md)|'*标识符*： 左侧的符号:: 必须是类型|
|[编译器错误 C3084](compiler-error-c3084.md)|'*标识符*： 析构函数/终结器不能为'*关键字*|
|[编译器错误 C3085](compiler-error-c3085.md)|'*标识符*： 构造函数不能为'*关键字*|
|编译器错误 C3086|找不到 std:: initializer_list： 需要 #include \<initializer_list >|
|[编译器错误 C3087](compiler-error-c3087.md)|'*标识符*： 调用的'*声明*将此成员已初始化|
|编译器错误 C3088|'*类*： 特性构造函数必须具有名为形式自变量|
|编译器错误 C3089|'*标识符*： 参数名称与任何数据成员的名称不匹配|
|编译器错误 C3090|'*类*： 特性类不能为模板|
|编译器错误 C3091|'*类*： 特性类不能具有基类|
|编译器错误 C3092|'*类*： 特性类成员不能是有点字段、 静态或 const|
|编译器错误 C3093|'*类型*： 不允许用于特性类成员的类型*成员*|
|[编译器错误 C3094](compiler-error-c3094.md)|'*特性*： 不允许匿名使用|
|[编译器错误 C3095](compiler-error-c3095.md)|'*特性*： 特性不能重复|
|[编译器错误 C3096](compiler-error-c3096.md)|'*特性*： 特性允许只能用于特性类的数据成员|
|[编译器错误 C3097](compiler-error-c3097.md)|'*特性*： 特性必须与作用域程序集: 或模块:|
|编译器错误 C3098|'*标识符*： 属性有任何用户定义的构造函数|
|[编译器错误 C3099](compiler-error-c3099.md)|'*关键字*： 使用 [system:: attributeusageattribute] / [Windows::Foundation::Metadata::AttributeUsageAttribute] 的托管 WinRT 属性|

## <a name="see-also"></a>请参阅

[C /C++编译器和生成工具错误和警告](../compiler-errors-1/c-cpp-build-errors.md) \
[编译器错误 C2000-C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
