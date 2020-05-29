---
title: 编译器错误 C3400 - C3499
ms.date: 04/21/2019
f1_keywords:
- C3401
- C3402
- C3403
- C3404
- C3405
- C3406
- C3407
- C3410
- C3411
- C3416
- C3419
- C3422
- C3424
- C3425
- C3426
- C3427
- C3428
- C3429
- C3430
- C3431
- C3432
- C3433
- C3434
- C3435
- C3436
- C3437
- C3438
- C3439
- C3440
- C3441
- C3442
- C3443
- C3444
- C3471
- C3472
- C3473
- C3474
- C3475
- C3476
- C3477
- C3478
- C3479
- C3486
- C3494
- C3497
helpviewer_keywords:
- C3401
- C3402
- C3403
- C3404
- C3405
- C3406
- C3407
- C3410
- C3411
- C3416
- C3419
- C3422
- C3424
- C3425
- C3426
- C3427
- C3428
- C3429
- C3430
- C3431
- C3432
- C3433
- C3434
- C3435
- C3436
- C3437
- C3438
- C3439
- C3440
- C3441
- C3442
- C3443
- C3444
- C3471
- C3472
- C3473
- C3474
- C3475
- C3476
- C3477
- C3478
- C3479
- C3486
- C3494
- C3497
ms.assetid: a5651dfb-c402-4e01-b3ae-28f371e51d6a
ms.openlocfilehash: f4aff80178033d34cf051a14d89736b2b8347dd0
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446846"
---
# <a name="compiler-errors-c3400-through-c3499"></a>编译器错误 C3400 - C3499

文档的本节中的文章介绍了编译器生成的错误消息的子集。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>错误消息

