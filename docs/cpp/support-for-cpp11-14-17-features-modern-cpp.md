---
title: "支持 C++11/14/17 功能（现代 C++） | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: dd2d5cbc-caf5-4a11-a057-8c365decba4e
caps.latest.revision: 59
caps.handback.revision: 56
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 支持 C++11/14/17 功能（现代 C++）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文描述了 Visual C\+\+ 中的 C\+\+11\/14\/17 功能。  
  
##  <a name="top"></a> 本文内容  
  
-   [C++11 功能列表](#featurelist)  
  
    -   [C++11 核心语言功能表](#corelanguagetable)  
  
    -   [C++11 核心语言功能表：并发](#concurrencytable)  
  
    -   [C++11 核心语言功能：C99](#c99table)  
  
-   [C++ 14 核心语言功能](#cpp14table)  
  
-   [C++17 建议的核心语言功能](#cpp17table)  
  
-   [功能表指南](#tableguide)  
  
    -   [右值引用](#rvref)  
  
    -   [Lambdas](#lambdas)  
  
    -   [decltype](#decltype)  
  
    -   [强类型/前向声明枚举](#stronglytyped)  
  
    -   [对齐方式](#alignment)  
  
    -   [标准布局和普通类型](#standardlayout)  
  
    -   [默认函数和已删除的函数](#defaultedanddeleted)  
  
    -   [override 和 final](#overrideandfinal)  
  
    -   [原子化及更多信息](#atomics)  
  
    -   [C99 __func__ 和预处理器规则](#c99)  
  
-   [标准库功能](#stl)  
  
##  <a name="featurelist"></a> C\+\+11 功能列表  
 Visual C\+\+ 实现了 [C\+\+11 核心语言规范](http://go.microsoft.com/fwlink/p/?LinkID=235092) 中的绝大多数功能、许多 C\+\+14 库功能和某些为 C\+\+17 建议的功能。 下表列出了 C\+\+11\/14\/17 核心语言功能及其在 Visual Studio 2010、[!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)]、[!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 和 Visual Studio 2015 中 Visual C\+\+ 中的实现状态。  
  
###  <a name="corelanguagetable"></a> C\+\+11 核心语言功能表  
  
|[C\+\+11 核心语言功能](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2009/n2869.html)|Visual Studio 2010|Visual Studio 2012|[!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)]|Visual Studio 2015|  
|------------------------------------------------------------------------------------------|------------------------|------------------------|--------------------------------------------------------------|------------------------|  
|右值引用 [v0.1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1610.html)、[v1.0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n2118.html)、[v2.0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2009/n2844.html)、[v2.1](http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_defects.html)、[v3.0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2010/n3053.html)|2.0 版|2.1\* 版|2.1\* 版|v3.0|  
|[引用限定符](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2439.htm)|否|否|否|是|  
|[非静态数据成员初始值设定项](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2756.htm)|否|否|[是](../cpp/uniform-initialization-and-delegating-constructors.md)|是|  
|可变参数模板 [v0.9](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2242.pdf)、[v1.0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2555.pdf)|否|否|[是](../cpp/ellipses-and-variadic-templates.md)|是|  
|[初始值设定项列表](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2672.htm)|否|否|[是](../cpp/uniform-initialization-and-delegating-constructors.md)|是|  
|[static\_assert](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1720.html)|是|是|是|是|  
|auto [v0.9](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n1984.pdf)、[v1.0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2546.htm)|v1.0|v1.0|v1.0|是|  
|[结尾返回类型](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2541.htm)|是|是|是|是|  
|Lambdas [v0.9](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2550.pdf)、[v1.0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2658.pdf)、[v1.1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2009/n2927.pdf)|v1.0|v1.1|v1.1|是|  
|decltype [v1.0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2343.pdf)、[v1.1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2011/n3276.pdf)|v1.0|v1.1\*\*|v1.1|是|  
|[右尖括号](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1757.html)|是|是|是|是|  
|[函数模板的默认模板参数](http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_defects.html)|否|否|是|是|  
|[表达式 SFINAE](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2634.html)|否|否|否|否|  
|[别名模板](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2258.pdf)|否|否|[是](../cpp/aliases-and-typedefs-cpp.md)|是|  
|[Extern 模板](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n1987.htm)|是|是|是|是|  
|[nullptr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2431.pdf)|是|是|是|是|  
|[强类型的枚举](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2347.pdf)|部分|是|是|是|  
|[前向声明枚举](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2764.pdf)|否|是|是|是|  
|[特性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2761.pdf)|否|否|否|是|  
|[constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2235.pdf)|否|否|否|是|  
|[对齐方式](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2341.pdf)|TR1|部分|部分|是|  
|[委托构造函数](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n1986.pdf)|否|否|[是](../cpp/uniform-initialization-and-delegating-constructors.md)|是|  
|[继承构造函数](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2540.htm)|否|否|否|是|  
|[显式转换运算符](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2437.pdf)|否|否|是|是|  
|[char16\_t\/char32\_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2249.html)|否|否|否|是|  
|[Unicode 字符串文本](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2442.htm)|否|否|否|是|  
|[原始字符串文本](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2442.htm)|否|否|[是](../cpp/string-and-character-literals-cpp.md)|是|  
|[文本中的通用字符名](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2170.html)|否|否|否|是|  
|[用户定义的文本](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2765.pdf)|否|否|否|是|  
|[标准布局和普通类型](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2342.htm)|否|是|是|是|  
|[默认函数和已删除的函数](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2346.htm)|否|否|[是\*](../cpp/explicitly-defaulted-and-deleted-functions.md)|是|  
|[扩展的友元声明](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1791.pdf)|是|是|是|是|  
|[扩展的 sizeof](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2253.html)|否|否|否|是|  
|[内联命名空间](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2535.htm)|否|否|否|是|  
|[无限制的联合](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2544.pdf)|否|否|否|是|  
|[作为模板参数的本地和未命名类型](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2657.htm)|是|是|是|是|  
|[基于范围的 for 循环](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2009/n2930.html)|否|是|是|是|  
|override 和 final [v0.8](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2009/n2928.htm)、[v0.9](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2010/n3206.htm)、[v1.0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2011/n3272.htm)|部分|是|是|是|  
|[最低 GC 支持](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2670.htm)|是|是|是|是|  
|[noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2010/n3050.html)|否|否|否|是|  
  
 \[[本文内容](#top)\]  
  
###  <a name="concurrencytable"></a> C\+\+11 核心语言功能表：并发  
  
|C\+\+11 核心语言功能：并发|Visual Studio 2010|Visual Studio 2012|[!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)]|Visual Studio 2015|  
|-----------------------|------------------------|------------------------|--------------------------------------------------------------|------------------------|  
|[改写的序列点](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2239.html)|不可用|不可用|不可用|是|  
|[原子](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2427.html)|否|是|是|是|  
|[强比较和交换](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2748.html)|否|是|是|是|  
|[双向界定](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2752.htm)|否|是|是|是|  
|[内存模型](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2429.htm)|不可用|不可用|不可用|是|  
|[数据依赖项排序](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2664.htm)|否|是|是|是|  
|[数据依赖项排序：函数批注](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2782.htm)|否|否|否|是|  
|[exception\_ptr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2179.html)|是|是|是|是|  
|[quick\_exit](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2440.htm)|否|否|否|是|  
|[信号处理程序中的原子化](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2547.htm)|否|否|否|否|  
|[线程本地存储区](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2659.htm)|部分|部分|部分|是|  
|[神奇的静态对象](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2660.htm)|否|否|否|是|  
  
 \[[本文内容](#top)\]  
  
###  <a name="c99table"></a> C\+\+11 核心语言功能：C99  
  
|C\+\+11 核心语言功能：C99|Visual Studio 2010|Visual Studio 2012|[!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)]|Visual Studio 2015|  
|------------------------|------------------------|------------------------|--------------------------------------------------------------|------------------------|  
|[\_\_func\_\_](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2340.htm)|部分|部分|部分|是|  
|[C99 预处理器](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1653.htm)|部分|部分|部分|部分|  
|[long long](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1811.pdf)|是|是|是|是|  
|[扩展的整型](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n1988.pdf)|不可用|不可用|不可用|不可用|  
  
 \[[本文内容](#top)\]  
  
###  <a name="cpp14table"></a> C\+\+ 14 核心语言功能  
  
||||  
|-|-|-|  
|功能|Visual Studio 2013|Visual Studio 2015|  
|上下文转换的已调整 workding|是|是|  
|二进制文本|否|是|  
|auto 和 decltype\(auto\) 返回类型|否|是|  
|init\-capture|否|是|  
|泛型 lambda|否|是|  
|变量模板|否|否|  
|扩展的 constexpr|否|否|  
|聚合的 NSDMI|否|否|  
|避免\/合成分配|否|否|  
|\[已弃用\] 特性|否|否|  
|大小经过调整的分配|否|是|  
|数字分隔符|否|是|  
  
###  <a name="cpp17table"></a> C\+\+17 建议的核心语言功能  
  
||||  
|-|-|-|  
|功能|Visual Studio 2013|Visual Studio 2015|  
|针对自动使用大括号内的初始值设定项列表的新建规则|否|否|  
|简要静态断言|否|否|  
|模板\-参数模板的类型名称|否|否|  
|删除三字符组|是|是|  
|嵌套的命名空间定义|否|否|  
|N4259 std::uncaught\_exceptions\(\)|否|否|  
|N4261 修复限定转换|否|否|  
|N4266 命名空间和枚举器的特性|否|否|  
|N4267 u8 字符文本|否|否|  
|N4268 允许更多非类型模板参数|否|否|  
|N4295 Fold 折叠表达式|否|否|  
|等待\/继续|否|是|  
  
##  <a name="tableguide"></a> 功能表指南  
  
###  <a name="rvref"></a> 右值引用  
  
> [!NOTE]
>  以下描述中的版本标识符（v0.1、v1.0、v2.0、v2.1、v3.0）仅用来演示 C\+\+11 的发展。 标准本身不会使用它们。  
  
 [N1610“通过右值澄清类对象的初始化”](http://go.microsoft.com/fwlink/p/?LinkID=235093)是早期在不引用右值的情况下支持移动语义的一种尝试。  为方便讨论，我们称之为“右值引用 0.1 版”。 它由“右值引用 [v1.0](http://go.microsoft.com/fwlink/p/?LinkID=235094)”取代。 “右值引用 [v2.0](http://go.microsoft.com/fwlink/p/?LinkID=235095)”是 Visual Studio 2010 中的 Visual C\+\+ 功能的基础，它禁止将右值引用绑定到左值，因此可以解决主要的安全性问题。  “右值引用 [v2.1](http://go.microsoft.com/fwlink/p/?LinkID=235096)”重新定义了此规则。  让我们看一下 `vector<string>::push_back()`，它具有重载 `push_back(const string&)` 和 `push_back(string&&)` 以及调用 `v.push_back("strval")`。  表达式 `"strval"` 是字符串，并且是左值。  （其他文本为右值，如整数 1729，但字符串有些特殊，因为它们是数组。\)  “右值引用 2.0 版”规则显示，`string&&` 无法绑定到 `"strval"`，因为 `"strval"` 是左值，因此 `push_back(const string&)` 是唯一可行的重载。  这将创建一个临时 `std::string`，并将它复制到向量中，然后销毁效率不太高的临时 `std::string`。 “右值引用 2.1 版”规则确认，将 `string&&` 绑定到 `"strval"` 将创建临时 `std::string`，并且该临时字符串为右值。  因此，`push_back(const string&)` 和 `push_back(string&&)` 都是可行的，但首选 `push_back(string&&)`。  将构造一个临时 `std::string`，然后将它移至向量中。  这样效率更高。  
  
 “右值引用 [v3.0](http://go.microsoft.com/fwlink/p/?LinkID=235097)”将添加新规则，以在特定条件下自动生成移动构造函数和移动赋值运算符。 这是在 Visual Studio 2015 中实现的。  
  
 \[[本文内容](#top)\]  
  
###  <a name="lambdas"></a> Lambdas  
 在 [lambda 函数](../cpp/lambda-expressions-in-cpp.md)选入到工作文件（[“0.9”版](http://go.microsoft.com/fwlink/p/?LinkID=235098)）并且已添加可变的 lambda（[“1.0”版](http://go.microsoft.com/fwlink/p/?LinkID=235099)）之后，标准化委员会全面修订了措词。 这产生了 lambda[“1.1”版](http://go.microsoft.com/fwlink/p/?LinkID=235100)，这个版本现在已完全受支持。  lambda 1.1 版的措词阐明了在特殊案例（例如引用静态成员或嵌套 lambda）中会发生的情况。  这将修复由复杂 lambda 触发的问题。  此外，无状态的 lambda 现在可转换为函数指针。  这没有包含在 N2927 措词中，但是无论如何都会将它计作 lambda 1.1 版的一部分。[C\+\+11](http://go.microsoft.com/fwlink/p/?LinkID=235092) **5.1.2 \[expr.prim.lambda\]\/6** 具有以下说明：“无 `lambda-capture` 的 `lambda-expression` 的闭包类型使用一个公共的非虚拟、非显式常量转换函数指向一个具有与闭包类型的函数调用运算符相同的参数和返回类型的函数。 此转换函数返回的值应为一个函数的地址，调用该函数时，其效果和调用闭包类型的函数调用运算符相同。”  （[!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] 实现的效果甚至更好，因为它使无状态的 lambda 可转换为具有任意调用约定的函数指针。  当你在使用期待像 `__stdcall` 函数指针这类对象的 API 时，这点很重要。）  
  
 \[[本文内容](#top)\]  
  
###  <a name="decltype"></a> decltype  
 在 decltype 选入到工作文件（[1.0 版](http://go.microsoft.com/fwlink/p/?LinkID=235101)）后，在最后时刻收到了一个小的但很重要的修复（[1.1 版](http://go.microsoft.com/fwlink/p/?LinkID=235102)）。  这对从事 STL 和 Boost 工作的程序员很有好处。  
  
 \[[本文内容](#top)\]  
  
###  <a name="stronglytyped"></a> 强类型\/前向声明枚举  
 Visual Studio 2010 中的 Visual C\+\+ 部分支持 [强类型的枚举](http://go.microsoft.com/fwlink/p/?LinkID=235103)（具体而言，支持有关显式指定的基础类型部分）。 现在这些在 Visual Studio 中已完全实现，[前向声明枚举](http://go.microsoft.com/fwlink/p/?LinkID=235104)的 C\+\+11 语义也已完全实现。  
  
 \[[本文内容](#top)\]  
  
###  <a name="alignment"></a> 对齐方式  
 选入工作文件的[对齐方式提案](http://go.microsoft.com/fwlink/p/?LinkID=235105)中的核心语言关键字 `alignas`\/`alignof` 在 Visual Studio 2015 中已实现。  Visual Studio 2010 中的 Visual C\+\+ 具有来自 TR1 的 `aligned_storage`。[!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] 已将 `aligned_union` 和 `std::align()` 添加到标准库，而且重大的问题已在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中修复。  
  
 \[[本文内容](#top)\]  
  
###  <a name="standardlayout"></a> 标准布局和普通类型  
 来自 [N2342“POD 重新访问；解决核心问题 568（修订 5）”](http://go.microsoft.com/fwlink/p/?LinkID=235106)的公开更改是将 `is_trivial` 和 `is_standard_layout` 添加到标准模板库的 `<type_traits>`。  （N2342 修改了大量核心语言措词，但无需进行编译器更改。）  这些类型特征在 Visual Studio 2010 的 Visual C\+\+ 中已提供，但它们只是复制了 `is_pod`。 因此，本文档中之前的表显示“不支持”。  它们现在由设计用于给出精确答案的编译器挂钩驱动。  
  
 STL 的 [common\_type](../standard-library/common-type-class.md) 在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中得到了迫切需要的修复。`common_type<>` 的 C\+\+11 规范导致意外后果；具体而言，它使 `common_type<int, int>::type` 返回 `int&&`。 因此，[!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 可实现[建议用于库工作组问题 2141 的解决方法](http://go.microsoft.com/fwlink/p/?LinkId=320075)，使 `common_type<int, int>::type` 返回 `int`。  
  
 作为此更改的副作用，标识用例不再起作用（`common_type<T>` 并不总是产生 `T` 类型）。 这将遵循建议的解决方法，但其将中断依赖于先前行为的所有代码。  
  
 如果需要标识类型特征，请不要使用 `std::identity` 中定义的非标准 `<type_traits>`，因为它对 `<void>` 无效。 相反，实现你自己的标识类型特征以满足你的需求。 以下是一个示例：  
  
```cpp  
template <typename T> struct Identity { typedef T type; };  
  
```  
  
> [!NOTE]
>  有关其他重大更改，请参阅[Visual C\+\+ 2015 中的重大更改](../porting/visual-cpp-change-history-2003-20151.md)。  
  
 \[[本文内容](#top)\]  
  
###  <a name="defaultedanddeleted"></a> 默认函数和已删除的函数  
 这些函数现在均受支持，但此种情况例外：对于默认函数，不支持使用 `=default` 请求识别成员的移动构造函数和移动赋值运算符。 复制和移动操作并不按照标准规定的方式进行精确交互 \- 例如，指定删除移动会同时禁止显示复制操作，但 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 不会。  
  
 有关如何使用默认函数和已删除的函数的信息，请参阅[函数](../cpp/functions-cpp.md)。  
  
 \[[本文内容](#top)\]  
  
###  <a name="overrideandfinal"></a> override 和 final  
 这经历了短暂而复杂的发展。 最初，在 [0.8 版](http://go.microsoft.com/fwlink/p/?LinkID=235108)中，具有 \[\[`override`\]\]、\[\[`hiding`\]\] 和 \[\[`base_check`\]\] 特性。  然后在 [0.9 版](http://go.microsoft.com/fwlink/p/?LinkID=235109)中，消除了这些特性并将其替换为上下文关键字。  最后，在 [1.0 版](http://go.microsoft.com/fwlink/p/?LinkID=235110)中，将它们精简为类的“`final`”以及函数的“`override`”和“`final`”。  这使它成为一个获得提升的扩展，因为 Visual Studio 2010 中的 Visual C\+\+ 已支持对函数使用此“`override`”语法，并且语义相当接近于 C\+\+11 中的语义。  “`final`”也受支持，但拼写不同（“sealed”）。  现在完全支持“`override`”和“`final`”的标准拼写和语义。 有关详细信息，请参阅 [override 说明符](../cpp/override-specifier.md) 和 [final 说明符](../cpp/final-specifier.md)。  
  
 \[[本文内容](#top)\]  
  
###  <a name="atomics"></a> 原子化及更多信息  
 [原子化](http://go.microsoft.com/fwlink/p/?LinkID=235111)、[强比较和交换](http://go.microsoft.com/fwlink/p/?LinkID=235112)、[双向界定](http://go.microsoft.com/fwlink/p/?LinkID=235113)和[数据依赖项排序](http://go.microsoft.com/fwlink/p/?LinkID=235114)指定现在已实现的标准库机制。  
  
 **相关 STL 标头：** [\<atomic\>](../standard-library/atomic.md)、[\<chrono\>](../standard-library/chrono.md)、[\<condition\_variable\>](../standard-library/condition-variable.md)、[\<future\>](../standard-library/future.md)、[\<mutex\>](../standard-library/mutex.md)、[\<ratio\>](../standard-library/ratio.md)、[\<scoped\_allocator\>](../standard-library/scoped-allocator.md) 和 [\<thread\>](../standard-library/thread.md)。  
  
 \[[本文内容](#top)\]  
  
###  <a name="c99"></a> C99 \_\_func\_\_ 和预处理器规则  
 [C++11 核心语言功能：C99](#c99table) 表列出了两个项的“部分”实现。 对于预定义标识符 `__func__`，列出“分部”，因为对非标准扩展 `__FUNCDNAME__`、`__FUNCSIG__` 和 `__FUNCTION__` 提供了支持。 有关详细信息，请参阅 [预定义的宏](../preprocessor/predefined-macros.md)。 对于 C99 预处理器规则，列出“分部”，因为支持*可变参数宏*。 有关详细信息，请参阅 [Variadic 宏](../preprocessor/variadic-macros.md)。  
  
 \[[本文内容](#top)\]  
  
###  <a name="stl"></a> 标准库功能  
 这涵盖核心语言。 至于 C\+\+11 标准库，我们虽没有漂亮的功能比较表，但 [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] 已实现此功能，但具有两个例外。  首先，当某个库功能依赖于编译器中缺少的功能时，该功能要么是模拟的（例如，`make_shared<T>()` 的模拟可变参数模板），要么没有实现。 （仅有少数情况现在已经在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中完全实现，其中最值得注意的是 `<initializer_list>`。）  C99 已在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 和提供的 C\+\+ 包装器标头中实现，并且例外情况非常少。 有关更多信息，请参阅 [Visual Studio 2013 中的 C99 库支持](http://go.microsoft.com/fwlink/p/?LinkId=321308)。  
  
 下面列出了 [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] 和 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中的部分更改：  
  
 **定位：**根据 C\+\+11 的要求，`emplace()`\/`emplace_front()`\/`emplace_back()`\/`emplace_hint()`\/`emplace_after()` 已在所有包含“任意”数量参数的容器中实现（请参见“模拟的可变参数”部分）。  例如，`vector<T>` 具有“`template <typename... Args> void emplace_back(Args&&... args)`”（它在向量的后面从任意数量的任意参数时直接构造元素类型 T，这称为“完全转发”）。  这相对于 `push_back(T&&)`（将涉及额外的移动构造和析构）效率更高。  
  
 **可变参数：** [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] 具有用于模拟可变参数模板的方案。 在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中，取消了模拟，**并完全实现了可变参数**。 如果你的代码依赖旧的模拟可变参数行为，则必须修复它。 但是，切换到实际可变参数模板**增加了编译次数**，并**降低了编译器的内存消耗**。  
  
 **显式转换运算符：**在核心语言中，显式转换运算符是一项常规功能 — 例如，你可以具有 `explicit operator MyClass()`。 但是，标准库当前仅使用一种形式：`explicit operator bool()`，这使类成为安全的布尔值可测试的类。 （无格式“`operator bool()`”是非常危险的。） 过去，Visual C\+\+ 模拟了带有 `explicit operator bool()` 的 `operator pointer-to-member()`，这导致各种问题，并且效率有些低下。 现在，完全移除了此“虚拟 bool”工作区。  
  
 **随机性：** `uniform_int_distribution` 现在是完全公平的，并且在 `<algorithm>` 中实现了 `shuffle()`，这样便可以直接接受统一随机数生成器，如 `mersenne_twister`。  
  
 **防止重载 address\-of 运算符：**C\+\+98\/03 禁止 STL 容器的元素重载其 address\-of 运算符。  这是类似 `CComPtr` 的类完成的操作，因此使 STL 避免此类重载需要类似 `CAdapt` 的帮助程序类。  开发 Visual Studio 2010 中的 Visual C\+\+ 时，STL 更改使其在更多情况下拒绝重载 address\-of 运算符。 C\+\+11 更改了相关要求，使得重载 address\-of 运算符可接受。 Visual Studio 2010 中的 C\+\+11 和 Visual C\+\+ 提供帮助程序函数 `std::addressof()`，此函数可获取对象的真实地址（无论运算符是否重载）。  在发布 Visual Studio 2010 中的 Visual C\+\+ 之前，我们已尝试将“`&elem`”的匹配项替换为具有一定抵抗性的“`std::addressof(elem)`”。[!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] 更进一步，这样重载 address\-of 运算符的类就能在整个 STL 中使用了。  
  
 **[!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] 在下列方面超出了 C\+\+11 的范围：**  
  
 **SCARY 迭代器：**实现了 SCARY 迭代器，如 [N2911“在泛型类中最小化依赖项以获得更快且更小的程序”](http://go.microsoft.com/fwlink/p/?LinkID=235115)和 [N2980“SCARY 迭代器分配和安装，第一版”](http://go.microsoft.com/fwlink/p/?LinkID=235116)中所述，这在 C\+\+11 标准是允许的，但不是必需的。  
  
 **文件系统：**已添加 [TR2 建议](http://go.microsoft.com/fwlink/p/?LinkID=235117)中的 `<filesystem>` 标头。 它提供 `recursive_directory_iterator` 和其他有趣功能。  在 TR2 的工作冻结之前，由于 C\+\+0x 很晚才投入运行且将更改为 C\+\+11，因此从 [Boost.Filesystem V2](http://go.microsoft.com/fwlink/p/?LinkID=235118) 派生出了 2006 协议。 它稍后改进为 Boost.Filesystem V3，这在 Visual Studio 2015 中实现。  
  
 一个主要优化！  现在，我们的所有容器相对于当前的表示形式都具有最小的合适大小。  这指的是容器对象本身，而不是它们指向的内容。  例如，`std::vector` 包含三个原始指针。  在 Visual Studio 2010 中的 Visual C\+\+ 中，x86 发布模式 `std::vector` 为 16 字节。  在 [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] 中，它为 12 字节，这是最小的合适大小。  如果你的程序有 100,000 个向量，则 [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] 将为你节省 400,000 字节，这很了不起。  减少内存使用率可节省空间和时间。  
  
 这是通过避免存储空的分配器和比较运算符来实现的，因为 `std::allocator` 和 `std::less` 是无状态的。  （只要自定义分配器\/比较运算符是无状态的，也会为它们启用这些优化。  显然，无法避免有状态的分配器\/比较运算符的存储，但这种情况极为少见。）  
  
 **[!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 实现一些关键的 C\+\+ 14 库功能：**  
  
-   “透明运算符函子”`less<>`、`greater<>`、`plus<>`、`multiplies<>` 等。  
  
-   `make_unique<T>(args...)` 和 `make_unique<T[]>(n)`  
  
-   `cbegin()`\/`cend()`、`rbegin()`\/`rend()` 和 `crbegin()`\/`crend()` 非成员函数。  
  
 \[[本文内容](#top)\]  
  
## 请参阅  
 [欢迎回到 C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C\+\+ 语言参考](../cpp/cpp-language-reference.md)   
 [lambda 表达式](../cpp/lambda-expressions-in-cpp.md)   
 [基于范围的 for 语句 \(C\+\+\)](../cpp/range-based-for-statement-cpp.md)   
 [C\+\+ 标准库](../standard-library/cpp-standard-library-reference.md)   
 [Visual C\+\+ 团队博客](http://blogs.msdn.com/b/vcblog/)   
 [What's New for Visual C\+\+](../top/what-s-new-for-visual-cpp-in-visual-studio-2015.md)   
 [Visual C\+\+ 2015 中的重大更改](../porting/visual-cpp-change-history-2003-20151.md)