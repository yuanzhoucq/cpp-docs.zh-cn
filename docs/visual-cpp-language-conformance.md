---
title: "Visual C++ 语言一致性 | Microsoft Docs"
ms.date: 11/15/2017
ms.technology: cpp-language
ms.topic: article
dev_langs: C++
ms.assetid: 475da6e9-0d78-4b4e-bd23-f41c406c4efe
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8e9d4d86abd15f59e94ce7e51d40e119f8ebd336
ms.sourcegitcommit: 1b480aa74886930b3bd0435d71cfcc3ccda36424
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2017
---
# <a name="visual-c-language-conformance"></a>Visual C++ 语言一致性

本主题概述了 Visual Studio 2017 及早期版本中，针对 Visual C++ 的编译器功能和标准库功能的 ISO C++03、C++11、C++14、C++17 以及 C++20 草稿语言标准一致性。 每个编译器和标准库功能名称都可链接到介绍该功能的 ISO C++ 标准建议文章（如果在发布时可用）。 “支持”列中列出了首次出现在其中并支持该功能的 Visual Studio 版本。

若要深入了解 Visual Studio 2017 中的一致性改进和其他更改，请参阅 [Visual Studio 2017 中 C++ 的一致性改进](cpp-conformance-improvements-2017.md)和 [Visual Studio 2017 中 Visual C++ 的新增功能](what-s-new-for-visual-cpp-in-visual-studio.md)。 若要了解早期版本中的一致性更改，请参阅 [Visual C++ 更改历史记录](porting/visual-cpp-change-history-2003-2015.md)和 [2003 至 2015 各版本中 Visual C++ 的新增功能](porting/visual-cpp-what-s-new-2003-through-2015.md)。 有关来自 C++ 团队的最新信息，请访问 [Visual C++ 团队博客](https://blogs.msdn.microsoft.com/vcblog/)。  

 > [!NOTE]
 > Visual Studio 2015 和 Visual Studio 2017 之间没有二进制的重大更改。

## <a name="compiler-features"></a>编译器功能

|功能区域| |
|----|---|
|__C++03/11 核心语言功能__|__支持__|
|&nbsp;&nbsp;其他所有内容|VS 2015 <sup>[A](#note_A)</sup>|
|&nbsp;&nbsp;两阶段名称查找|部分 <sup>[B](#note_B)</sup>|
|&nbsp;&nbsp;[N2634 表达式 SFINAE](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2634.html)|部分 <sup>[C](#note_C)</sup>|
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
|&nbsp;&nbsp;[N4261 修复限定转换](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4261.html)|No|
|&nbsp;&nbsp;[P0017R1 扩展的聚合初始化](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)|No|
|&nbsp;&nbsp;[P0091R3 类模板的模板参数推导](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html)<br />&nbsp;&nbsp;[P0512R0 类模板参数推导问题](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0512r0.pdf)|No|
|&nbsp;&nbsp;[P0127R2 使用 auto 声明非类型模板参数](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)|No|
|&nbsp;&nbsp;[P0135R1 保证副本省略](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0135r1.html)|否 <sup>[H](#note_H)</sup>|
|&nbsp;&nbsp;[P0136R1 重新组织继承构造函数](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html)|No|
|&nbsp;&nbsp;[P0145R3 改进表达式计算顺序](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0145r3.pdf)<br />&nbsp;&nbsp;[P0400R0 函数参数的计算顺序](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0400r0.html)|No|
|&nbsp;&nbsp;[P0195R2 using 声明中的包扩展](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0195r2.html)|No|
|&nbsp;&nbsp;[P0283R2 忽略无法识别的属性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0283r2.html)|No|
|&nbsp;&nbsp;[P0702R1 修复 initializer-list ctor 的类模板参数推导](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0702r1.html)|No|
|__C++20 核心语言功能__|__支持__|
|&nbsp;&nbsp;[P0306R4 添加 &#95;&#95;VA_OPT&#95;&#95 用于省略和删除逗号](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0306r4.pdf)|No|
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
|&nbsp;&nbsp;[P0463R1 endian](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0463r1.html)|No|
|&nbsp;&nbsp;[P0674R1 数组的 make_shared()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0674r1.html)|No|
|__C++17 标准库功能__|__支持__|
|&nbsp;&nbsp;[P0433R2 将类模板的模板推导集成到标准库中](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0433r2.html)<br />&nbsp;&nbsp;[P0739R0 改进集成到标准库中的类模板参数推导](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html)|No|
|&nbsp;&nbsp;[P0426R1 char_traits 的 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html)|No|
|&nbsp;&nbsp;[P0030R1 hypot(x, y, z)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf)|No|
|&nbsp;&nbsp;[P0220R1 Library Fundamentals V1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html)|部分 <sup>[J](#note_J)</sup>|
|&nbsp;&nbsp;[P0067R5 基本字符串转换](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html)|No|
|&nbsp;&nbsp;[N4562 库基础知识：\<memory_resource>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#memory.resource.synop)<br />&nbsp;&nbsp;[P0337R0 删除 polymorphic_allocator 分配](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0337r0.html)|No|
|&nbsp;&nbsp;[P0024R2 并行算法](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html)<br />&nbsp;&nbsp;[P0336R1 重命名并行执行策略](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0336r1.pdf)<br />&nbsp;&nbsp;[P0394R4 并行算法应该对异常调用 terminate()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0394r4.html)<br />&nbsp;&nbsp;[P0452R1 统一 \<numeric> 并行算法](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0452r1.html)|No|
|&nbsp;&nbsp;[P0226R1 特殊数学函数](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0226r1.pdf)|No|
|&nbsp;&nbsp;[P0218R1 \<filesystem>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html)<br />&nbsp;&nbsp;[P0219R1 文件系统的相对路径](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0219r1.html)<br />&nbsp;&nbsp;[P0317R1 文件系统的目录项缓存](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p03179r1.html)<br />&nbsp;&nbsp;[P0392R0 文件系统路径中支持 string_view](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0392r0.pdf)<br />&nbsp;&nbsp;[P0430R2 支持非 POSIX 文件系统](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0430r2.pdf)<br />&nbsp;&nbsp;[P0492R2 解析文件系统的 NB 注释](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0492r2.html)|否 <sup>[K](#note_K)</sup>|
|&nbsp;&nbsp;[P0003R5 删除动态异常规范](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0005R4 not_fn()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html)<br />&nbsp;&nbsp;[P0358R1 not_fn() 的修补程序](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0033R1 重新组织 enable_shared_from_this](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0083R3 拼接映射和集](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf)<br />&nbsp;&nbsp;[P0508R0 阐明 insert_return_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0174R2 弃用残留库部分](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0302R1 删除 std::function 中的分配器支持](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0414R2 shared_ptr\<T[]>、shared_ptr\<T[N]>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html)<br />&nbsp;&nbsp;[P0497R0 修复数组的 shared_ptr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0521R0 弃用 shared_ptr::unique()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0521r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0607R0 标准库的内联变量](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0618R0 弃用 \<codecvt>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0618r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4562 库基础知识：Boyer Moore search()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#func.searchers.boyer_moore)<br/>&nbsp;&nbsp;[P0253R1 修复搜索器返回类型](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0253r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0031R0 \<数组> (Again) 和 \<迭代器>的 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0031r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0040R3 扩展内存管理工具](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0040r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0084R2 Emplace 返回类型](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0084r2.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0152R1 atomic::is_always_lock_free](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0152r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0154R1 hardware_destructive_interference_size 等](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0154r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0156R2 将可变参数 lock\_guard 重命名为 scoped\_lock](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0156r2.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
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
|&nbsp;&nbsp;[N4562 库基础知识：\<optional>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#optional)|VS 2017|
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

__否__表示尚未实现。  
__部分支持__意味着尚未在 Visual Studio 2017 中完全实现。 有关详细信息，请参阅注释部分。  
__N/A__ 表示建议文章未介绍功能。 这些文章虽然更改了标准的语言，但没有为实施者创建任何工作。 在此处将其列出是出于完整性的考虑。  
__VS 2010__ 表示在 Visual Studio 2010 中支持的功能。  
__VS 2013__ 表示在 Visual Studio 2013 中支持的功能。  
__VS 2015__ 表示在 Visual Studio 2015 RTM 中支持的功能。  
__VS 2015.2__ 和 __VS 2015.3__ 分别表示在 Visual Studio 2015 Update 2 和 Visual Studio 2015 Update 3 中支持的功能。  
__VS 2017__ 表示在 Visual Studio 2017 RTM 中支持的功能。  
__VS 2017 15.3__表示 Visual Studio 2017 版本 15.3 中支持的功能。  
__VS 2017 15.5__ 表示 Visual Studio 2017 版本 15.5 中支持的功能。

### <a name="notes"></a>说明

<a name="note_A"></a>__A__ 这忽略了 C++03 的动态异常规范，该规范在 C++11 中已弃用。 没有计划来实现它们，应该会从将来的 C++ 标准版中删除。  
<a name="note_B"></a>__B__ 编译器对两阶段名称查找的支持得到了改进，但仍不完整。  
<a name="note_C"></a>__C__ 自 Visual Studio 2015 Update 2 后，编译器对表达式 SFINAE 的支持足以满足标准库，但支持仍不完整。  
<a name="note_D"></a>__D__ 编译器对 C99 预处理器规则的支持在 Visual Studio 2017 中不完整。 Variadic 宏受支持，但预处理器的行为存在很多 Bug。  
<a name="note_E"></a>__E__ 它被标记为“不适用”，因为允许但不要求编译器支持扩展的整数类型。  和 GCC 和 Clang 一样，我们选择不支持它们。  
<a name="note_F"></a>__F__ 与此类似，它被标记为“不适用”，因为允许但不要求编译器实现此优化。  
<a name="note_G"></a>__G__ 在 [/std:c++14](./build/reference/std-specify-language-standard-version.md) 下受支持，并且出现可禁止的警告。  
<a name="note_H"></a>__H__ 此功能以前在 Visual Studio 2017 版本 15.3 的预览版中可用，但由于发现了 bug，已将其从发行版中删除。  
<a name="note_J"></a>__J__ 在本表中的其他部分对 Visual Studio 2015 中不完整的功能进行了说明。  
<a name="note_K"></a>__K__ 出于历史原因，文件系统 TS 在 \<experimental/filesystem> 和 \<filesystem> 中均可实现，但必须先更正其实现才能移动其命名空间。 完成此操作前，此功能标记为尚未实现。  
<a name="note_L"></a>__L__ 由编译器内部函数支持。 此内部函数在 Clang 中尚不可用。 此功能可用，但尚未在 Intellisense 中启用。   
<a name="note_14"></a>__14__ 即使指定了 [/std:c++14](./build/reference/std-specify-language-standard-version.md)（默认值），这些 C++17 功能也始终处于启用状态。 这是因为在引入 /std 选项之前实现了该功能，或者因为条件实现异常复杂。  
<a name="note_17"></a>__17__ 这些功能由 [/std:c++17](./build/reference/std-specify-language-standard-version.md)（或 [/std:c++latest](./build/reference/std-specify-language-standard-version.md)）编译器选项启用。  
<a name="note_byte"></a>__byte__ `std::byte` 由 [/std:c++17](./build/reference/std-specify-language-standard-version.md)（或 [/std:c++latest](./build/reference/std-specify-language-standard-version.md)）启用，但由于它在某些情况下可能会与 Windows SDK 标头冲突，因此它具有细化的选择退出宏。 可以通过将 `_HAS_STD_BYTE` 定义为 `0` 将其禁用。  
<a name="note_C11"></a>__C11__ 通用 CRT 实现了 C++17 所需的部分 C11 标准库，不包括 C99 `strftime()` E/O 备用转换说明符、C11 `fopen()` 独占模式和 C11 `aligned_alloc()`。 后者不太可能实现，因为 C11 以与 `free()` 的 Microsoft 实现不兼容的方式指定了 `aligned_alloc()`，即 `free()` 必须能够处理高度一致的分配。  
指定 [/std:c++17](./build/reference/std-specify-language-standard-version.md)（或 [/std:c++latest](./build/reference/std-specify-language-standard-version.md)）编译器选项后会删除 <a name="note_rem"></a>__rem__ 功能。 这些功能具有选择退出宏：`_HAS_AUTO_PTR_ETC`、`_HAS_FUNCTION_ALLOCATOR_SUPPORT`、`_HAS_OLD_IOSTREAMS_MEMBERS` 和 `_HAS_UNEXPECTED`。
  
## <a name="see-also"></a>请参阅

[C++ 语言参考](cpp/cpp-language-reference.md)  
[C++ 标准库](standard-library/cpp-standard-library-reference.md)   
[Visual Studio 2017 中 C++ 的符合性改进](cpp-conformance-improvements-2017.md)  
[Visual Studio 2017 中 Visual C++ 的新增功能](what-s-new-for-visual-cpp-in-visual-studio.md)  
[Visual C++ 更改历史记录（2003 - 2015）](porting/visual-cpp-change-history-2003-2015.md)  
[Visual C++ 新增功能（2003 - 2015）](porting/visual-cpp-what-s-new-2003-through-2015.md)  
[Visual C++ 团队博客](https://blogs.msdn.microsoft.com/vcblog/)  