|错误|Message|
|-----------|-------------|
|[编译器错误 C3400](compiler-error-c3400.md)|涉及 "*e*" 和 "*e*" 的循环约束依赖项|
|编译器错误 C3401|"*说明符*"：程序集访问说明符无效-只允许在类模板上使用 "private"|
|编译器错误 C3402|"*function*"：除了在当前范围内，无法解析重载|
|编译器错误 C3403|thread_local 不能与/clr： pure 或/clr： safe 一起使用|
|编译器错误 C3404|"*构造*"：意外的语法错误|
|编译器错误 C3405|"*function*"：没有完整的说明符无法解析重载|
|编译器错误 C3406|"*关键字*"：不能在详细类型说明符中使用|
|编译器错误 C3407|"*type*" 不能在此上下文中使用|
|[编译器错误 C3408](compiler-error-c3408.md)|"*attribute*"：模板定义中不允许使用特性|
|[编译器错误 C3409](compiler-error-c3409.md)|不允许空特性块|
|编译器错误 C3410|"*identifier*"：显式实例化 "*type*" 的类型与变量模板 "*type*" 的类型不匹配|
|编译器错误 C3411|由于数组的大小不是整数类型，因此 "*type*" 无效|
|[编译器错误 C3412](compiler-error-c3412.md)|"*专用化*"：无法在当前范围内专用化模板|
|[编译器错误 C3413](compiler-error-c3413.md)|"*template*"：显式实例化无效|
|[编译器错误 C3414](compiler-error-c3414.md)|"*function*"：不能定义导入的成员函数|
|[编译器错误 C3415](compiler-error-c3415.md)|找到多个具有不同属性（"0x*值*"）的 "*section*" 节|
|编译器错误 C3416|已过时。|
|[编译器错误 C3417](compiler-error-c3417.md)|"*声明符*"：值类型不能包含用户定义的特殊成员函数|
|[编译器错误 C3418](compiler-error-c3418.md)|不支持访问说明符 "*说明符*"|
|编译器错误 C3419|已过时。|
|[编译器错误 C3420](compiler-error-c3420.md)|"*function*"：终结器不能是虚拟的|
|[编译器错误 C3421](compiler-error-c3421.md)|"*function*"：无法调用此类的终结器，因为它无法访问或不存在|
|编译器错误 C3422|"*声明*"：类型 "*type*" 和 "*type*" 不匹配|
|编译器错误 C3423|已过时。|
|编译器错误 C3424|"*type*"：不允许将函数样式强制转换为数组类型|
|编译器错误 C3425|无法引发指向不完整类型 "*type*" 的对象的指针|
|编译器错误 C3426|无法引发不完整类型 "*type*" 的对象|
|编译器错误 C3427|"*context*"： "*关键字*" 不能用于 layout_version （*number*）|
|编译器错误 C3428|"*context*"： "*关键字*" 只能应用于类声明或定义|
|编译器错误 C3429|"*context*"： "*关键字*" 不能应用于联合|
|编译器错误 C3430|范围枚举必须有名称|
|编译器错误 C3431|"*identifier*"： *type1*不能重新声明为*type2*|
|编译器错误 C3432|"*identifier*"：未区分范围的枚举的前向声明必须有基础类型|
|编译器错误 C3433|"*identifier*"：枚举的所有声明必须具有相同的基础类型，"*type1*" 现在为 "*type2*"|
|编译器错误 C3434|"*context*"：枚举器值 "*number*" 不能表示为 "*type*"，值为 "*number*"|
|编译器错误 C3435|不支持字符集 "*name*"|
|编译器错误 C3436|指定/source-charset、/execution-charset 或/utf-8 时，不支持 #pragma setlocale|
|编译器错误 C3437|指定/source-charset、/execution-charset 或/utf-8 后，不支持 #pragma execution_character_set|
|编译器错误 C3438|"*context*"： "*value*" 不能应用于托管的/WinRT 类|
|编译器错误 C3439|layout_version （*number*）：无效的版本号|
|编译器错误 C3440|"*声明*"： layout_version （*number*）与之前的声明不兼容|
|编译器错误 C3441|"*声明*"：定义类后，不能应用 "*关键字*"|
|编译器错误 C3442|正在初始化 union 的多个成员： "*member1*" 和 "*member2*"|
|编译器错误 C3443|"*Class*" 的默认成员初始值设定项为递归|
|编译器错误 C3444|空的聚合类 "*class*" 必须用 "{}" 初始化|
|[编译器错误 C3445](compiler-error-c3445.md)|"*type*" 的复制列表初始化不能使用显式构造函数|
|[编译器错误 C3446](compiler-error-c3446.md)|"*class*"：值类的成员不允许使用默认成员初始值设定项|
|编译器错误 C3447|已过时。|
|编译器错误 C3448|已过时。|
|编译器错误 C3449|已过时。|
|[编译器错误 C3450](compiler-error-c3450.md)|"*type*"：不是特性;无法指定 [System：： AttributeUsageAttribute]/[Windows：： Foundation：： Metadata：： AttributeUsageAttribute]|
|[编译器错误 C3451](compiler-error-c3451.md)|"*attribute*"：不能将非托管特性应用于 "*type*"|
|[编译器错误 C3452](compiler-error-c3452.md)|列出不是常量的参数成员|
|[编译器错误 C3453](compiler-error-c3453.md)|"*attribute*"：未应用特性，因为限定符 "*限定符*" 不匹配|
|[编译器错误 C3454](compiler-error-c3454.md)|类声明中不允许出现 [attribute]|
|[编译器错误 C3455](compiler-error-c3455.md)|"*attribute*"：没有任何特性构造函数匹配这些参数|
|[编译器错误 C3456](compiler-error-c3456.md)|在托管/WinRT 类声明上不允许使用 [source\_annotation_attribute]|
|[编译器错误 C3457](compiler-error-c3457.md)|"*attribute*"：特性不支持未命名参数|
|[编译器错误 C3458](compiler-error-c3458.md)|"[*attribute*]"：已经为 "*identifier*" 指定了特性 "[*attribute*]"|
|[编译器错误 C3459](compiler-error-c3459.md)|"[*attribute*]"：只允许在类索引器（默认索引属性）上使用特性|
|[编译器错误 C3460](compiler-error-c3460.md)|"*type*"：只有用户定义的类型才能被转发|
|[编译器错误 C3461](compiler-error-c3461.md)|"*type*"：仅可转发托管/WinRT 类型|
|[编译器错误 C3462](compiler-error-c3462.md)|"*type*"：只有导入的类型才能被转发|
|[编译器错误 C3463](compiler-error-c3463.md)|"*type*"：类型不允许出现在特性 "implements" 中|
|[编译器错误 C3464](compiler-error-c3464.md)|"*type*" 嵌套类型不能被转发|
|[编译器错误 C3465](compiler-error-c3465.md)|若要使用类型 "*type*"，必须引用程序集 "*assembly*"|
|[编译器错误 C3466](compiler-error-c3466.md)|"*type*"：泛型类的专用化不能被转发|
|[编译器错误 C3467](compiler-error-c3467.md)|"*type*"：此类型已被转发|
|[编译器错误 C3468](compiler-error-c3468.md)|"*type*"：只能将类型转发到程序集： "*identifier*" 不是程序集|
|[编译器错误 C3469](compiler-error-c3469.md)|"*type*"：不能转发泛型类|
|[编译器错误 C3470](compiler-error-c3470.md)|"*class*"：类不能同时具有索引器（默认索引属性）和运算符 []|
|编译器错误 C3471|新模块名称*名称*（在命令行上设置）与以前的名称*名称*冲突|
|编译器错误 C3472|新输出文件名*文件名*（在命令行上设置）与以前的文件名*文件名*冲突|
|编译器错误 C3473|未指定任何输出路径名称或模块名称。|
|编译器错误 C3474|无法打开输出文件 "*filename*"|
|编译器错误 C3475|输入文件 "*filename*" 中有语法错误|
|编译器错误 C3476|无法打开用于输入的文件 "*filename*"|
|编译器错误 C3477|lambda 不能出现在未计算的上下文中|
|编译器错误 C3478|"*identifier*"：无法通过复制捕获数组|
|编译器错误 C3479|Lambda 上的 SAL 注释不受支持|
|[编译器错误 C3480](compiler-error-c3480.md)|"*variable*"： lambda 捕获变量必须来自封闭函数范围|
|[编译器错误 C3481](compiler-error-c3481.md)|"*identifier*"：未找到 lambda 捕获变量|
|[编译器错误 C3482](compiler-error-c3482.md)|“this”只能在非静态成员函数中用作 lambda 捕获|
|[编译器错误 C3483](compiler-error-c3483.md)|"*identifier*" 已是 lambda 捕获列表的一部分|
|[编译器错误 C3484](compiler-error-c3484.md)|语法错误：返回类型前应为 "->"|
|[编译器错误 C3485](compiler-error-c3485.md)|lambda 定义不能包含任何 cv 限定符|
|编译器错误 C3486|已过时。|
|[编译器错误 C3487](compiler-error-c3487.md)|"*type*"：所有返回表达式必须推导为相同类型：以前为 "*type*"|
|[编译器错误 C3488](compiler-error-c3488.md)|默认捕获模式为按引用时，不允许使用 "&*标识符*"|
|[编译器错误 C3489](compiler-error-c3489.md)|默认捕获模式为复制时需要 "&*标识符*"|
|[编译器错误 C3490](compiler-error-c3490.md)|无法修改 "*identifier*"，因为正在通过 const 对象对其进行访问|
|[编译器错误 C3491](compiler-error-c3491.md)|"*identifier*"：不能在非可变 lambda 中修改按复制捕获|
|[编译器错误 C3492](compiler-error-c3492.md)|"*identifier*"：不能捕获匿名联合的成员|
|[编译器错误 C3493](compiler-error-c3493.md)|无法隐式捕获 "*identifier*"，因为尚未指定默认捕获模式|
|编译器错误 C3494|无法显式捕获 "this"，因为封闭的捕获模式不允许使用它|
|[编译器错误 C3495](compiler-error-c3495.md)|"*identifier*"：捕获中的标识符必须是带有自动存储持续时间的变量（在 lambda 的到达范围内声明）|
|[编译器错误 C3496](compiler-error-c3496.md)|“this”始终按值捕获: 已忽略“&”|
|编译器错误 C3497|无法构造 lambda 实例|
|[编译器错误 C3498](compiler-error-c3498.md)|"*identifier*"：无法捕获具有托管/WinRT 类型的变量|
|[编译器错误 C3499](compiler-error-c3499.md)|已指定返回类型为 void 的 lambda 无法返回值|

## <a name="see-also"></a>另请参阅

[C/C++编译器和生成工具错误和警告](../compiler-errors-1/c-cpp-build-errors.md) \
[编译器错误 C2000-C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
