---
title: 编译器错误s C2300 Through C2399
ms.date: 11/17/2017
f1_keywords:
- C2303
- C2304
- C2305
- C2306
- C2314
- C2321
- C2323
- C2328
- C2329
- C2330
- C2331
- C2335
- C2336
- C2339
- C2340
- C2342
- C2343
- C2347
- C2354
- C2358
- C2359
- C2363
- C2366
- C2367
- C2398
- C2399
helpviewer_keywords:
- C2303
- C2304
- C2305
- C2306
- C2314
- C2321
- C2323
- C2328
- C2329
- C2330
- C2331
- C2335
- C2336
- C2339
- C2340
- C2342
- C2343
- C2347
- C2354
- C2358
- C2359
- C2363
- C2366
- C2367
- C2398
- C2399
ms.assetid: 07ca45b5-b2f0-4049-837b-40a7a3caed88
ms.openlocfilehash: 6f95ec90a08b842259a383d7bfc6af2cba119e14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580630"
---
# <a name="compiler-errors-c2300-through-c2399"></a>编译器错误s C2300 Through C2399

在本部分文档中的文章说明了由编译器生成的错误消息的子集。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>错误消息

|Error|消息|
|-----------|-------------|
|[编译器错误 C2300](compiler-error-c2300.md)|'*类*： 类没有调用析构函数 ~*类*|
|[编译器错误 C2301](compiler-error-c2301.md)|左侧的-> ~*标识符*必须指向类/结构/联合|
|[编译器错误 C2302](compiler-error-c2302.md)|左侧的。 ~*标识符*必须有类/结构/联合类型|
|编译器错误 C2303|不能是协同程序中使用结构化的异常处理|
|编译器错误 C2304|'*关键字*不能在 catch 块内使用|
|编译器错误 C2305|'*文件*不包含此模块的调试信息|
|编译器错误 C2306|'*文件*不包含此模块的最新调试信息|
|[编译器错误 C2307](compiler-error-c2307.md)|杂注*指令*必须移到函数外，如果启用增量编译|
|[编译器错误 C2308](compiler-error-c2308.md)|串联不匹配的字符串|
|[编译器错误 C2309](compiler-error-c2309.md)|catch 处理程序需要带括号的异常声明|
|[编译器错误 C2310](compiler-error-c2310.md)|catch 处理程序必须指定一种类型|
|[编译器错误 C2311](compiler-error-c2311.md)|'*类型*： 由...行上捕获*数*|
|[编译器错误 C2312](compiler-error-c2312.md)|'*type1*： 由捕获*type2*行上*数*|
|[编译器错误 C2313](compiler-error-c2313.md)|'*type1*： 由引用捕获 ('*type2*) 行上*数*|
|编译器错误 C2314|关键字 '*keyword1*已弃用： 使用'*keyword2*改为|
|[编译器错误 C2315](compiler-error-c2315.md)|'*type1*： 引用由捕获*type2*行上*数*|
|[编译器错误 C2316](compiler-error-c2316.md)|'*类型*： 不能被捕获，因为析构函数和/或复制构造函数是不可访问或已删除|
|[编译器错误 C2317](compiler-error-c2317.md)|try 行上开始块 '*数*没有 catch 处理程序|
|[编译器错误 C2318](compiler-error-c2318.md)|没有与该 catch 处理程序关联的 Try 块|
|[编译器错误 C2319](compiler-error-c2319.md)|“try/catch”后面必须有复合语句。 缺少“{”|
|[编译器错误 C2320](compiler-error-c2320.md)|预期: 若要按照访问说明符*说明符*|
|编译器错误 C2321|'*标识符*是关键字，并且不能在此上下文中使用|
|[编译器错误 C2322](compiler-error-c2322.md)|'*标识符*: dllimport 地址'*标识符*不是静态的|
|编译器错误 C2323|'*标识符*： 非成员运算符 new 或 delete 函数不能声明静态或全局命名空间之外的命名空间中|
|[编译器错误 C2324](compiler-error-c2324.md)|'*标识符*： 意外右侧的:: ~'|
|[编译器错误 C2325](compiler-error-c2325.md)|'*type1*： 意外的类型右侧的-> ~： 预期*type2*|
|[编译器错误 C2326](compiler-error-c2326.md)|'*声明符*： 函数无法访问'*标识符*|
|[编译器错误 C2327](compiler-error-c2327.md)|'*标识符*： 不是类型名称、 静态或枚举器|
|编译器错误 C2328|'*关键字*： 尚不支持关键字|
|编译器错误 C2329|'*标识符*: __ptr64 不可用于指向函数的指针|
|编译器错误 C2330|implementation_key （） 才受 #pragma start_map_region/stop_map_region 限定的区域中有效|
|编译器错误 C2331|访问权限*标识符*现在定义为'*1>*'，以前它被定义为'*accessibility2*|
|[编译器错误 C2332](compiler-error-c2332.md)|'*typedef*： 缺少标记名称|
|[编译器错误 C2333](compiler-error-c2333.md)|'*函数*： 函数声明中的错误; 跳过函数体|
|[编译器错误 C2334](compiler-error-c2334.md)|前面有意外的标记*令牌*; 正在跳过明显的函数体|
|编译器错误 C2335|'*标识符*： 不能在函数参数列表中引入一种类型|
|编译器错误 C2336|'*类型*： 非法类型|
|[编译器错误 C2337](compiler-error-c2337.md)|'*特性*： 未找到特性|
|[编译器错误 C2338](compiler-error-c2338.md)|*（从外部提供程序的错误消息）*|
|编译器错误 C2339|'*标识符*： 嵌入的 IDL 中的非法类型|
|编译器错误 C2340|'*标识符*: static 只能在类定义中|
|[编译器错误 C2341](compiler-error-c2341.md)|'*部分*： 必须使用 #pragma data_seg、 code_seg 或部分之前，若要使用定义段|
|编译器错误 C2342|语法错误： 类型限定符冲突|
|编译器错误 C2343|'*部分*： 节特性冲突|
|[编译器错误 C2344](compiler-error-c2344.md)|对齐 (*数*): 对齐必须是 2 的幂|
|[编译器错误 C2345](compiler-error-c2345.md)|对齐 (*数*): 非法的对齐值|
|[编译器错误 C2346](compiler-error-c2346.md)|'*函数*不能编译为本机:'*说明*|
|编译器错误 C2347|已过时。|
|[编译器错误 C2348](compiler-error-c2348.md)|'*类型*： 不是 C 样式聚合，不能嵌入的 IDL 中导出|
|[编译器错误 C2349](compiler-error-c2349.md)|'*函数*不能编译为托管:'*说明*; 使用非托管的 #pragma|
|[编译器错误 C2350](compiler-error-c2350.md)|'*标识符*不是静态成员|
|[编译器错误 C2351](compiler-error-c2351.md)|已过时的 c + + 构造函数初始化语法|
|[编译器错误 C2352](compiler-error-c2352.md)|'*标识符*： 非静态成员函数的非法调用|
|[编译器错误 C2353](compiler-error-c2353.md)|异常规范不允许|
|编译器错误 C2354|已过时。|
|[编译器错误 C2355](compiler-error-c2355.md)|this： 只能在非静态成员函数或非静态数据成员初始值设定项内部引用|
|[编译器错误 C2356](compiler-error-c2356.md)|初始化段在翻译单元期间不能更改|
|[编译器错误 C2357](compiler-error-c2357.md)|'*标识符*： 必须是类型的函数*类型*|
|编译器错误 C2358|'*标识符*： 不能在类定义之外定义的静态属性|
|编译器错误 C2359|已过时。|
|[编译器错误 C2360](compiler-error-c2360.md)|初始化*标识符*通过 case 标签跳过|
|[编译器错误 C2361](compiler-error-c2361.md)|初始化*标识符*跳过了 default 标签|
|[编译器错误 C2362](compiler-error-c2362.md)|初始化*标识符*通过跳过 goto*标签*|
|编译器错误 C2363|编译器内部数字限制函数需要字符串字面量参数|
|[编译器错误 C2364](compiler-error-c2364.md)|'*类型*： 自定义特性的非法类型|
|[编译器错误 C2365](compiler-error-c2365.md)|'*member1*： 重定义; 以前的定义是*member2*|
|编译器错误 C2366|'*标识符*： 重定义; 不同的 implementation_key 说明符|
|编译器错误 C2367|已过时。|
|[编译器错误 C2368](compiler-error-c2368.md)|'*标识符*： 重定义; 不同的分配说明符|
|[编译器错误 C2369](compiler-error-c2369.md)|'*标识符*： 重定义; 不同的下标|
|[编译器错误 C2370](compiler-error-c2370.md)|'*标识符*： 重定义; 不同的存储类|
|[编译器错误 C2371](compiler-error-c2371.md)|'*标识符*： 重定义; 不同的基类型|
|[编译器错误 C2372](compiler-error-c2372.md)|'*标识符*： 重定义; 不同类型的间接寻址|
|[编译器错误 C2373](compiler-error-c2373.md)|'*标识符*： 重定义; 不同的类型修饰符|
|[编译器错误 C2374](compiler-error-c2374.md)|'*标识符*： 重定义; 多次初始化|
|[编译器错误 C2375](compiler-error-c2375.md)|'*标识符*： 重定义; 不同的链接|
|[编译器错误 C2376](compiler-error-c2376.md)|'*标识符*： 重定义; 不同基础的分配|
|[编译器错误 C2377](compiler-error-c2377.md)|'*标识符*： 重定义; typedef 不能与任何其他符号重载|
|[编译器错误 C2378](compiler-error-c2378.md)|'*标识符*： 重定义; 符号不能使用 typedef 重载|
|[编译器错误 C2379](compiler-error-c2379.md)|形参*数*具有不同的类型提升时|
|[编译器错误 C2380](compiler-error-c2380.md)|前的类型*标识符*（构造函数的返回类型或当前类名的非法重定义？）|
|[编译器错误 C2381](compiler-error-c2381.md)|'*标识符*： 重定义;__declspec （noreturn） 或 [[noreturn]] 不同|
|[编译器错误 C2382](compiler-error-c2382.md)|'*标识符*： 重定义; 不同的异常规范|
|[编译器错误 C2383](compiler-error-c2383.md)|'*标识符*： 此符号上不允许使用默认自变量|
|[编译器错误 C2384](compiler-error-c2384.md)|'*成员*： 不能对托管/WinRT 类的成员应用 thread_local 或 __declspec （thread）|
|[编译器错误 C2385](compiler-error-c2385.md)|访问不明确的 '*成员*|
|[编译器错误 C2386](compiler-error-c2386.md)|'*标识符*： 当前范围内已存在具有此名称的符号|
|[编译器错误 C2387](compiler-error-c2387.md)|'*标识符*： 不明确的基类|
|[编译器错误 C2388](compiler-error-c2388.md)|'*标识符*： 不能具有 __declspec 和 __declspec （process） 声明一个符号|
|[编译器错误 C2389](compiler-error-c2389.md)|'*运算符*： 非法的操作数 nullptr|
|[编译器错误 C2390](compiler-error-c2390.md)|'*标识符*： 不正确的存储类*说明符*|
|[编译器错误 C2391](compiler-error-c2391.md)|'*标识符*: friend 不能在类型定义过程|
|[编译器错误 C2392](compiler-error-c2392.md)|'*member1*： 协变返回类型不支持在托管/WinRT 类型中，否则'*member2*将被重写|
|[编译器错误 C2393](compiler-error-c2393.md)|'*符号*： 不能在段中分配 per-appdomain 符号*段*|
|[编译器错误 C2394](compiler-error-c2394.md)|'*类型*:: 运算符*运算符*: CLR/WinRT 运算符无效。 至少一个参数必须是以下类型的: ' T ^，' T ^ %，' T ^ &，其中 T =*类型*|
|[编译器错误 C2395](compiler-error-c2395.md)|'*类型*:: 运算符*运算符*: CLR/WinRT 运算符无效。 至少一个参数必须是以下类型的： 不，不 %，不 &，' T ^，不 ^ %，' T ^ &，其中 T =*类型*|
|[编译器错误 C2396](compiler-error-c2396.md)|'*type1*:: 运算符*type2*: CLR/WinRT 用户定义的转换函数无效。 必须转换自或转换为: ' T ^，' T ^ %，' T ^ &，其中 T =*type1*|
|[编译器错误 C2397](compiler-error-c2397.md)|从转换*type1*到*type2*需要收缩转换|
|编译器错误 C2398|元素*数量*： 从转换*type1*to*type2*需要收缩转换|
|编译器错误 C2399|已过时。|
