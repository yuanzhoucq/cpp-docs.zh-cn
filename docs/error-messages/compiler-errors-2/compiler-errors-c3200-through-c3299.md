---
title: 编译器错误 C3200 - C3299
ms.date: 04/21/2019
f1_keywords:
- C3220
- C3221
- C3245
- C3249
- C3250
- C3256
- C3257
- C3258
- C3259
- C3260
- C3261
- C3263
- C3267
- C3281
- C3294
helpviewer_keywords:
- C3220
- C3221
- C3245
- C3249
- C3250
- C3256
- C3257
- C3258
- C3259
- C3260
- C3261
- C3263
- C3267
- C3281
- C3294
ms.assetid: 6b3104f6-63bc-4823-b6f3-b8a16be4b87f
ms.openlocfilehash: 6965fcde5f7cc93464593e83f787d0a5838398dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62281490"
---
# <a name="compiler-errors-c3200-through-c3299"></a>编译器错误 C3200 - C3299

在本部分文档中的文章说明了由编译器生成的错误消息的子集。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>错误消息

|Error|消息|
|-----------|-------------|
|[编译器错误 C3200](compiler-error-c3200.md)|'*类型*： 模板参数的无效的模板参数*参数*，应为类模板|
|[编译器错误 C3201](compiler-error-c3201.md)|类模板的模板参数列表*模板*不符模板参数的模板参数列表*参数*|
|[编译器错误 C3202](compiler-error-c3202.md)|'*标识符*： 无效的默认参数，应为类模板|
|[编译器错误 C3203](compiler-error-c3203.md)|'*标识符*： 未专用化的类模板/泛型不能用作模板/泛型参数的模板/泛型参数*参数*，应为 real 类型|
|[编译器错误 C3204](compiler-error-c3204.md)|'*函数*不能从 catch 块内调用|
|[编译器错误 C3205](compiler-error-c3205.md)|模板 template 参数的参数列表*标识符*缺少|
|[编译器错误 C3206](compiler-error-c3206.md)|'*函数*： 无效的模板/泛型参数*模板*，缺少模板/泛型参数列表类模板/泛型'*类型*|
|[编译器错误 C3207](compiler-error-c3207.md)|'*函数*： 模板参数无效*参数*，应当是类模板|
|[编译器错误 C3208](compiler-error-c3208.md)|'*函数*： 类模板的模板参数列表*模板*不符模板 template 参数的模板参数列表'*参数*|
|[编译器错误 C3209](compiler-error-c3209.md)|'*类型*： 泛型类必须是托管/WinRT 类|
|[编译器错误 C3210](compiler-error-c3210.md)|'*标识符*： 访问声明可以仅应用于基类成员|
|[编译器错误 C3211](compiler-error-c3211.md)|'*函数*： 显式专用化正在使用部分专用化语法，改为使用 template<>|
|[编译器错误 C3212](compiler-error-c3212.md)|'*函数*： 模板成员的显式专用化必须是显式特殊化的成员|
|[编译器错误 C3213](compiler-error-c3213.md)|基本类的*类*是可访问性低于*derived_class*|
|[编译器错误 C3214](compiler-error-c3214.md)|'*自变量*： 泛型参数的类型参数无效*参数*的泛型*类型*，不满足约束*约束*'|
|[编译器错误 C3215](compiler-error-c3215.md)|'*constraint1*： 泛型类型参数已由约束*constraint2*|
|[编译器错误 C3216](compiler-error-c3216.md)|约束必须不是泛型参数，'*类型*|
|[编译器错误 C3217](compiler-error-c3217.md)|'*参数*： 泛型参数不能在此声明中进行约束|
|[编译器错误 C3218](compiler-error-c3218.md)|'*类型*： 不允许作为约束的类型|
|[编译器错误 C3219](compiler-error-c3219.md)|'*参数*： 泛型参数不能由多个非接口约束:'*类型*|
|编译器错误 C3220|'*接口*： 接口不能有 progid|
|编译器错误 C3221|'*成员*： 多个 default 和 case 特性不允许在成员上|
|[编译器错误 C3222](compiler-error-c3222.md)|'*函数*： 不能声明成员的默认自变量的托管 WinRT 类型的函数或泛型函数|
|[编译器错误 C3223](compiler-error-c3223.md)|'*属性*： 不能将 typeid 应用到属性|
|[编译器错误 C3224](compiler-error-c3224.md)|'*类型*： 没有重载的泛型采用*数*泛型类型参数|
|[编译器错误 C3225](compiler-error-c3225.md)|泛型类型参数*自变量*'不能是'*类型*，它必须是值类型或引用类型的句柄|
|[编译器错误 C3226](compiler-error-c3226.md)|泛型声明内不允许出现模板声明|
|[编译器错误 C3227](compiler-error-c3227.md)|'*类型*： 不能使用'*运算符*来分配泛型类型|
|[编译器错误 C3228](compiler-error-c3228.md)|'*函数*： 泛型类型参数*自变量*'不能是'*类型*，它必须是值类型或句柄类型|
|[编译器错误 C3229](compiler-error-c3229.md)|'*类型*： 不允许泛型类型参数上的间接寻址|
|[编译器错误 C3230](compiler-error-c3230.md)|'*函数*： 模板类型参数*自变量*不能包含泛型类型参数:*类型*|
|[编译器错误 C3231](compiler-error-c3231.md)|'*类型*： 模板类型参数不能使用泛型类型参数|
|[编译器错误 C3232](compiler-error-c3232.md)|'*参数*： 泛型类型参数不能使用限定名中|
|[编译器错误 C3233](compiler-error-c3233.md)|'*类型*： 泛型类型参数已被约束|
|[编译器错误 C3234](compiler-error-c3234.md)|泛型类可能无法从泛型类型参数派生|
|[编译器错误 C3235](compiler-error-c3235.md)|'*专用化*： 不允许显式或部分专用化泛型类|
|[编译器错误 C3236](compiler-error-c3236.md)|不允许显式实例化泛型|
|[编译器错误 C3237](compiler-error-c3237.md)|'*类*： 泛型类不能是自定义属性|
|[编译器错误 C3238](compiler-error-c3238.md)|'*类型*： 具有此名称的类型已转发到程序集*程序集*|
|[编译器错误 C3239](compiler-error-c3239.md)|'*类型*： 公共语言运行时不允许使用指向内部 /pin 指针的指针|
|[编译器错误 C3240](compiler-error-c3240.md)|'*标识符*： 必须为非重载抽象成员函数*类型*|
|[编译器错误 C3241](compiler-error-c3241.md)|'*成员*： 此方法不由引入'*接口*|
|[编译器错误 C3242](compiler-error-c3242.md)|'*函数*： 只能显式重写虚函数|
|[编译器错误 C3243](compiler-error-c3243.md)|未引入任何重载函数*接口*|
|[编译器错误 C3244](compiler-error-c3244.md)|'*成员*： 通过引入了此方法*接口 1*'不是'*interface2*|
|编译器错误 C3245|'*函数*： 使用变量模板需要模板自变量列表|
|[编译器错误 C3246](compiler-error-c3246.md)|'*类*： 不能继承自*base_class*as 已被声明为*继承*|
|[编译器错误 C3247](compiler-error-c3247.md)|'*组件类*： 组件类不能继承自另一个组件类*base_class*|
|[编译器错误 C3248](compiler-error-c3248.md)|已过时。 '*函数*： 函数声明为 sealed 不能通过重写*函数*|
|编译器错误 C3249|非法语句或子表达式 constexpr 函数|
|编译器错误 C3250|'*声明*: constexpr 函数体中不允许声明|
|[编译器错误 C3251](compiler-error-c3251.md)|无法调用在数值类型实例上的基类方法|
|[编译器错误 C3252](compiler-error-c3252.md)|'*函数*： 不能降低托管/WinRT 类型中的虚方法的可访问性|
|[编译器错误 C3253](compiler-error-c3253.md)|'*函数*： 显式重写错误|
|[编译器错误 C3254](compiler-error-c3254.md)|'*函数*： 类包含显式重写*函数*但不会从包含函数声明的接口派生|
|[编译器错误 C3255](compiler-error-c3255.md)|'*类型*： 不能动态地分配本机堆上的此值类型对象|
|编译器错误 C3256|'*函数*： 变量使用不会生成一个常量表达式|
|编译器错误 C3257|已过时。|
|编译器错误 C3258|已过时。|
|编译器错误 C3259|constexpr 函数只能有一个返回语句|
|编译器错误 C3260|'*令牌*： 跳过 lambda 主体之前的意外的标记|
|编译器错误 C3261|返回托管/WinRT 数组的函数必须有数组括号在声明的结尾:*标识符*（...）[]'|
|[编译器错误 C3262](compiler-error-c3262.md)|无效的数组索引：*数量*为指定的维*数量*-维*类型*|
|编译器错误 C3263|已过时。|
|[编译器错误 C3264](compiler-error-c3264.md)|'*标识符*： 类-构造函数不能有返回类型|
|[编译器错误 C3265](compiler-error-c3265.md)|无法声明托管*managed_construct*中非托管'*unmanaged_construct*|
|[编译器错误 C3266](compiler-error-c3266.md)|'*函数*： 类-构造函数必须具有 void 参数列表|
|编译器错误 C3267|已过时。|
|[编译器错误 C3268](compiler-error-c3268.md)|'*函数*： 泛型函数或泛型类的成员函数不能具有变量参数列表|
|[编译器错误 C3269](compiler-error-c3269.md)|'*函数*： 托管/WinRT 类型的成员函数不能使用...声明|
|[编译器错误 C3270](compiler-error-c3270.md)|'*字段*: FieldOffset 特性只能在 StructLayout(LayoutKind::Explicit) 的上下文中|
|[编译器错误 C3271](compiler-error-c3271.md)|'*字段*： 无效的值*数*FieldOffset 特性的|
|[编译器错误 C3272](compiler-error-c3272.md)|'*符号*： 符号需要 FieldOffset，因为它是结构/类的成员*type_name*使用 StructLayout(LayoutKind::Explicit) 定义|
|[编译器错误 C3273](compiler-error-c3273.md)|'*关键字*： 不允许对C++try 块|
|[编译器错误 C3274](compiler-error-c3274.md)|最后 /&#95;&#95;最后没有匹配的 try|
|[编译器错误 C3275](compiler-error-c3275.md)|'*标识符*： 不能使用该无限定符的符号|
|[编译器错误 C3276](compiler-error-c3276.md)|'*关键字*： 最后的跳转 /&#95;&#95;最后块有未定义的行为在终止处理期间|
|[编译器错误 C3277](compiler-error-c3277.md)|不能定义非托管的枚举 '*枚举*内部托管*类型*|
|[编译器错误 C3278](compiler-error-c3278.md)|直接调用的接口或纯方法*函数*将在运行时失败|
|[编译器错误 C3279](compiler-error-c3279.md)|不允许对在 cli 命名空间中声明的类模板进行部分专用化、显式专用化和显式实例化|
|[编译器错误 C3280](compiler-error-c3280.md)|'*函数*： 不能将托管类型的成员函数编译成非托管函数|
|编译器错误 C3281|'*函数*： 全局运算符不能具有托管/WinRT 类型*类型*签名中|
|[编译器错误 C3282](compiler-error-c3282.md)|泛型参数列表只能出现在托管/WinRT 类、 结构或函数|
|[编译器错误 C3283](compiler-error-c3283.md)|'*接口*: 接口不能有实例构造函数|
|[编译器错误 C3284](compiler-error-c3284.md)|泛型形参约束*参数*的函数*声明符*必须匹配的泛型参数约束*参数*的函数'*声明符*|
|[编译器错误 C3285](compiler-error-c3285.md)|对于每个语句不能作用于类型的变量*类型*|
|[编译器错误 C3286](compiler-error-c3286.md)|'*说明符*： 迭代变量不能包含任何存储类说明符|
|[编译器错误 C3287](compiler-error-c3287.md)|类型*类型*（GetEnumerator 的返回类型） 必须具有适当的公共 MoveNext 成员函数和公共 Current 属性|
|[编译器错误 C3288](compiler-error-c3288.md)|'*类型*： 非法取消对引用的句柄类型|
|[编译器错误 C3289](compiler-error-c3289.md)|'*标识符*： 无法索引 trivial 属性|
|[编译器错误 C3290](compiler-error-c3290.md)|'*类型*: trivial 属性不能具有引用类型|
|[编译器错误 C3291](compiler-error-c3291.md)|default： 不能作为 trivial 属性的名称|
|[编译器错误 C3292](compiler-error-c3292.md)|cli 命名空间不能重新打开|
|[编译器错误 C3293](compiler-error-c3293.md)|'*标识符*： 使用 default 访问类的默认属性 （索引器）*类*|
|编译器错误 c3294:|已过时。|
|[编译器错误 C3295](compiler-error-c3295.md)|#pragma*说明符*只能在全局或命名空间范围|
|[编译器错误 C3296](compiler-error-c3296.md)|'*标识符*： 已存在具有此名称的属性|
|[编译器错误 C3297](compiler-error-c3297.md)|' *constraint2*： 不能使用' *constraint1*作为约束因为 ' *constraint1*具有值约束|
|[编译器错误 C3298](compiler-error-c3298.md)|' *constraint1*： 不能使用' *constraint2*作为约束因为 ' *constraint2*具有 ref 约束和*constraint1*具有值约束|
|[编译器错误 C3299](compiler-error-c3299.md)|'*函数*： 不能指定约束，它们都继承自基方法|

## <a name="see-also"></a>请参阅

[C /C++编译器和生成工具错误和警告](../compiler-errors-1/c-cpp-build-errors.md) \
[编译器错误 C2000-C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
