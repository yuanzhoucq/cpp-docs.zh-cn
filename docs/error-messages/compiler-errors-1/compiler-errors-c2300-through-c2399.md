---
title: "编译器错误 s C2300 Through C2399 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
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
dev_langs:
- C++
ms.assetid: 07ca45b5-b2f0-4049-837b-40a7a3caed88
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 4bac7b2942f9d72674b8092dc7bf64174dd3c349
ms.openlocfilehash: 8d8925a68ffbb7ba607e37be8db5eca33300ef23
ms.lasthandoff: 04/24/2017

---
# <a name="compiler-errors-c2300-through-c2399"></a>编译器错误s C2300 Through C2399
文档的此部分中的文章包含有关 Visual C++ 编译器错误的子部分的信息。 可在此处访问信息，或者在 Visual Studio 中的“输出”  窗口中选择错误号，然后选择 F1 键。  
  
> [!NOTE]
>  不是每个[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]错误记录在 MSDN 中。 在许多情况下，诊断消息将提供的所有可用信息。 如果你认为某个错误消息需要更多说明，请通知我们。 你可以在此页上，使用反馈表单或转到 Visual Studio 中的菜单栏，然后选择**帮助**，**报告 Bug**，或可以在提交建议或 bug 报表[Microsoft Connect](http://connect.microsoft.com/VisualStudio)。  
  
 错误和警告的 MSDN 公共论坛，可能会发现更多帮助。 [Visual c + + 语言](http://go.microsoft.com/fwlink/?LinkId=158195)论坛是有关问题和讨论有关[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]语言语法和编译器。 [Visual c + + 常规](http://go.microsoft.com/fwlink/?LinkId=158194)论坛的问题是有关[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]其他论坛中未涉及。 你还可能上查找有关错误和警告的帮助[堆栈溢出](http://stackoverflow.com/)。  
  
|错误|消息|  
|-----------|-------------|  
|[编译器错误 C2300](compiler-error-c2300.md)|*类*︰ 类不具有析构函数调用 ~*类*|  
|[编译器错误 C2301](compiler-error-c2301.md)|左侧的-> ~*标识符*必须指向类/结构/联合|  
|[编译器错误 C2302](compiler-error-c2302.md)|左侧的。 ~*标识符*必须有类/结构/联合类型|  
|编译器错误 C2303|协同程序中不能使用结构化的异常处理|  
|编译器错误 C2304|*关键字*不能在 catch 块内使用|  
|编译器错误 C2305|*文件*不包含为此模块的调试信息|  
|编译器错误 C2306|*文件*不包含该模块的最新的调试信息|  
|[编译器错误 C2307](compiler-error-c2307.md)|杂注*指令*必须移动在函数之外，如果启用增量编译|  
|[编译器错误 C2308](compiler-error-c2308.md)|串联不匹配的字符串|  
|[编译器错误 C2309](compiler-error-c2309.md)|catch 处理程序需要带括号的异常声明|  
|[编译器错误 C2310](compiler-error-c2310.md)|catch 处理程序必须指定一种类型|  
|[编译器错误 C2311](compiler-error-c2311.md)|*类型*︰ 捕获了... 在行上*数*|  
|[编译器错误 C2312](compiler-error-c2312.md)|*type1*︰ 由捕获*type2*行上*数*|  
|[编译器错误 C2313](compiler-error-c2313.md)|*type1*︰ 由引用捕获 (*type2*) 在行上*数*|  
|编译器错误 C2314|关键字*keyword1*已弃用︰ 使用*keyword2*改为|  
|[编译器错误 C2315](compiler-error-c2315.md)|*type1*︰ 由引用捕获*type2*行上*数*|  
|[编译器错误 C2316](compiler-error-c2316.md)|*类型*︰ 无法作为析构函数和/或复制构造函数是不可访问或已删除捕获|  
|[编译器错误 C2317](compiler-error-c2317.md)|try 块行上启动*数*没有 catch 处理程序|  
|[编译器错误 C2318](compiler-error-c2318.md)|没有与该 catch 处理程序关联的 Try 块|  
|[编译器错误 C2319](compiler-error-c2319.md)|“try/catch”后面必须有复合语句。 缺少“{”|  
|[编译器错误 C2320](compiler-error-c2320.md)|预期: 遵循访问说明符*说明符*|  
|编译器错误 C2321|*标识符*是一个关键字，并且不能在此上下文中|  
|[编译器错误 C2322](compiler-error-c2322.md)|*标识符*: dllimport 地址*标识符*不是静态的|  
|编译器错误 C2323|*标识符*︰ 非成员运算符 new 或 delete 函数不能声明静态或全局命名空间之外的命名空间中|  
|[编译器错误 C2324](compiler-error-c2324.md)|*标识符*︰ 意外的右侧:: ~|  
|[编译器错误 C2325](compiler-error-c2325.md)|*type1*︰ 意外的类型，右侧的-> ~︰ 预期*type2*|  
|[编译器错误 C2326](compiler-error-c2326.md)|*声明符*︰ 函数无法访问*标识符*|  
|[编译器错误 C2327](compiler-error-c2327.md)|*标识符*︰ 不是类型名称、 静态、 或枚举器|  
|编译器错误 C2328|*关键字*︰ 尚不支持关键字|  
|编译器错误 C2329|*标识符*: __ptr64 不可用于指向函数的指针|  
|编译器错误 C2330|“implementation_key( )”只在由 #pragma start_map_region/stop_map_region 限定的区域中有效|  
|编译器错误 C2331|访问*标识符*现在定义为*1>*'，以前它被定义为'*accessibility2*|  
|[编译器错误 C2332](compiler-error-c2332.md)|*typedef*︰ 缺少标记名称|  
|[编译器错误 C2333](compiler-error-c2333.md)|*函数*︰ 函数声明中的存在错误; 跳过函数体|  
|[编译器错误 C2334](compiler-error-c2334.md)|前面的意外的标记*令牌*; 正在跳过明显函数体|  
|编译器错误 C2335|*标识符*: 类型不能引入函数参数列表中|  
|编译器错误 C2336|*类型*︰ 非法类型|  
|[编译器错误 C2337](compiler-error-c2337.md)|*属性*︰ 未找到属性|  
|[编译器错误 C2338](compiler-error-c2338.md)|*（来自外部提供程序的错误消息）*|  
|编译器错误 C2339|*标识符*︰ 嵌入 IDL 中的非法类型|  
|编译器错误 C2340|*标识符*': 'static' 只能在类定义|  
|[编译器错误 C2341](compiler-error-c2341.md)|*部分*︰ 必须使用 #pragma data_seg、 code_seg 或之前的部分，用于定义段|  
|编译器错误 C2342|语法错误: 类型限定符冲突|  
|编译器错误 C2343|*部分*︰ 冲突节特性|  
|[编译器错误 C2344](compiler-error-c2344.md)|对齐 (*数*): 对齐必须是 2 的幂|  
|[编译器错误 C2345](compiler-error-c2345.md)|对齐 (*数*): 非法的对齐值|  
|[编译器错误 C2346](compiler-error-c2346.md)|*函数*不能编译为本机:*说明*|  
|编译器错误 C2347|已过时。|  
|[编译器错误 C2348](compiler-error-c2348.md)|*类型*︰ 不是 C 样式聚合的不能嵌入的 IDL 中导出|  
|[编译器错误 C2349](compiler-error-c2349.md)|*函数*不能编译为托管:*说明*; 使用非托管的 #pragma|  
|[编译器错误 C2350](compiler-error-c2350.md)|*标识符*不是静态成员|  
|[编译器错误 C2351](compiler-error-c2351.md)|过时的 C++ 构造函数初始化语法|  
|[编译器错误 C2352](compiler-error-c2352.md)|*标识符*︰ 非静态成员函数的非法调用|  
|[编译器错误 C2353](compiler-error-c2353.md)|不允许使用异常规范|  
|编译器错误 C2354|已过时。|  
|[编译器错误 C2355](compiler-error-c2355.md)|“this”: 只能在非静态成员函数或非静态数据成员初始值设定项的内部引用|  
|[编译器错误 C2356](compiler-error-c2356.md)|初始化段在翻译单元期间不能更改|  
|[编译器错误 C2357](compiler-error-c2357.md)|*标识符*︰ 必须是类型的函数*类型*|  
|编译器错误 C2358|*标识符*︰ 不能在类定义之外定义的静态属性|  
|编译器错误 C2359|已过时。|  
|[编译器错误 C2360](compiler-error-c2360.md)|初始化*标识符*通过 case 标签跳过|  
|[编译器错误 C2361](compiler-error-c2361.md)|初始化*标识符*通过 default 标签跳过|  
|[编译器错误 C2362](compiler-error-c2362.md)|初始化*标识符*通过跳过 goto*标签*|  
|编译器错误 C2363|编译器内部函数的数字限制函数需要字符串文本参数|  
|[编译器错误 C2364](compiler-error-c2364.md)|*类型*︰ 非法类型的自定义特性|  
|[编译器错误 C2365](compiler-error-c2365.md)|*member1*︰ 重定义; 以前的定义已*member2*|  
|编译器错误 C2366|*标识符*︰ 重定义; 不同 implementation_key 说明符|  
|编译器错误 C2367|已过时。|  
|[编译器错误 C2368](compiler-error-c2368.md)|*标识符*︰ 重定义; 不同的分配说明符|  
|[编译器错误 C2369](compiler-error-c2369.md)|*标识符*︰ 重定义; 不同的下标|  
|[编译器错误 C2370](compiler-error-c2370.md)|*标识符*︰ 重定义; 不同的存储类|  
|[编译器错误 C2371](compiler-error-c2371.md)|*标识符*︰ 重定义; 不同的基类型|  
|[编译器错误 C2372](compiler-error-c2372.md)|*标识符*︰ 重定义; 不同类型的间接寻址|  
|[编译器错误 C2373](compiler-error-c2373.md)|*标识符*︰ 重定义; 不同的类型修饰符|  
|[编译器错误 C2374](compiler-error-c2374.md)|*标识符*︰ 重定义; 多次初始化|  
|[编译器错误 C2375](compiler-error-c2375.md)|*标识符*︰ 重定义; 不同的链接|  
|[编译器错误 C2376](compiler-error-c2376.md)|*标识符*︰ 重定义; 不同基础的分配|  
|[编译器错误 C2377](compiler-error-c2377.md)|*标识符*︰ 重定义; typedef 不能由任何其他符号重载|  
|[编译器错误 C2378](compiler-error-c2378.md)|*标识符*︰ 重定义; 符号不能使用 typedef 重载|  
|[编译器错误 C2379](compiler-error-c2379.md)|形参*数*具有不同的类型提升时|  
|[编译器错误 C2380](compiler-error-c2380.md)|前的类型*标识符*（构造函数的返回类型或当前的类名称非法重定义？）|  
|[编译器错误 C2381](compiler-error-c2381.md)|*标识符*︰ 重定义;__declspec （noreturn） 或 [[noreturn]] 不同|  
|[编译器错误 C2382](compiler-error-c2382.md)|*标识符*︰ 重定义; 不同的异常规范|  
|[编译器错误 C2383](compiler-error-c2383.md)|*标识符*︰ 默认自变量不能存在于此符号|  
|[编译器错误 C2384](compiler-error-c2384.md)|*成员*︰ 无法将 thread_local 或 __declspec （thread） 应用于托管/WinRT 类的成员|  
|[编译器错误 C2385](compiler-error-c2385.md)|不明确的访问*成员*|  
|[编译器错误 C2386](compiler-error-c2386.md)|*标识符*︰ 当前范围内已存在具有此名称的符号|  
|[编译器错误 C2387](compiler-error-c2387.md)|*标识符*︰ 不明确的基类|  
|[编译器错误 C2388](compiler-error-c2388.md)|*标识符*︰ 不能使用 __declspec(appdomain) 和 __declspec 声明符号|  
|[编译器错误 C2389](compiler-error-c2389.md)|*运算符*︰ 非法的操作数 nullptr|  
|[编译器错误 C2390](compiler-error-c2390.md)|*标识符*︰ 不正确的存储类*说明符*|  
|[编译器错误 C2391](compiler-error-c2391.md)|*标识符*︰ 在类型定义，无法使用 friend|  
|[编译器错误 C2392](compiler-error-c2392.md)|*member1*︰ 协变返回类型不支持在托管/WinRT 类型中，否则*member2*将被重写|  
|[编译器错误 C2393](compiler-error-c2393.md)|*符号*︰ 不能在段中分配每个 appdomain 符号*段*|  
|[编译器错误 C2394](compiler-error-c2394.md)|*类型*:: 运算符*运算符*: CLR/WinRT 运算符无效。 至少一个参数必须是以下类型的: ' T ^，' T ^ %，' T ^ &，其中 T =*类型*|  
|[编译器错误 C2395](compiler-error-c2395.md)|*类型*:: 运算符*运算符*: CLR/WinRT 运算符无效。 至少一个参数必须是以下类型的: ' T，无法 %，无法 （& a)，' T ^，' T ^ %，无法 ^ （& a)，其中 T =*类型*|  
|[编译器错误 C2396](compiler-error-c2396.md)|*type1*:: 运算符*type2*: CLR/WinRT 用户定义的转换函数无效。 必须转换自或转换为: ' T ^，' T ^ %，无法 ^ &，其中 T =*type1*|  
|[编译器错误 C2397](compiler-error-c2397.md)|从*type1*到*type2*需要收缩转换|  
|编译器错误 C2398|元素*数*︰ 从转换*type1*到*type2*需要收缩转换|  
|编译器错误 C2399|已过时。|  

