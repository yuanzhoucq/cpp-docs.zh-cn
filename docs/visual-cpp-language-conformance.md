---
title: Visual C++ 语言一致性
ms.date: 11/15/2017
ms.technology: cpp-language
ms.assetid: 475da6e9-0d78-4b4e-bd23-f41c406c4efe
author: corob-msft
ms.author: corob
ms.openlocfilehash: 17a830238e21a5ef231285b5be9bfa6ae39183f4
ms.sourcegitcommit: 42e65c171aaa17a15c20b155d22e3378e27b4642
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2019
ms.locfileid: "58356265"
---
# <a name="visual-c-language-conformance"></a>Visual C++ 语言一致性

本主题概述了 Visual Studio 2017 及早期版本中的 C++ 编译器的编译器功能和标准库功能的 ISO C++03、C++11、C++14、C++17 以及 C++20 草稿语言标准符合性。 每个编译器和标准库功能名称都可链接到介绍该功能的 ISO C++ 标准建议文章（如果在发布时可用）。 “支持”列中列出了首次出现在其中并支持该功能的 Visual Studio 版本。

若要深入了解 Visual Studio 2017 中的一致性改进和其他更改，请参阅 [Visual Studio 2017 中 C++ 的一致性改进](cpp-conformance-improvements-2017.md)和 [Visual Studio 2017 中 Visual C++ 的新增功能](what-s-new-for-visual-cpp-in-visual-studio.md)。 若要了解早期版本中的一致性更改，请参阅 [Visual C++ 更改历史记录](porting/visual-cpp-change-history-2003-2015.md)和 [2003 至 2015 各版本中 Visual C++ 的新增功能](porting/visual-cpp-what-s-new-2003-through-2015.md)。 有关来自 C++ 团队的最新信息，请访问 [Visual C++ 团队博客](https://blogs.msdn.microsoft.com/vcblog/)。

> [!NOTE]
> Visual Studio 2015 和 Visual Studio 2017 之间没有二进制的重大更改。

## <a name="compiler-features"></a>编译器功能

|功能区域| |
|----|---|
|__C++03/11 核心语言功能__|__支持__|
|&nbsp;&nbsp;其他所有内容|VS 2015 <sup>[A](#note_A)</sup>|
|&nbsp;&nbsp;两阶段名称查找|VS 2017 15.7 <sup>[B](#note_B)</sup>|
|&nbsp;&nbsp;[N2634 表达式 SFINAE](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2634.html)|VS 2017 15.7|
|&nbsp;&nbsp;[N1653 C99 预处理器](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1653.htm)|部分 <sup>[D](#note_D)</sup>|
|&nbsp;&nbsp;[N1988 扩展的整型](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n1988.pdf)|N/A <sup>[E](#note_E)</sup>|
|__C++ 14 核心语言功能__|__支持__|
|&nbsp;&nbsp;[N3323 上下文转换的已调整 wording](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3323.pdf)|VS 2013|
|&nbsp;&nbsp;[N3472 二进制文本](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3472.pdf)|VS 2015|
|&nbsp;&nbsp;[N3638 auto 和 decltype(auto) 返回类型](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3638.html)|VS 2015|
|&nbsp;&nbsp;[N3648 init-captures](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3648.html)|VS 2015|
|&nbsp;&nbsp;[N3649 泛型 lambda](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3649.html)|VS 2015|
|&nbsp;&nbsp;[N3760 [[已弃用]] 属性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3760.html)|VS 2015|
|&nbsp;&nbsp;[N3778 调整大小的释放](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[N3781 数字分隔符](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3781.pdf)|VS 2015|
|&nbsp;&nbsp;[N3651 变量模板](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3651.pdf)|VS 2015.2|
|&nbsp;&nbsp;[N3652 扩展的 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html)|VS 2017|
|&nbsp;&nbsp;[N3653 聚合的 NSDMI](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3653.html)|VS 2017|
|&nbsp;&nbsp;[N3664 避免/合成分配](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3664.html)|N/A <sup>[F](#note_F)</sup>|
|__C++ 17 核心语言功能__|__支持__|
|&nbsp;&nbsp;[N4086 删除三字符组](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)|VS 2010 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N3922 针对自动使用大括号内的初始值设定项列表的新建规则](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4051 模板-参数模板的类型名称](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4266 命名空间和枚举器的属性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4267 u8 字符文本](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4230 嵌套的命名空间定义](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4230.html)|VS 2015.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N3928 简要静态断言](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf)|VS 2017 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0184R0 一般化的基于范围的 for 循环](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html)|VS 2017 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0188R1 [[fallthrough]] 属性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r1.pdf)|VS 2017 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0001R1 删除 register 关键字](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0002R1 删除 bool 的 operator++](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0018R3 按值捕获 *this](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0028R4 不重复使用属性命名空间](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0028r4.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0061R1 __has_include](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0061r1.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0138R2 直接列表初始化整数中的固定枚举](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0170R1 constexpr lambda](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0170r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0189R1 [[nodiscard]] 属性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0189r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0212R1 [[maybe_unused]] 属性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0212r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0217R3 结构化绑定](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0217r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0292R2 constexpr if 语句](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0292r2.html)|VS 2017 15.3 <sup>[G](#note_G)</sup>|
|&nbsp;&nbsp;[P0305R1 具有初始化表达式的选择语句](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0305r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0245R1 Hexfloat 文本](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0245r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4268 允许更多非类型模板参数](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4268.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4295 折叠表达式](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4295.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0003R5 删除动态-异常-规范](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0012R1 向类型系统添加 noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0012r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0035R4 过度对齐的动态内存分配](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0035r4.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0386R2 内联变量](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0386r2.pdf)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0522R0 将template-parameters 模板与兼容参数匹配](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0522r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0036R0 删除某些空的一元折叠](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0036r0.pdf)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4261 修复限定转换](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4261.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0017R1 扩展的聚合初始化](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0091R3 类模板的模板参数推导](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html)<br />&nbsp;&nbsp;[P0512R0 类模板参数推导问题](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0512r0.pdf)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0127R2 使用 auto 声明非类型模板参数](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0135R1 保证副本省略](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0135r1.html)|VS 2017 15.6|
|&nbsp;&nbsp;[P0136R1 重新组织继承构造函数](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0137R1 std::launder](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0137r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0145R3 改进表达式计算顺序](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0145r3.pdf)<br />&nbsp;&nbsp;[P0400R0 函数参数的计算顺序](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0400r0.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0195R2 using 声明中的包扩展](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0195r2.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0283R2 忽略无法识别的属性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0283r2.html)|VS 2015 <sup>[14](#note_14)</sup>|

|功能区域| |
|----|---|
|__C++17 核心语言功能（缺陷报告）__|__支持__|
|&nbsp;&nbsp;[P0702R1 修复 initializer-list ctor 的类模板参数推导](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0702r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0588R1 简化隐式 lambda 捕获](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0588r1.html)|No|
|&nbsp;&nbsp;[CWG 1581：何时定义 constexpr 成员函数？](https://wg21.cmeerw.net/cwg/issue1581)|No|
|&nbsp;&nbsp;[P0962R1 放宽结构化绑定的自定义点查找规则](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0961r1.html)|No|
|&nbsp;&nbsp;[P0962R2 放宽 range-for 循环的自定义点查找规则](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0962r1.html)|No|
|&nbsp;&nbsp;[P0969R0 允许对可访问的成员进行结构化绑定](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0969r0.pdf)|No|

|功能区域| |
|----|---|
|__C++20 核心语言功能__|__支持__|
|&nbsp;&nbsp;[P0306R4 添加 &#95;&#95;VA_OPT&#95;&#95 用于省略和删除逗号](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0306r4.html)|No|
|&nbsp;&nbsp;[P0329R4 指定的初始化](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0329r4.pdf)|No|
|&nbsp;&nbsp;[P0409R2 允许 lambda 捕获 [=, this]](http://open-std.org/JTC1/SC22/WG21/docs/papers/2017/p0409r2.html)|No|
|&nbsp;&nbsp;[P0428R2 泛型 lambda 的熟悉模板语法](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0428r2.pdf)|No|
|&nbsp;&nbsp;[P0683R1 位域的默认成员初始化表达式](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0683r1.html)|No|
|&nbsp;&nbsp;[P0704R1 修复指向成员的 const 左值引用限定的指针](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0704r1.html)|No|
|&nbsp;&nbsp;[P0734R0 概念](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0734r0.pdf)|No|

## <a name="standard-library-features"></a>标准库功能

|功能区域| |
|---|---|
|__C++20 标准库功能__|__支持__|
|&nbsp;&nbsp;[P0777R1 避免不必要的衰减](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0777r1.pdf)|VS 2017 15.7 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0463R1 endian](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0463r1.html)|No|
|&nbsp;&nbsp;[P0674R1 数组的 make_shared()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0674r1.html)|No|
|&nbsp;&nbsp;[P0858R0 Constexpr 迭代器要求](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0858r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0809R0 比较无序容器](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0809r0.pdf)| VS 2010 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp; [P0020R3 原子\<float>，原子\<double>，原子\<long double>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0020r6.html)|No|
|&nbsp;&nbsp;[P0053R7 \<syncstream>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0053r7.pdf)<br />&nbsp;&nbsp;[P0753R2 osyncstream 操控器](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0753r2.pdf)|No|
|&nbsp;&nbsp;[P0122R7 \<span>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0122r7.pdf)|No|
|&nbsp;&nbsp;[P0202R3 \<algorithm> 和 exchange() 的 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0202r3.html)|No|
|&nbsp;&nbsp;[P0355R7 \<chrono> 日历和时区](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0355r7.html)|No|
|&nbsp;&nbsp;[P0415R1 \<complex>（重新）的 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0415r1.html)|No|
|&nbsp;&nbsp;[P0439R0 枚举类 memory_order](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0439r0.html)|No|
|&nbsp;&nbsp;[P0457R2 basic_string/basic_string_view 的 starts_with()/ends_with()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0457r2.html)|No|
|&nbsp;&nbsp;[P0550R2 remove_cvref](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf)|No|
|&nbsp;&nbsp;[P0551R3 不应将 std 函数模板专用化!](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0551r3.pdf)|No|
|&nbsp;&nbsp;[P0600R1 STL 第 1 部分的 \[\[nodiscard\]\] ](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0600r1.pdf)|No|
|&nbsp;&nbsp;[P0616R0 在 \<numeric> 中使用 move()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0616r0.pdf)|No|
|&nbsp;&nbsp;[P0653R2 to_address()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0653r2.html)|No|
|&nbsp;&nbsp;[P0718R2 原子\<shared_ptr\<T>>、原子\<weak_ptr\<T>>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0718r2.html)|No|
|&nbsp;&nbsp;[P0754R2\<version>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0754r2.pdf)|No|
|&nbsp;&nbsp;[P0767R1 弃用 is_pod](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0767r1.html)|No|
|&nbsp;&nbsp;[P0768R1 太空船比较运算符的库支持\<=>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0768r1.pdf)|No|
|&nbsp;&nbsp;[P0966R1 string::reserve() 不应缩减](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0966r1.html)|No|
|__C++17 标准库功能__|__支持__|
|&nbsp;&nbsp;[P0433R2 将类模板的模板推导集成到标准库中](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0433r2.html)<br />&nbsp;&nbsp;[P0739R0 改进集成到标准库中的类模板参数推导](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0426R1 char_traits 的 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0030R1 hypot(x, y, z)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf)|VS 2017 15.7|
|&nbsp;&nbsp;[P0220R1 Library Fundamentals V1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html)|VS 2017 15.6 <sup>[J](#note_J)</sup>|
|&nbsp;&nbsp;[P0067R5 基本字符串转换](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html)|VS 2017 15.7 <sup>[charconv](#note_charconv)</sup>|
|&nbsp;&nbsp;[N4562 库基础知识：\<memory_resource>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#memory.resource.synop)<br />&nbsp;&nbsp;[P0337R0 删除 polymorphic_allocator 分配](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0337r0.html)|VS 2017 15.6|
|&nbsp;&nbsp;[P0024R2 并行算法](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html)<br />&nbsp;&nbsp;[P0336R1 重命名并行执行策略](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0336r1.pdf)<br />&nbsp;&nbsp;[P0394R4 并行算法应该对异常调用 terminate()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0394r4.html)<br />&nbsp;&nbsp;[P0452R1 统一 \<numeric> 并行算法](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0452r1.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0226R1 特殊数学函数](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0226r1.pdf)|VS 2017 15.7|
|&nbsp;&nbsp;[P0218R1 \<filesystem>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html)<br />&nbsp;&nbsp;[P0219R1 文件系统的相对路径](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0219r1.html)<br />&nbsp;&nbsp;[P0317R1 文件系统的目录项缓存](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0317r1.html)<br />&nbsp;&nbsp;[P0392R0 文件系统路径中支持 string_view](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0392r0.pdf)<br />&nbsp;&nbsp;[P0430R2 支持非 POSIX 文件系统](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0430r2.pdf)<br />&nbsp;&nbsp;[P0492R2 解析文件系统的 NB 注释](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0492r2.html)|VS 2017 15.7 <sup>[K](#note_K)</sup>|
|&nbsp;&nbsp;[P0003R5 删除动态异常规范](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0005R4 not_fn()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html)<br />&nbsp;&nbsp;[P0358R1 not_fn() 的修补程序](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0033R1 重新组织 enable_shared_from_this](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html)|VS 2017 15.5 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0083R3 拼接映射和集](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf)<br />&nbsp;&nbsp;[P0508R0 阐明 insert_return_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0174R2 弃用残留库部分](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0302R1 删除 std::function 中的分配器支持](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0414R2 shared_ptr\<T[]>、shared_ptr\<T[N]>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html)<br />&nbsp;&nbsp;[P0497R0 修复数组的 shared_ptr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html)|VS 2017 15.5 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0521R0 弃用 shared_ptr::unique()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0521r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0607R0 标准库的内联变量](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0618R0 弃用 \<codecvt>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0618r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4562 库基础知识：Boyer-Moore search()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#func.searchers.boyer_moore)<br/>&nbsp;&nbsp;[P0253R1 修复搜索器返回类型](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0253r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0031R0 \<数组> (Again) 和 \<迭代器>的 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0031r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0040R3 扩展内存管理工具](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0040r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0084R2 Emplace 返回类型](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0084r2.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0152R1 atomic::is_always_lock_free](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0152r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0154R1 hardware_destructive_interference_size 等](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0154r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0156R2 将可变参数 lock\_guard 重命名为 scoped\_lock](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0156r2.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0258R2 has_unique_object_representations](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0258r2.html)|VS 2017 15.3 <sup>[L](#note_L)</sup>|
|&nbsp;&nbsp;[P0295R0 gcd()、lcm()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0295r0.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0298R3 std::byte](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0298r3.pdf)|VS 2017 15.3 <sup>[17](#note_17)、[byte](#note_byte)</sup>|
|&nbsp;&nbsp;[P0403R1 \<string_view>（“meow”sv 等）的 UDL](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0403r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0418R2 原子 compare_exchange memory_order 要求](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0418r2.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0435R1 修改 common_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0435r1.pdf)<br />&nbsp;&nbsp;[P0548R1 调整 common\_type 和持续时间](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0548r1.pdf)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0505R0 \<chrono> (Again) 的 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0505r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0513R0 中毒哈希](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0513r0.pdf)<br />&nbsp;&nbsp;[P0599R1 noexcept 哈希](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0599r1.pdf)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0516R0 将 shared_future 复制标记为 noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0516r0.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0517R0 从 future_errc 构造 future_error](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0517r0.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0558R1 解决 atomic<T> 已命名基类不一致的问题](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0558r1.pdf)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0604R0 将 is\_callable/result\_of 更改为 invoke\_result、is\_invocable、is\_nothrow\_invocable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0604r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4562 库基础知识：\<algorithm> sample()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#alg.random.sample)|VS 2017|
|&nbsp;&nbsp;[N4562 库基础知识：\<any>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#any)|VS 2017|
|&nbsp;&nbsp;[N4562 库基础知识：\<optional>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#optional)|VS 2017 |
|&nbsp;&nbsp;[N4562 库基础知识：\<string_view>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#string.view)|VS 2017|
|&nbsp;&nbsp;[N4562 库基础知识：\<tuple> apply()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#tuple)|VS 2017|
|&nbsp;&nbsp;[P0032R3 variant/any/optional 的同类接口](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0032r3.pdf)|VS 2017|
|&nbsp;&nbsp;[P0077R2 is_callable、is_nothrow_callable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0077r2.html)|VS 2017|
|&nbsp;&nbsp;[P0088R3 \<variant>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0088r3.html)|VS 2017|
|&nbsp;&nbsp;[P0163R0 shared_ptr::weak_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0163r0.html)|VS 2017|
|&nbsp;&nbsp;[P0209R2 make_from_tuple()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0209r2.pdf)|VS 2017|
|&nbsp;&nbsp;[P0254R2 将 string_view 和 std::string 集成](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0254r2.pdf)|VS 2017|
|&nbsp;&nbsp;[P0307R2 使 Optional 再次大于等于](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0307r2.pdf)|VS 2017|
|&nbsp;&nbsp;[P0393R3 使 Variant 大于等于](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0393r3.html)|VS 2017|
|&nbsp;&nbsp;[P0504R0 再次访问 in_place_t/in_place_type_t\<T>/in_place_index_t\<I>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0504r0.html)|VS 2017|
|&nbsp;&nbsp;[P0510R0 拒绝 Nothing、数组、引用和不完整类型的 variant](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0510r0.html)|VS 2017|
|&nbsp;&nbsp;[P0025R1 clamp()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0025r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0185R1 is_swappable、is_nothrow_swappable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0185r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0272R1 非常量 basic_string::data()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0272r1.html)|VS 2015.3|
|&nbsp;&nbsp;[N4387 改进 pair 和 tuple](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4387.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4508 shared_mutex (Untimed)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4508.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0004R1 删除已弃用的 Iostreams 别名](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0004r1.html)|VS 2015.2 <sup>[rem](#note_rem)</sup>|
|&nbsp;&nbsp;[P0006R0 类型特征（is_same_v 等）的变量模板](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0006r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0007R1 as_const()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0007r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0013R1 逻辑运算符类型特征（conjunction 等）](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0013r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0074R0 owner_less\<>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0074r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0092R1 \<chrono> floor()、ceil()、round()、abs()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0092r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0156R0 可变参数 lock_guard](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0156r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N3911 void_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3911.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4089 unique_ptr\<T[]> 中的安全转换](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4089.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4169 invoke()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4169.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4190 删除 auto_ptr、random_shuffle() 和旧的 \<功能> 内容](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4190.htm)|VS 2015 <sup>[rem](#note_rem)</sup>|
|&nbsp;&nbsp;[N4258 noexcept 清理](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4258.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4259 uncaught_exceptions()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4259.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4277 可完全复制的 reference_wrapper](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4277.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4279 map/unordered_map 的 insert_or_assign()/try_emplace()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4279.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4280 size()、empty()、data()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4280.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4366 精确限制 unique_ptr 分配](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4366.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4389 bool_constant](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4389.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0063R3 C11 标准库](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0063r3.html)|VS 2015 <sup>[C11](#note_C11)、[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4510 支持 vector/list/forward_list 中的不完整类型](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4510.html)|VS 2013 <sup>[14](#note_14)</sup>|
|__C++14 标准库功能__|__支持__|
|&nbsp;&nbsp;[N3462 SFINAE 友好的 result_of](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3462.html)|VS 2015.2|
|&nbsp;&nbsp;[N3302 \<complex> 的 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2011/n3302.html)|VS 2015|
|&nbsp;&nbsp;[N3469 \<chrono> 的 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3469.html)|VS 2015|
|&nbsp;&nbsp;[N3470 \<数组> 的 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3470.html)|VS 2015|
|&nbsp;&nbsp;[N3471 \<initializer_list>、\<tuple> 和 \<utility> 的 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3471.html)|VS 2015|
|&nbsp;&nbsp;[N3545 integral_constant::operator()()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3545.pdf)|VS 2015|
|&nbsp;&nbsp;[N3642 \<chrono>、\<字符串>（1729ms、“meow”s 等）的 UDL](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3642.pdf)|VS 2015|
|&nbsp;&nbsp;[N3644 Null 向前迭代器](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3644.pdf)|VS 2015|
|&nbsp;&nbsp;[N3654 quoted()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3654.html)|VS 2015|
|&nbsp;&nbsp;[N3657 异类关联查找](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3657.htm)|VS 2015|
|&nbsp;&nbsp;[N3658 integer_sequence](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3658.html)|VS 2015|
|&nbsp;&nbsp;[N3659 shared_mutex（定时）](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3659.html)|VS 2015|
|&nbsp;&nbsp;[N3668 exchange()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3668.html)|VS 2015|
|&nbsp;&nbsp;[N3669 修复不包含常量的 constexpr 成员函数](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3669.pdf)|VS 2015|
|&nbsp;&nbsp;[N3670 get\<T>()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3670.html)|VS 2015|
|&nbsp;&nbsp;[N3671 Dual-Range equal()、is_permutation()、mismatch()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3671.html)|VS 2015|
|&nbsp;&nbsp;[N3778 调整大小的释放](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[N3779 \<complex>（3.14i 等）的 UDL](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3779.pdf)|VS 2015|
|&nbsp;&nbsp;[N3789 \<功能> 的 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3789.htm)|VS 2015|
|&nbsp;&nbsp;[N3887 tuple_element_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3887.pdf)|VS 2015|
|&nbsp;&nbsp;[N3891 将 shared_mutex（定时）重命名为 shared_timed_mutex](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3891.htm)|VS 2015|
|&nbsp;&nbsp;[N3346 容器元素的最低要求](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3346.pdf)|VS 2013|
|&nbsp;&nbsp;[N3421 透明运算符函子（小于\<> 等）](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3421.htm)|VS 2013|
|&nbsp;&nbsp;[N3655 \<type_traits>（decay_t 等）的别名模板](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3655.pdf)|VS 2013|
|&nbsp;&nbsp;[N3656 make_unique()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3656.htm)|VS 2013|
|&nbsp;&nbsp;[N3924 阻止 rand()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3924.pdf)|不可用|

一起列出的一组文章表明某项功能已被选择加入到标准版中，同时也选择加入了一篇或多篇改进和扩展该功能的文章。 这些功能可一起实现。

### <a name="supported-values"></a>支持的值

__否__表示尚未实现。<br/>
__部分支持__意味着尚未在 Visual Studio 2017 中完全实现。 有关详细信息，请参阅注释部分。<br/>
__N/A__ 表示建议文章未介绍功能。 这些文章虽然更改了标准的语言，但没有为实施者创建任何工作。 在此处将其列出是出于完整性的考虑。<br/>
__VS 2010__ 表示在 Visual Studio 2010 中支持的功能。<br/>
__VS 2013__ 表示在 Visual Studio 2013 中支持的功能。<br/>
__VS 2015__ 表示在 Visual Studio 2015 RTM 中支持的功能。<br/>
__VS 2015.2__ 和 __VS 2015.3__ 分别表示在 Visual Studio 2015 Update 2 和 Visual Studio 2015 Update 3 中支持的功能。<br/>
__VS 2017__ 表示在 Visual Studio 2017 RTM 中支持的功能。<br/>
__VS 2017 15.3__表示 Visual Studio 2017 版本 15.3 中支持的功能。<br/>
__VS 2017 15.5__ 表示 Visual Studio 2017 版本 15.5 中支持的功能。<br/>
__VS 2017 15.7__ 表示 Visual Studio 2017 15.7 版中支持的功能。<br/>

### <a name="notes"></a>说明

<a name="note_A"></a>__A__ 在 /std:c++14 模式下，动态异常规范仍处于未实现状态，且 throw() 仍被视为 \_\_ declspec(nothrow) 的同义词。 在 C++17 中，动态异常规范大部分被 P0003R5 删除，留下了一个痕迹：throw() 被弃用，并被要求具有 noexcept 的同义词的行为。 在 /std:c++17 模式下，MSVC 现通过赋予 throw() 与 noexcept 相同的行为（即通过终止强制执行）来符合标准。

编译器选项 /Zc:noexceptTypes- 请求 \_\_declspec(nothrow) 的旧行为。 throw() 很可能会从 C++20 删除。 为帮助迁移代码，以响应标准和实现中的这些更改，在 /std:c++17 和 /permissive- 下添加了异常规范问题的新编译器警告。

<a name="note_B"></a>__B__支持 Visual Studio 2017 15.7 版中的 /permissive- 模式。 有关详细信息，请参阅 [Two-phase name lookup support comes to MSVC](https://blogs.msdn.microsoft.com/vcblog/2017/09/11/two-phase-name-lookup-support-comes-to-msvc/)（MSVC 引入两阶段名称查找支持）。

<a name="note_C"></a>__C__ 自 Visual Studio 2015 Update 2 后，编译器对表达式 SFINAE 的支持足以满足标准库。 受 Visual Studio 2017 15.7 支持（无论是否设置 /permissive- 模式）。 某些 bug 仍处于待修复状态。 “唯一标签类型”解决方法不再是必需的，我们已从 STL 实现中将其删除。

<a name="note_D"></a>__D__ 编译器对 C99 预处理器规则的支持在 Visual Studio 2017 中不完整。 Variadic 宏受支持，但预处理器的行为存在很多 Bug。  我们正在修改预处理器，并且很快将在 /permissive- 模式下发布实验版的改进内容。

<a name="note_E"></a>__E__ 它被标记为“不适用”，因为允许但不要求编译器支持扩展的整数类型。  和 GCC 和 Clang 一样，我们选择不支持它们。

<a name="note_F"></a>__F__ 与此类似，它被标记为“不适用”，因为允许但不要求编译器实现此优化。

<a name="note_G"></a>__G__ 在 [/std:c++14](./build/reference/std-specify-language-standard-version.md) 下受支持，并且出现可禁止的警告。

<a name="note_J"></a>__J__ 在本表中的其他部分对 Visual Studio 2015 中不完整的功能进行了说明。

<a name="note_K"></a>__K__ 这是一个全新的实现，与之前的 std::experimental 版本不兼容，这对符号链接支持、bug 修复以及更改需符合标准的行为而言是必不可少的。 目前，包含 \< filesystem> 提供新 std::filesystem 和旧 std::experimental::filesystem，而包含 \<experimental/filesystem> 仅提供旧实验性实现。 在下一突破性 ABI 版本的库中，实验性实现将会被删除。

<a name="note_L"></a>__L__ 由编译器内部函数支持。

<a name="note_14"></a>__14__ 即使指定了 [/std:c++14](build/reference/std-specify-language-standard-version.md)（默认值），这些 C++17/20 功能也始终处于启用状态。 这是因为在引入 /std 选项之前实现了该功能，或者因为条件实现异常复杂。

<a name="note_17"></a>__17__ 这些功能由 [/std:c++17](./build/reference/std-specify-language-standard-version.md)（或 [/std:c++latest](./build/reference/std-specify-language-standard-version.md)）编译器选项启用。

<a name="note_byte"></a>__byte__ `std::byte` 由 [/std:c++17](./build/reference/std-specify-language-standard-version.md)（或 [/std:c++latest](./build/reference/std-specify-language-standard-version.md)）启用，但由于它在某些情况下可能会与 Windows SDK 标头冲突，因此它具有细化的选择退出宏。 可以通过将 `_HAS_STD_BYTE` 定义为 `0` 将其禁用。

<a name="note_C11"></a>__C11__ 通用 CRT 实现了 C++17 所需的部分 C11 标准库，不包括 C99 `strftime()` E/O 备用转换说明符、C11 `fopen()` 独占模式和 C11 `aligned_alloc()`。 后者不太可能实现，因为 C11 以与 `free()` 的 Microsoft 实现不兼容的方式指定了 `aligned_alloc()`，即 `free()` 必须能够处理高度一致的分配。

指定 [/std:c++17](./build/reference/std-specify-language-standard-version.md)（或 [/std:c++latest](./build/reference/std-specify-language-standard-version.md)）编译器选项后会删除 <a name="note_rem"></a>__rem__ 功能。 这些功能具有选择退出宏：`_HAS_AUTO_PTR_ETC`、`_HAS_FUNCTION_ALLOCATOR_SUPPORT`、`_HAS_OLD_IOSTREAMS_MEMBERS` 和 `_HAS_UNEXPECTED`。

<a name="note_charconv"></a>__charconv__ from_chars() 和 to_chars() 均可用于整数。 我们目前正在处理浮点 from_chars()，其后需接浮点 to_chars()。

<a name ="note_parallel"></a>__并行__ C++17 的并行算法库已完成。 请注意，这并不意味着各种情况中的各种算法都是并行执行的；我们已将最重要的算法并行执行，且即使算法未并行执行，我们也提供执行策略签名。 我们的 STL 实现的中央内部标头 yvals.h 包含以下“并行算法备注”：C++ 允许将并行算法作为对串行算法的调用来实现。   此实现并行执行几个常见算法调用，但不是全部。

以下算法并行执行：

- adjacent_difference、adjacent_find、all_of、any_of、count、count_if、equal、exclusive_scan、find、find_end、find_first_of、find_if、for_each、for_each_n、inclusive_scan、mismatch、none_of、reduce、remove、remove_if、search、search_n、sort、stable_sort、transform、transform_exclusive_scan、transform_inclusive_scan、transform_reduce。

以下算法目前不并行执行：

- 目标硬件上的并行性能没有显著提升；只用于复制或交换无分支的元素的所有算法通常会受内存带宽限制：
  - copy、copy_backward、copy_n、fill、fill_n、move、move_backward、remove、remove_if、replace、replace_if、reverse、reverse_copy、rotate、rotate_copy、swap_ranges
- 对用户并行性要求存在混淆；可能出现在上述类别中：
  - generate、generate_n
- 疑为不可实现的有效并行性：
  - partial_sort、partial_sort_copy
- 尚未评估；并行性可能在未来的版本中实现，且可能是有益的：
  - copy_if、includes、inplace_merge、is_heap、is_heap_until、is_partitioned、is_sorted、is_sorted_until、lexicographical_compare、max_element、merge、min_element、minmax_element、nth_element、partition_copy、remove_copy、remove_copy_if、replace_copy、replace_copy_if、set_difference、set_intersection、set_symmetric_difference、set_union、stable_partition、unique、unique_copy

## <a name="see-also"></a>请参阅

[C++ 语言参考](cpp/cpp-language-reference.md)<br/>
[C++ 标准库](standard-library/cpp-standard-library-reference.md)<br/>
[Visual Studio 2017 中 C++ 的符合性改进](cpp-conformance-improvements-2017.md)<br/>
[Visual Studio 2017 中 Visual C++ 的新增功能](what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Visual C++ 更改历史记录（2003 - 2015）](porting/visual-cpp-change-history-2003-2015.md)<br/>
[Visual C++ 新增功能（2003 - 2015）](porting/visual-cpp-what-s-new-2003-through-2015.md)<br/>
[Visual C++ 团队博客](https://blogs.msdn.microsoft.com/vcblog/)
