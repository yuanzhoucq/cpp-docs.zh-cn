---
title: 编译器错误 C2500 到 C2599 |Microsoft 文档
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2501
- C2508
- C2515
- C2519
- C2520
- C2522
- C2525
- C2527
- C2536
- C2538
- C2539
- C2546
- C2547
- C2559
- C2560
- C2564
- C2565
- C2576
- C2578
- C2580
- C2590
- C2591
- C2595
- C2596
helpviewer_keywords:
- C2501
- C2508
- C2515
- C2519
- C2520
- C2522
- C2525
- C2527
- C2536
- C2538
- C2539
- C2546
- C2547
- C2559
- C2560
- C2564
- C2565
- C2576
- C2578
- C2580
- C2590
- C2591
- C2595
- C2596
dev_langs:
- C++
ms.assetid: a869aaed-e9f6-49e3-b273-00ea7f45bed7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 994f29009294e6b49851a817a5872fcaa122b153
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-errors-c2500-through-c2599"></a>编译器错误 C2500 到 C2599

本部分中的文档的文章说明由编译器生成的错误消息的子集。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>错误消息

|Error|消息|
|-----------|-------------|
|[编译器错误 C2500](compiler-error-C2500.md)|*identifier1*:*identifier2*已直接基类|
|编译器错误 C2501|*标识符*: __declspec (*说明符*) 可以仅应用于结构、 联合、 类或无符号的位域成员|
|[编译器错误 C2502](compiler-error-C2502.md)|*标识符*： 上的基类的访问修饰符太多|
|[编译器错误 C2503](compiler-error-C2503.md)|*类*： 基类，这些类不能包含零大小的数组|
|[编译器错误 C2504](compiler-error-C2504.md)|*类*： 未定义的基类|
|[编译器错误 C2505](compiler-error-C2505.md)|*符号*: __declspec (*说明符*) 只能应用于声明或定义的全局对象或静态数据成员|
|[编译器错误 C2506](compiler-error-C2506.md)|*成员*: __declspec (*说明符*) 不能应用于此符号|
|[编译器错误 C2507](compiler-error-C2507.md)|*标识符*： 基的类上的虚拟修饰符太多|
|编译器错误 C2508|*标识符*: __declspec (*specifier1*) 不能与组合 __declspec (*specifier2*)|
|[编译器错误 C2509](compiler-error-C2509.md)|*标识符*： 成员函数中未声明*类*|
|[编译器错误 C2510](compiler-error-C2510.md)|*标识符*： 左侧的:: 必须是类/结构/联合|
|[编译器错误 C2511](compiler-error-C2511.md)|*标识符*： 重载成员函数中找不到*类*|
|[编译器错误 C2512](compiler-error-C2512.md)|*标识符*： 没有适当的默认构造函数可用|
|[编译器错误 C2513](compiler-error-C2513.md)|* 类型: = 之前的任何变量声明|
|[编译器错误 C2514](compiler-error-C2514.md)|*类*： 类具有任何构造函数|
|编译器错误 C2515|*标识符*: vtguard 只能应用于类声明或定义|
|[编译器错误 C2516](compiler-error-C2516.md)|*类*： 不是合法的基本类|
|[编译器错误 C2517](compiler-error-C2517.md)|*标识符*： 右侧的:: 未定义|
|[编译器错误 C2518](compiler-error-C2518.md)|关键字*关键字*非法基类列表中; 已忽略|
|编译器错误 C2519|*标识符*: WinRT 特性只能包含公共字段|
|编译器错误 C2520|*类*： 没有隐式构造函数隐式转换为可用|
|[编译器错误 C2521](compiler-error-C2521.md)|析构函数/终结器不采用任何参数|
|编译器错误 C2522|*标识符*： 不能用于重载标识符*identifier1*因为它已经在指定*identifier2*|
|[编译器错误 C2523](compiler-error-C2523.md)|*类*:: ~*标识符*： 析构函数/终结器标记不匹配|
|[编译器错误 C2524](compiler-error-C2524.md)|*标识符*： 析构函数/终结器必须具有 void 参数列表|
|编译器错误 C2525|*标识符*: 参数 '*identifier1*名为*identifier2*基函数，必须在已发布的实现中进行匹配|
|[编译器错误 C2526](compiler-error-C2526.md)|*identifier1*: C 链接函数不能返回 c + + 类*identifier2*|
|编译器错误 C2527|*标识符*: DefaultOverload 不能同时指定*function1*和*function2*。 删除一个指定，或者在实现期间重命名该函数|
|[编译器错误 C2528](compiler-error-C2528.md)|*标识符*： 指针引用是非法的|
|[编译器错误 C2529](compiler-error-C2529.md)|*标识符*： 引用的引用是非法的|
|[编译器错误 C2530](compiler-error-C2530.md)|*标识符*： 必须初始化引用|
|[编译器错误 C2531](compiler-error-C2531.md)|*标识符*： 对有点字段非法引用|
|[编译器错误 C2532](compiler-error-C2532.md)|*标识符*： 非法引用修饰符|
|[编译器错误 C2533](compiler-error-C2533.md)|*标识符*： 不能有返回类型的构造函数|
|[编译器错误 C2534](compiler-error-C2534.md)|*标识符*： 构造函数无法返回值|
|[编译器错误 C2535](compiler-error-C2535.md)|*标识符*： 已定义或声明的成员函数|
|编译器错误 C2536|已过时。|
|[编译器错误 C2537](compiler-error-C2537.md)|*说明符*： 非法链接规范|
|编译器错误 C2538|已过时。|
|编译器错误 C2539|已过时。|
|[编译器错误 C2540](compiler-error-C2540.md)|作为数组界限的非常量表达式|
|[编译器错误 C2541](compiler-error-C2541.md)|*标识符*： 无法删除不是指针的对象|
|[编译器错误 C2542](compiler-error-C2542.md)|*标识符*： 类对象具有初始化没有构造函数|
|[编译器错误 C2543](compiler-error-C2543.md)|预期] 运算符 []|
|[编译器错误 C2544](compiler-error-C2544.md)|预期 ')' 运算符 '（）'|
|[编译器错误 C2545](compiler-error-C2545.md)|*运算符*： 无法查找重载运算符|
|编译器错误 C2546|*标识符*： 当 PIA 和 NO-PIA 必须首先引用 PIA 中定义了一个类型|
|编译器错误 C2547|*标识符*： 已发布的方法的所有参数必须显式都命名的声明上|
|[编译器错误 C2548](compiler-error-C2548.md)|*函数*： 缺少参数的默认参数*参数*|
|[编译器错误 C2549](compiler-error-C2549.md)|用户定义的转换不能指定返回类型|
|[编译器错误 C2550](compiler-error-C2550.md)|*标识符*： 构造函数定义上只允许构造函数初始值设定项列表|
|[编译器错误 C2551](compiler-error-C2551.md)|“void *”类型需要显式转换|
|[编译器错误 C2552](compiler-error-C2552.md)|*标识符*： 不能用初始值设定项列表初始化非聚合|
|[编译器错误 C2553](compiler-error-C2553.md)|*类型* *derived_class*::*函数*： 重写虚函数的返回类型不同于*类型* *base_类*::*函数*|
|[编译器错误 C2555](compiler-error-C2555.md)|*derived_class*::*函数*： 重写虚函数返回类型不同，且不从协变*base_class*::*函数*'|
|[编译器错误 C2556](compiler-error-C2556.md)|*type1* *类*::*函数*： 重载的函数不同只是返回类型从*type2* *类*::*函数*|
|[编译器错误 C2557](compiler-error-C2557.md)|*标识符*： 不能没有构造函数初始化私有成员和受保护成员|
|[编译器错误 C2558](compiler-error-C2558.md)|类的*类*： 没有可用的复制构造函数或复制构造函数声明为 explicit|
|编译器错误 C2559|*标识符*： 不能重载，而无需 ref 限定符包含 ref 限定符包含的成员函数的成员函数|
|编译器错误 C2560|*标识符*： 不能重载使用 ref 限定符包含没有 ref 限定符的成员函数的成员函数|
|[编译器错误 C2561](compiler-error-C2561.md)|*函数*： 函数必须返回值|
|[编译器错误 C2562](compiler-error-C2562.md)|*函数*: void 函数返回值|
|[编译器错误 C2563](compiler-error-C2563.md)|形参表中的不匹配|
|编译器错误 C2564|已过时。|
|编译器错误 C2565|*标识符*: ref 限定符是非法的构造函数/析构函数|
|[编译器错误 C2566](compiler-error-C2566.md)|条件表达式中的重载的函数|
|[编译器错误 C2567](compiler-error-C2567.md)|无法打开中的元数据*filename*， *possible_reason*|
|[编译器错误 C2568](compiler-error-C2568.md)|*标识符*： 无法解析函数重载|
|[编译器错误 C2569](compiler-error-C2569.md)|*标识符*： 枚举/联合不能用作基类|
|[编译器错误 C2570](compiler-error-C2570.md)|*标识符*： 联合不能具有基类|
|[编译器错误 C2571](compiler-error-C2571.md)|*标识符*： 虚函数不能为联合中*联合*|
|[编译器错误 C2572](compiler-error-C2572.md)|*函数*： 重定义的默认参数： 参数*数*|
|[编译器错误 C2573](compiler-error-C2573.md)|*类*： 不能删除指向此类型; 的对象类具有 operator delete 的重载均没有非位置。 使用:: 删除，或将运算符 delete(void*) 添加到类|
|[编译器错误 C2574](compiler-error-C2574.md)|*析构函数*： 不能声明为静态|
|[编译器错误 C2575](compiler-error-C2575.md)|*标识符*： 只能成员函数和基虚拟|
|编译器错误 C2576|*标识符*： 不能引入新的虚拟方法，为 public。 考虑进行非虚拟方法或更改的可访问性为内部或 protected private|
|[编译器错误 C2577](compiler-error-C2577.md)|*标识符*： 析构函数/终结器不能有返回类型|
|编译器错误 C2578|*类*： 类型不能有 protected 或 protected 公共的构造函数|
|[编译器错误 C2579](compiler-error-C2579.md)|无法解析类型*类型*(*偏移量*)。 应处于*filename*|
|编译器错误 C2580|*标识符*： 不允许多个版本的默认特殊成员函数|
|[编译器错误 C2581](compiler-error-C2581.md)|*类型*： 静态运算符 = 是非法的函数|
|[编译器错误 C2582](compiler-error-C2582.md)|运算符*运算符*函数 is 中不可用*类型*|
|[编译器错误 C2583](compiler-error-C2583.md)|*标识符*: const/volatile this 指针是非法的构造函数/析构函数|
|[编译器错误 C2584](compiler-error-C2584.md)|*类*： 直接基*base_class2*不可访问; 已基数*base_class1*|
|[编译器错误 C2585](compiler-error-C2585.md)|显式转换为*类型*不明确|
|[编译器错误 C2586](compiler-error-C2586.md)|不正确的用户定义的转换语法： 非法的间接寻址|
|[编译器错误 C2587](compiler-error-C2587.md)|*标识符*： 非法用作本地变量的默认参数|
|[编译器错误 C2588](compiler-error-C2588.md)|:: ~*标识符*： 非法全局析构函数/终结器|
|[编译器错误 C2589](compiler-error-C2589.md)|*标识符*： 非法的标记，在右侧::|
|编译器错误 C2590|*标识符*： 只有一个构造函数可将基/成员初始值设定项列表|
|编译器错误 C2591|不能使用 ExclusiveTo*类型*作为自变量。 仅 ref class 是一个有效的参数|
|[编译器错误 C2592](compiler-error-C2592.md)|*类*:*base_class2*继承自*base_class1*，且无法重新指定|
|[编译器错误 C2593](compiler-error-C2593.md)|运算符*标识符*不明确|
|[编译器错误 C2594](compiler-error-C2594.md)|*运算符*： 不明确的转换，从*type1*到*type2*|
|编译器错误 C2595|*标识符*WinRT 属性类型必须都密封|
|编译器错误 C2596|*标识符*WinRT 特性字段只能是公共枚举类、 int、 unsigned 的 int、 bool、 platform:: type、 platform:: string' 或 ' Windows:: Foundation:: HResult|
|[编译器错误 C2597](compiler-error-C2597.md)|非法引用非静态成员*标识符*|
|[编译器错误 C2598](compiler-error-C2598.md)|链接规范必须在全局范围内|
|[编译器错误 C2599](compiler-error-C2599.md)|*标识符*： 不允许管理/WinRT 枚举的前向声明|  