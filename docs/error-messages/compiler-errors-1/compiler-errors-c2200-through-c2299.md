---
title: "编译器错误 C2200 到 C2299 |Microsoft 文档"
ms.custom: 
ms.date: 11/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2202
- C2209
- C2210
- C2211
- C2214
- C2215
- C2221
- C2225
- C2230
- C2235
- C2237
- C2239
- C2240
- C2257
- C2260
- C2263
- C2265
- C2269
- C2278
- C2281
- C2282
- C2288
- C2291
- C2294
helpviewer_keywords:
- C2202
- C2209
- C2210
- C2211
- C2214
- C2215
- C2221
- C2225
- C2230
- C2235
- C2237
- C2239
- C2240
- C2257
- C2260
- C2263
- C2265
- C2269
- C2278
- C2281
- C2282
- C2288
- C2291
- C2294
dev_langs: C++
ms.assetid: 9b36d11b-9510-4390-96f1-0c9235124d14
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 76de03030f61e56acd2189679704ff939e6e9c8c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-errors-c2200-through-c2299"></a>编译器错误 C2200 到 C2299

本部分中的文档的文章说明由编译器生成的错误消息的子集。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>错误消息

|Error|消息|
|-----------|-------------|
|[编译器错误 C2200](compiler-error-c2200.md)|*函数*： 已定义函数|
|[编译器错误 C2201](compiler-error-c2201.md)|*标识符*： 必须拥有才能导出/导入的外部链接|
|编译器错误 C2202|*函数*： 并非所有控制路径都返回值|
|[编译器错误 C2203](compiler-error-c2203.md)|删除运算符不能指定数组的边界|
|[编译器错误 C2204](compiler-error-c2204.md)|*类型*： 在括号内找到的类型定义|
|[编译器错误 C2205](compiler-error-c2205.md)|*标识符*： 无法初始化具有块范围的外部变量|
|[编译器错误 C2206](compiler-error-c2206.md)|*函数*: typedef 不能用于函数定义|
|[编译器错误 C2207](compiler-error-c2207.md)|*成员*： 类模板的成员无法获取函数类型|
|[编译器错误 C2208](compiler-error-c2208.md)|*类型*： 没有定义使用此类型的成员|
|编译器错误 C2209|*标识符*： 不能在构造函数声明中使用别名|
|编译器错误 C2210|*标识符*： 包扩展不能用作别名模板中的非打包参数的变量|
|编译器错误 C2211|从具有公共析构函数的 ref 类派生的 ref 类中的非虚拟析构函数也必须是公共|
|[编译器错误 C2212](compiler-error-c2212.md)|*标识符*： 不 __based 可用于指向函数的指针|
|[编译器错误 C2213](compiler-error-c2213.md)|*标识符*： 非法的自变量以 __based|
|编译器错误 C2214|基于 void 的指针需要使用： >|
|编译器错误 C2215|*关键字*不能与使用 / 体系结构： SSE|
|[编译器错误 C2216](compiler-error-c2216.md)|*keyword1*不能与使用*keyword2*|
|[编译器错误 C2217](compiler-error-c2217.md)|*attribute1*要求*attribute2*|
|[编译器错误 C2218](compiler-error-c2218.md)|*calltype*不能与使用 / /arch: IA32|
|[编译器错误 C2219](compiler-error-c2219.md)|语法错误： 必须晚于类型限定符 *|
|[编译器错误 C2220](compiler-error-c2220.md)|警告视为错误-不*filetype*生成文件|
|编译器错误 C2221|已过时。|
|[编译器错误 C2222](compiler-error-c2222.md)|意外的类型*类型*： 应输入基类或成员|
|[编译器错误 C2223](compiler-error-c2223.md)|左侧的->*标识符*必须指向结构/联合|
|[编译器错误 C2224](compiler-error-c2224.md)|左侧的。*标识符*必须具有结构/联合类型|
|编译器错误 C2225|已过时。|
|[编译器错误 C2226](compiler-error-c2226.md)|语法错误： 意外的类型*类型*|
|[编译器错误 C2227](compiler-error-c2227.md)|左侧的->*标识符*必须指向类/结构/联合/泛型类型|
|[编译器错误 C2228](compiler-error-c2228.md)|左侧的。*标识符*必须有类/结构/联合|
|[编译器错误 C2229](compiler-error-c2229.md)|类/结构/联合*类型*具有非法大小为零的数组|
|编译器错误 C2230|找不到模块*名称*|
|[编译器错误 C2231](compiler-error-c2231.md)|'.*标识符*： 左操作数指向类/结构/联合，使用->|
|[编译器错误 C2232](compiler-error-c2232.md)|->*标识符*： 左的操作数具有类/结构/联合类型，使用。|
|[编译器错误 C2233](compiler-error-c2233.md)|*标识符*： 包含大小为零数组的对象的数组是非法的|
|[编译器错误 C2234](compiler-error-c2234.md)|*标识符*： 数组的引用是非法|
|编译器错误 C2235|已过时。|
|[编译器错误 C2236](compiler-error-c2236.md)|意外的标记*令牌*。 你是否忘了“;”？|
|编译器错误 C2237|多个模块声明|
|[编译器错误 C2238](compiler-error-c2238.md)|前面的意外的标记*令牌*|
|编译器错误 C2239|*函数*': 尝试删除 __declspec （dllexport） 函数|
|编译器错误 C2240|已过时。|
|[编译器错误 C2241](compiler-error-c2241.md)|*标识符*： 成员访问受限制|
|[编译器错误 C2242](compiler-error-c2242.md)|typedef 名不能位于类/结构/联合之后|
|[编译器错误 C2243](compiler-error-c2243.md)|*conversion_type*： 从转换*type1*到*type2*存在，但无法访问|
|[编译器错误 C2244](compiler-error-c2244.md)|*标识符*： 无法匹配函数定义与现有的声明|
|[编译器错误 C2245](compiler-error-c2245.md)|不存在的成员函数*函数*指定为友元 （成员函数签名不匹配任何重载）|
|[编译器错误 C2246](compiler-error-c2246.md)|*标识符*： 局部定义的类中的非法静态数据成员|
|[编译器错误 C2247](compiler-error-c2247.md)|*标识符*无法访问因为*class1*使用*说明符*要从中继承*class2*|
|[编译器错误 C2248](compiler-error-c2248.md)|*标识符*： 无法访问*可访问性**成员*中类的声明*类*|
|[编译器错误 C2249](compiler-error-c2249.md)|*标识符*： 没有可访问路径*可访问性**成员*声明中虚拟基*类*|
|[编译器错误 C2250](compiler-error-c2250.md)|*标识符*： 不明确的继承*类*::*成员*|
|[编译器错误 C2251](compiler-error-c2251.md)|命名空间*命名空间*不具有成员*标识符*-您的意思*成员*？|
|[编译器错误 C2252](compiler-error-c2252.md)|模板的显式实例化时，才进行命名空间范围处|
|[编译器错误 C2253](compiler-error-c2253.md)|*函数*： 纯说明符或抽象重写说明符仅允许对虚拟函数|
|[编译器错误 C2254](compiler-error-c2254.md)|*函数*： 纯说明符或抽象重写说明符不允许对友元函数|
|[编译器错误 C2255](compiler-error-c2255.md)|*元素*： 不允许在类定义之外|
|[编译器错误 C2256](compiler-error-c2256.md)|上的友元说明符非法使用*函数*|
|编译器错误 C2257|*说明符*： 不允许在尾随返回类型说明符|
|[编译器错误 C2258](compiler-error-c2258.md)|非法的纯语法，必须为“= 0”|
|[编译器错误 C2259](compiler-error-c2259.md)|*类*： 无法实例化的抽象类|
|编译器错误 C2260|*说明符*': 无效 InternalsVisibleToAttribute 友元程序集说明符|
|[编译器错误 C2261](compiler-error-c2261.md)|*字符串*： 程序集引用无效，无法解析|
|[编译器错误 C2262](compiler-error-c2262.md)|*说明符*： 为 InternalsVisibleTo 声明不能具有指定的版本、 区域性或处理器体系结构|
|编译器错误 C2263|已过时。|
|[编译器错误 C2264](compiler-error-c2264.md)|*函数*： 函数定义或声明中的错误; 不会调用的函数|
|编译器错误 C2265|已过时。|
|[编译器错误 C2266](compiler-error-c2266.md)|*标识符*： 对非常量绑定数组的引用是非法的|
|[编译器错误 C2267](compiler-error-c2267.md)|*函数*： 具有块范围的静态函数是非法的|
|[编译器错误 C2268](compiler-error-c2268.md)|*函数*是编译器预定义的库帮助器。 不要使用 /GL。 不支持库帮助器编译对象文件*filename*不要使用 /gl。|
|编译器错误 C2269|无法创建的指针或引用为限定的函数类型 （需要指向成员的指针）|
|[编译器错误 C2270](compiler-error-c2270.md)|*函数*： 非成员函数上不允许的修饰符|
|[编译器错误 C2271](compiler-error-c2271.md)|*函数*： 新/删除不能具有形参列表修饰符|
|[编译器错误 C2272](compiler-error-c2272.md)|*函数*： 静态成员函数上不允许的修饰符|
|[编译器错误 C2273](compiler-error-c2273.md)|*类型*:-> 运算符右边非法|
|[编译器错误 C2274](compiler-error-c2274.md)|*类型*： 非法作为右侧。 运算符|
|[编译器错误 C2275](compiler-error-c2275.md)|*类型*： 非法使用此类型作为表达式|
|[编译器错误 C2276](compiler-error-c2276.md)|*运算符*： 非法操作绑定的成员函数表达式|
|[编译器错误 C2277](compiler-error-c2277.md)|*函数*： 不能采用该成员函数的地址|
|编译器错误 C2278|已过时。|
|[编译器错误 C2279](compiler-error-c2279.md)|异常规范不能出现在 typedef 声明|
|[编译器错误 C2280](compiler-error-c2280.md)|*类*::*函数*': 尝试引用已删除的函数|
|编译器错误 C2281|*类*::*函数*： 函数只能在第一个声明中删除|
|编译器错误 C2282|*function1*不能重写*function2*|
|[编译器错误 C2283](compiler-error-c2283.md)|*标识符*： 纯说明符或抽象重写说明符不允许对未命名类/结构|
|编译器错误 C2284|*函数*： 非法的自变量的内部函数，参数*数*|
|[编译器错误 C2285](compiler-error-c2285.md)|已确定指针为成员表示形式-忽略杂注|
|[编译器错误 C2286](compiler-error-c2286.md)|指向成员的*标识符*表示已设置为*继承*-忽略声明|
|[编译器错误 C2287](compiler-error-c2287.md)|*标识符*： 继承表示形式:*inheritiance*is 不太常规比所需*继承*|
|编译器错误 C2288|已过时。|
|[编译器错误 C2289](compiler-error-c2289.md)|多次使用同一类型限定符|
|[编译器错误 C2290](compiler-error-c2290.md)|忽略 c + + asm 语法。 使用__asm。|
|编译器错误 C2291|无法导出一个匿名命名空间。|
|[编译器错误 C2292](compiler-error-c2292.md)|*标识符*： 最佳情况下继承表示形式： *inheritance1*声明，但*inheritance2*所需|
|[编译器错误 C2293](compiler-error-c2293.md)|*标识符*： 非法的成员变量作为 __based 说明符|
|编译器错误 C2294|无法导出符号*标识符*因为它具有内部链接|
|[编译器错误 C2295](compiler-error-c2295.md)|转义*字符*： 在宏定义中非法|
|[编译器错误 C2296](compiler-error-c2296.md)|*运算符*： 非法的左操作数具有类型*类型*|
|[编译器错误 C2297](compiler-error-c2297.md)|*运算符*： 非法、 右操作数具有类型*类型*|
|[编译器错误 C2298](compiler-error-c2298.md)|缺少绑定到成员函数的指针的调用|
|[编译器错误 C2299](compiler-error-c2299.md)|*函数*： 行为更改： 显式专用化不能是复制构造函数或复制赋值运算符|
