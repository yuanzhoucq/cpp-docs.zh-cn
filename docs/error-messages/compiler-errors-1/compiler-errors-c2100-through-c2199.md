---
title: "编译器错误 s C2100 through C2199 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2119
- C2123
- C2125
- C2126
- C2127
- C2131
- C2136
- C2176
- C2187
- C2189
helpviewer_keywords:
- C2119
- C2123
- C2125
- C2126
- C2127
- C2131
- C2136
- C2176
- C2187
- C2189
dev_langs:
- C++
ms.assetid: 1ccab076-0954-4386-b959-d3112a6793ae
caps.latest.revision: 12
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: c724fd7907f7ec3f0ce8f096faf88d4ec66ae970
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---
# <a name="compiler-errors-c2100-through-c2199"></a>编译器错误s C2100 through C2199
文档的此部分中的文章包含有关 Visual C++ 编译器错误的子部分的信息。 可在此处访问信息，或者在 Visual Studio 中的“输出”  窗口中选择错误号，然后选择 F1 键。  
  
> [!NOTE]
>  不是每个[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]错误记录在 MSDN 中。 在许多情况下，诊断消息将提供的所有可用信息。 如果你认为某个错误消息需要更多说明，请通知我们。 你可以在此页上，使用反馈表单或转到 Visual Studio 中的菜单栏，然后选择**帮助**，**报告 Bug**，或可以在提交建议或 bug 报表[Microsoft Connect](http://connect.microsoft.com/VisualStudio)。  
  
 错误和警告的 MSDN 公共论坛，可能会发现更多帮助。 [Visual c + + 语言](http://go.microsoft.com/fwlink/?LinkId=158195)论坛是有关问题和讨论有关[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]语言语法和编译器。 [Visual c + + 常规](http://go.microsoft.com/fwlink/?LinkId=158194)论坛的问题是有关[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]其他论坛中未涉及。 你还可能上查找有关错误和警告的帮助[堆栈溢出](http://stackoverflow.com/)。  
  
|错误|消息|  
|-----------|-------------|  
|[编译器错误 C2100](compiler-error-c2100.md)|非法的间接寻址|  
|[编译器错误 C2101](compiler-error-c2101.md)|常量上的“&”|  
|[编译器错误 C2102](compiler-error-c2102.md)|"&" 要求左值|  
|[编译器错误 C2103](compiler-error-c2103.md)|寄存器变量上的“&”|  
|[编译器错误 C2104](compiler-error-c2104.md)|位域上的“&”被忽略|  
|[编译器错误 C2105](compiler-error-c2105.md)|*运算符*需要左值|  
|[编译器错误 C2106](compiler-error-c2106.md)|*运算符*︰ 左的操作数必须为左值|  
|[编译器错误 C2107](compiler-error-c2107.md)|非法索引，不允许间接寻址|  
|[编译器错误 C2108](compiler-error-c2108.md)|下标不是整型|  
|[编译器错误 C2109](compiler-error-c2109.md)|下标要求数组或指针类型|  
|[编译器错误 C2110](compiler-error-c2110.md)|+︰ 无法添加两个指针|  
|[编译器错误 C2111](compiler-error-c2111.md)|+︰ 指针加法要求整型操作数|  
|[编译器错误 C2112](compiler-error-c2112.md)|-︰ 指针减法要求整型或指针操作数|  
|[编译器错误 C2113](compiler-error-c2113.md)|-︰ 指针只能从另一个指针上进行减法运算|  
|[编译器错误 C2114](compiler-error-c2114.md)|*运算符*︰ 左侧指针; 需要右侧的整数值|  
|[编译器错误 C2115](compiler-error-c2115.md)|*运算符*︰ 不兼容的类型|  
|[编译器错误 C2116](compiler-error-c2116.md)|函数参数列表有差异|  
|[编译器错误 C2117](compiler-error-c2117.md)|*标识符*︰ 数组界限溢出|  
|[编译器错误 C2118](compiler-error-c2118.md)|负下标|  
|编译器错误 C2119|*标识符*: 类型 '*类型*无法从空初始值设定项推导|  
|[编译器错误 C2120](compiler-error-c2120.md)|对于所有类型“void”非法|  
|[编译器错误 C2121](compiler-error-c2121.md)|“#”: 无效字符 : 可能是宏扩展的结果|  
|[编译器错误 C2122](compiler-error-c2122.md)|*标识符*︰ 原型中的参数名称列表非法|  
|编译器错误 C2123|*标识符*︰ 别名模板不能显式或部分专用|  
|[编译器错误 C2124](compiler-error-c2124.md)|被零除或对零求模|  
|编译器错误 C2125|constexpr 不符合*令牌*|  
|编译器错误 C2126|*标识符*不能使用 constexpr 说明符声明|  
|编译器错误 C2127|*标识符*︰ 具有非常量表达式的 constexpr 实体的初始化非法|  
|[编译器错误 C2128](compiler-error-c2128.md)|*函数*: alloc_text/same_seg 仅适用于带 C 链接的函数|  
|[编译器错误 C2129](compiler-error-c2129.md)|静态函数*标识符*声明但未定义|  
|[编译器错误 C2130](compiler-error-c2130.md)|#line 应包含文件名，却找到的字符串*令牌*|  
|编译器错误 C2131|表达式的计算结果不是常数|  
|[编译器错误 C2132](compiler-error-c2132.md)|语法错误: 意外的标识符|  
|[编译器错误 C2133](compiler-error-c2133.md)|*标识符*': 未知的大小|  
|[编译器错误 C2134](compiler-error-c2134.md)|*函数*︰ 调用不会导致常量表达式|  
|[编译器错误 C2135](compiler-error-c2135.md)|*运算符*︰ 非法的位域操作|  
|编译器错误 C2136|不允许创作 API 合同|  
|[编译器错误 C2137](compiler-error-c2137.md)|空字符常量|  
|[编译器错误 C2138](compiler-error-c2138.md)|定义没有任何成员的枚举是非法的|  
|[编译器错误 C2139](compiler-error-c2139.md)|*类*︰ 未定义的类不允许作为编译器内部类型特征的自变量*特征*|  
|[编译器错误 C2140](compiler-error-c2140.md)|*类型*︰ 依赖于泛型类型参数的类型不允许作为编译器内部类型特征的自变量*特征*|  
|[编译器错误 C2141](compiler-error-c2141.md)|数组大小溢出|  
|[编译器错误 C2142](compiler-error-c2142.md)|函数声明有差异，只在一个声明中指定了变量参数|  
|[编译器错误 C2143](compiler-error-c2143.md)|语法错误︰ 缺少*token1*before*token2*|  
|[编译器错误 C2144](compiler-error-c2144.md)|语法错误:*类型*前面应带有*token2*|  
|[编译器错误 C2145](compiler-error-c2145.md)|语法错误︰ 缺少*令牌*标识符的前面|  
|[编译器错误 C2146](compiler-error-c2146.md)|语法错误︰ 缺少*令牌*before identifier*标识符*|  
|[编译器错误 C2147](compiler-error-c2147.md)|语法错误:*令牌*是一个新的关键字|  
|[编译器错误 C2148](compiler-error-c2148.md)|数组的总大小不能超过 0x*值*字节|  
|[编译器错误 C2149](compiler-error-c2149.md)|*标识符*︰ 已命名的位域不能具有零宽度|  
|[编译器错误 C2150](compiler-error-c2150.md)|*标识符*︰ 位域必须具有类型 int、 signed 的 int 或 unsigned 的 int|  
|[编译器错误 C2151](compiler-error-c2151.md)|语言特性多于一个|  
|[编译器错误 C2152](compiler-error-c2152.md)|*标识符*︰ 指向具有不同的属性的函数的指针|  
|[编译器错误 C2153](compiler-error-c2153.md)|整数文本必须至少具有一位数|  
|[编译器错误 C2154](compiler-error-c2154.md)|*类型*︰ 只有枚举类型才允许作为编译器内部类型特征的自变量*特征*|  
|[编译器错误 C2155](compiler-error-c2155.md)|“?”: 左边的操作数无效，应使用算术类型或指针类型|  
|[编译器错误 C2156](compiler-error-c2156.md)|杂注必须在函数的外部|  
|[编译器错误 C2157](compiler-error-c2157.md)|*标识符*︰ 必须先声明才能用于杂注列表|  
|[编译器错误 C2158](compiler-error-c2158.md)|*类型*︰ 本机非模板类型才当前支持 #pragma make_public 指令|  
|[编译器错误 C2159](compiler-error-c2159.md)|指定了一个以上的存储类|  
|[编译器错误 C2160](compiler-error-c2160.md)|“##”不能在宏定义的开始处出现|  
|[编译器错误 C2161](compiler-error-c2161.md)|“##”不能在宏定义的结尾处出现|  
|[编译器错误 C2162](compiler-error-c2162.md)|应输入宏形参|  
|[编译器错误 C2163](compiler-error-c2163.md)|*函数*︰ 不可用作内部函数|  
|[编译器错误 C2164](compiler-error-c2164.md)|*函数*︰ 未声明的内部函数|  
|[编译器错误 C2165](compiler-error-c2165.md)|*修饰符*︰ 不能修改指向数据|  
|[编译器错误 C2166](compiler-error-c2166.md)|左值指定 const 对象|  
|[编译器错误 C2167](compiler-error-c2167.md)|*函数*︰ 内部函数的实参太多|  
|[编译器错误 C2168](compiler-error-c2168.md)|*函数*︰ 内部函数的实参太少|  
|[编译器错误 C2169](compiler-error-c2169.md)|*函数*︰ 不能定义内部函数|  
|[编译器错误 C2170](compiler-error-c2170.md)|*标识符*︰ 未声明为函数，不能为内部函数|  
|[编译器错误 C2171](compiler-error-c2171.md)|*运算符*︰ 类型的操作数非法*类型*|  
|[编译器错误 C2172](compiler-error-c2172.md)|*函数*︰ 实参不是指针︰ 参数*数*|  
|[编译器错误 C2173](compiler-error-c2173.md)|*函数*︰ 实参不是指针︰ 参数*数*，参数列表*数*|  
|[编译器错误 C2174](compiler-error-c2174.md)|*函数*︰ 实参具有类型 void︰ 参数*数*，参数列表*数*|  
|[编译器错误 C2175](compiler-error-c2175.md)|*区域设置*': 无效的区域设置|  
|编译器错误 C2176|不能在与构造函数关联的函数 try 块的处理程序中使用 return 语句|  
|[编译器错误 C2177](compiler-error-c2177.md)|常量太大|  
|[编译器错误 C2178](compiler-error-c2178.md)|*标识符*不能使用声明*说明符*说明符|  
|[编译器错误 C2179](compiler-error-c2179.md)|*类型*︰ 特性自变量不能使用类型参数|  
|[编译器错误 C2180](compiler-error-c2180.md)|控制表达式具有类型*类型*|  
|[编译器错误 C2181](compiler-error-c2181.md)|没有匹配 if 的非法 else|  
|[编译器错误 C2182](compiler-error-c2182.md)|*标识符*︰ 非法使用 void 类型|  
|[编译器错误 C2183](compiler-error-c2183.md)|语法错误: 翻译单元为空|  
|[编译器错误 C2184](compiler-error-c2184.md)|*类型*: __except 表达式而言为非法类型|  
|[编译器错误 C2185](compiler-error-c2185.md)|*标识符*︰ 非法基于分配|  
|[编译器错误 C2186](compiler-error-c2186.md)|*运算符*: void 类型的操作数非法|  
|编译器错误 C2187|语法错误:*令牌*此处是异常|  
|[编译器错误 C2188](compiler-error-c2188.md)|*数*︰ 对宽字符来说太大|  
|编译器错误 C2189|alignas 属性不能应用于位域、 函数参数、 异常声明，或与声明的变量注册存储类|  
|[编译器错误 C2190](compiler-error-c2190.md)|第一个参数列表比第二个长|  
|[编译器错误 C2191](compiler-error-c2191.md)|第二个参数列表比第一个长|  
|[编译器错误 C2192](compiler-error-c2192.md)|参数*数*不同的声明|  
|[编译器错误 C2193](compiler-error-c2193.md)|*标识符*︰ 已在一段|  
|[编译器错误 C2194](compiler-error-c2194.md)|*标识符*︰ 是的文本段|  
|[编译器错误 C2195](compiler-error-c2195.md)|*标识符*︰ 是数据段|  
|[编译器错误 C2196](compiler-error-c2196.md)|case 值*值*已使用|  
|[编译器错误 C2197](compiler-error-c2197.md)|*函数*︰ 用于调用的参数太多|  
|[编译器错误 C2198](compiler-error-c2198.md)|*函数*︰ 用于调用的参数太少|  
|[编译器错误 C2199](compiler-error-c2199.md)|语法错误︰ 找到*标识符*(在全局范围内 （是否要使用声明）？|  
