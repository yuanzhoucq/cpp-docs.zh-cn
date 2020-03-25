---
title: Microsoft C++ 语言一致性表
description: 依据 Visual Studio 版本 Microsoft C++ 一致性更新表。
ms.date: 03/17/2020
ms.technology: cpp-language
ms.assetid: 475da6e9-0d78-4b4e-bd23-f41c406c4efe
author: corob-msft
ms.author: corob
ms.openlocfilehash: 8a5ffb5b3ab4bc80cb200b41752b19d1c958ece6
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079362"
---
# <a name="microsoft-c-language-conformance-table"></a>Microsoft C++ 语言一致性表

我们正致力于 Visual Studio (MSVC) 中 Microsoft C++ 编译器的标准符合性。 下面概述了我们的 ISO 标准 C++ 语言和 Visual Studio 版本的库一致性。 每个编译器和标准库功能名称都可链接到介绍该功能的 ISO 标准 C++ 建议文章（如果在发布时可用）。 “支持”  列中列出了首次出现支持该功能的 Visual Studio 版本。

有关 Visual Studio 2017 或 Visual Studio 2019 MSVC 符合性改进，请参阅 [Visual Studio 中 C++ 的符合性改进](cpp-conformance-improvements.md)。 有关其他更改的列表，请参阅 [Visual Studio 中 Visual C++ 的新增功能](what-s-new-for-visual-cpp-in-visual-studio.md)。 若要了解早期版本中的一致性更改，请参阅 [Visual C++ 更改历史记录](../porting/visual-cpp-change-history-2003-2015.md)和 [2003 至 2015 各版本中 Visual C++ 的新增功能](../porting/visual-cpp-what-s-new-2003-through-2015.md)。 若要获取 C++ 团队的最新资讯，请访问 [C++ 团队博客](https://devblogs.microsoft.com/cppblog/)。

> [!NOTE]
> Visual Studio 2015、Visual Studio 2017 和 Visual Studio 2019 之间没有二元中断性变更。 有关详细信息，请参阅 [Visual Studio 2015、2017 和 2019 之间的 C++ 二进制兼容性](../porting/binary-compat-2015-2017.md)

## <a name="compiler-features"></a>编译器功能

|  |  |
|--|--|
| __C++03/11 核心语言功能__ | __支持__ |
| &nbsp;&nbsp;其他所有内容 | VS 2015 <sup>[A](#note_A)</sup> |
| &nbsp;&nbsp;两阶段名称查找 | VS 2017 15.7 <sup>[B](#note_B)</sup> |
| &nbsp;&nbsp;[N2634 表达式 SFINAE](https://wg21.link/N2634) | VS 2017 15.7 |
| &nbsp;&nbsp;[N1653 C99 预处理器](https://wg21.link/N1653) | 部分 <sup>[C](#note_C)</sup> |
| __C++14 核心语言功能__ | __支持__ |
| &nbsp;&nbsp;[N3323 上下文转换的已调整 wording](https://wg21.link/N3323) | VS 2013 |
| &nbsp;&nbsp;[N3472 二进制文本](https://wg21.link/N3472) | VS 2015 |
| &nbsp;&nbsp;[N3638 auto 和 decltype(auto) 返回类型](https://wg21.link/n3638) | VS 2015 |
| &nbsp;&nbsp;[N3648 init-captures](https://wg21.link/n3648) | VS 2015 |
| &nbsp;&nbsp;[N3649 泛型 lambda](https://wg21.link/n3649) | VS 2015 |
| &nbsp;&nbsp;[N3760 \[\[deprecated\]\] 属性](https://wg21.link/n3760) | VS 2015 |
| &nbsp;&nbsp;[N3778 调整大小的释放](https://wg21.link/n3778) | VS 2015 |
| &nbsp;&nbsp;[N3781 数字分隔符](https://wg21.link/n3781) | VS 2015 |
| &nbsp;&nbsp;[N3651 变量模板](https://wg21.link/n3651) | VS 2015.2 |
| &nbsp;&nbsp;[N3652 扩展的 constexpr](https://wg21.link/n3652) | VS 2017 15.0 |
| &nbsp;&nbsp;[N3653 用于聚合的默认成员初始值设定项](https://wg21.link/n3653) | VS 2017 15.0 |
| __C++17 核心语言功能__ | __支持__ |
| &nbsp;&nbsp;[N4086 删除三字符组](https://wg21.link/n4086) | VS 2010 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N3922 针对自动使用大括号内的初始值设定项列表的新建规则](https://wg21.link/n3922) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4051 模板-参数模板的类型名称](https://wg21.link/n4051) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4266 命名空间和枚举器的属性](https://wg21.link/n4266) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4267 u8 字符文本](https://wg21.link/n4267) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4230 嵌套的命名空间定义](https://wg21.link/n4230) | VS 2015.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[N3928 简要静态断言](https://wg21.link/n3928) | VS 2017 15.0 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0184R0 一般化的基于范围的 for 循环](https://wg21.link/p0184r0) | VS 2017 15.0 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0188R1 \[\[fallthrough\]\] 属性](https://wg21.link/p0188r1) | VS 2017 15.0 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0001R1 删除 register 关键字](https://wg21.link/p0001r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0002R1 删除 bool 的 operator++](https://wg21.link/p0002r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0018R3 按值捕获 *this](https://wg21.link/p0018r3) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0028R4 不重复使用属性命名空间](https://wg21.link/p0028r4) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0061R1 \_\_has_include](https://wg21.link/p0061r1) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0138R2 直接列表初始化整数中的固定枚举](https://wg21.link/p0138r2) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0170R1 constexpr lambda](https://wg21.link/p0170r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0189R1 \[\[nodiscard\]\] 属性](https://wg21.link/p0189r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0212R1 \[\[maybe_unused\]\] 属性](https://wg21.link/p0212r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0217R3 结构化绑定](https://wg21.link/p0217r3) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0292R2 constexpr if 语句](https://wg21.link/p0292r2) | VS 2017 15.3 <sup>[D](#note_D)</sup> |
| &nbsp;&nbsp;[P0305R1 具有初始化表达式的选择语句](https://wg21.link/p0305r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0245R1 Hexfloat 文本](https://wg21.link/p0245r1) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[N4268 允许更多非类型模板参数](https://wg21.link/n4268) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[N4295 折叠表达式](https://wg21.link/n4295) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0003R5 删除动态-异常-规范](https://wg21.link/p0003r5) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0012R1 向类型系统添加 noexcept](https://wg21.link/p0012r1) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0035R4 过度对齐的动态内存分配](https://wg21.link/p0035r4) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0386R2 内联变量](https://wg21.link/p0386r2) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0522R0 将template-parameters 模板与兼容参数匹配](https://wg21.link/p0522r0) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0036R0 删除某些空的一元折叠](https://wg21.link/p0036r0) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[N4261 修复限定转换](https://wg21.link/n4261) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0017R1 扩展的聚合初始化](https://wg21.link/p0017r1) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0091R3 类模板的模板参数推导](https://wg21.link/p0091r3)<br/>&nbsp;&nbsp;[P0512R0 类模板参数推导问题](https://wg21.link/p0512r0) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0127R2 使用 auto 声明非类型模板参数](https://wg21.link/p0127r2) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0135R1 保证副本省略](https://wg21.link/p0135r1) | VS 2017 15.6 |
| &nbsp;&nbsp;[P0136R1 重新组织继承构造函数](https://wg21.link/p0136r1) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0137R1 std::launder](https://wg21.link/p0137r1) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0145R3 改进表达式计算顺序](https://wg21.link/p0145r3)<br/>&nbsp;&nbsp;[P0400R0 函数参数的计算顺序](https://wg21.link/p0400r0) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0195R2 using 声明中的包扩展](https://wg21.link/p0195r2) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0283R2 忽略无法识别的属性](https://wg21.link/p0283r2) | VS 2015 <sup>[14](#note_14)</sup> |
| __C++17 核心语言功能（缺陷报告）__ | __支持__ |
| &nbsp;&nbsp;[P0702R1 修复 initializer-list ctor 的类模板参数推导](https://wg21.link/p0702r1) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0961R1 放宽结构化绑定自定义点查找规则](https://wg21.link/p0961r1) | VS 2019 16.0 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0969R0 允许对可访问的成员进行结构化绑定](https://wg21.link/p0969r0) | VS 2019 16.0 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0588R1 简化隐式 lambda 捕获](https://wg21.link/p0588r1) | VS 2019 16.4 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P1771R1 构造函数的\[\[nodiscard\]\]](https://wg21.link/p1771r1) | VS 2019 16.4 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P1825R0 P0527R1 和 P1155R3 的合并词，更隐式移动](https://wg21.link/p1825r0) | VS 2019 16.4 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0929R2 检查是否有抽象类类型](https://wg21.link/P0929R2) | 否 |
| &nbsp;&nbsp;[P0962R2 放宽 range-for 循环的自定义点查找规则](https://wg21.link/p0962r1) | 否 |
| &nbsp;&nbsp;[P0859R0 CWG 1581：何时定义 constexpr 成员函数](https://wg21.link/p0859r0) | 否 |
| &nbsp;&nbsp;[P1009R2 new 表达式中的数组大小推导](https://wg21.link/P1009R2) | 否 |
| &nbsp;&nbsp;[P1286R2 协定 CWG DR1778](https://wg21.link/P1286R2) | 否 |
| __C++20 核心语言功能__ | __支持__ |
| &nbsp;&nbsp;[P0704R1 修复指向成员的 const 左值引用限定的指针](https://wg21.link/p0704r1) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P1041R4 将 char16_t/char32_t 字符串文本设为 UTF-16/32](https://wg21.link/P1041R4) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P1330R0 在常量表达式内更改联合的活动成员](https://wg21.link/P1330R0) | VS 2017 15.0 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0972R0 用于 \<chrono> zero()、min()、max() 的 noexcept](https://wg21.link/P0972R0) | VS 2017 15.7 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0515R3 三向（太空船）比较运算符 <=>](https://wg21.link/P0515R3) | VS 2019 16.0 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0941R2 功能测试宏](https://wg21.link/P0941R2) | VS 2019 16.0 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P1008R1 禁止聚合包含用户声明的构造函数](https://wg21.link/P1008R1) | VS 2019 16.0 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0329R4 指定的初始化](https://wg21.link/p0329r4) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0846R0 ADL 和不可见的函数模板](https://wg21.link/P0846R0) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0409R2 允许 lambda 捕获 \[=, this\]](https://wg21.link/p0409r2) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0428R2 泛型 lambda 的熟悉模板语法](https://wg21.link/p0428r2) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0624R2 默认可构造且可分配的无状态 lambda](https://wg21.link/P0624R2) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0780R2 允许在 lambda 初始捕获中使用包扩展](https://wg21.link/P0780R2) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0806R2 弃用通过 \[=\] 隐式捕获](https://wg21.link/P0806R2) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1120R0 <=> 和其他比较运算符的一致性改进](https://wg21.link/P1120R0) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1185R2 \<=\> != ==](https://wg21.link/P1185R2) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0734R0 概念](https://wg21.link/P0734R0) | VS 2019 16.3 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0857R0 修复约束中的功能差距](https://wg21.link/P0857R0) | VS 2019 16.3 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1084R2 目前的返回类型要求不足](https://wg21.link/P1084R2) | VS 2019 16.3 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0892R2 条件显式](https://wg21.link/P0892R2) | VS 2019 16.4 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1091R3 将结构化绑定扩展为更像变量声明](https://wg21.link/P1091R3) | VS 2019 16.4 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1099R5 使用 enum](https://wg21.link/P1099R5) | VS 2019 16.4 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1186R3 何时实际使用 \<=>](https://wg21.link/P1186R3) | VS 2019 16.4 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1630R1 宇宙飞船需要调整](https://wg21.link/P1630R1) | VS 2019 16.4 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0306R4 添加 \_\_VA_OPT\_\_ 用于逗号省略和逗号删除](https://wg21.link/P0306R4) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0614R1 包含初始值设定项的基于范围的 for 循环](https://wg21.link/P0614R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0683R1 位域的默认成员初始化表达式](https://wg21.link/P0683R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1002R1 常量表达式函数中的 try-catch 块](https://wg21.link/P1002R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1161R3 在加下标表达式中弃用逗号运算符](https://wg21.link/P1161R3) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1301R4 \[\[nodiscard（“消息”）\]\]](https://wg21.link/P1301R4) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1703R1 识别标头单位导入需要完全预处理](https://wg21.link/P1703R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1946R0 允许按值进行默认比较](https://wg21.link/P1946R0) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0641R2 常量与默认复制构造函数不匹配](https://wg21.link/P0641R2) | 部分 |
| &nbsp;&nbsp;[P0912R5 协同例程](https://wg21.link/P0912R5) | 部分 |
| &nbsp;&nbsp;[P1103R3 模块](https://wg21.link/P1103R3) | 部分 |
| &nbsp;&nbsp;[P0315R4 允许在未求值的上下文中使用 lambda](https://wg21.link/P0315R4) | 否 |
| &nbsp;&nbsp;[P0388R4 允许转换为未知绑定的数组](https://wg21.link/P0388R4) | 否 |
| &nbsp;&nbsp;[P0479R5 \[\[likely\]\] 和 \[\[unlikely\]\] 属性](https://wg21.link/P0479R5) | 否 |
| &nbsp;&nbsp;[P0634R3 停止使用 typename！](https://wg21.link/P0634R3) | 否 |
| &nbsp;&nbsp;[P0692R1 放宽对专用化的访问权限检查](https://wg21.link/P0692R1) | 否 |
| &nbsp;&nbsp;[P0722R3 变量大小类的高效大小删除](https://wg21.link/P0722R3) | 否 |
| &nbsp;&nbsp;[P0732R2 非类型模板参数中的类类型](https://wg21.link/P0732R2) | 否 |
| &nbsp;&nbsp;[P0735R1 memory_order_consume 与发布序列的交互](https://wg21.link/P0735R1) | 否 |
| &nbsp;&nbsp;[P0784R7 更多 constexpr 容器](https://wg21.link/P0784R7) | 否 |
| &nbsp;&nbsp;[P0840R2 \[\[no_unique_address\]\] 属性](https://wg21.link/P0840R2) | 否 |
| &nbsp;&nbsp;[P0848R3 有条件的特殊成员平凡函数](https://wg21.link/P0848R3) | 否 |
| &nbsp;&nbsp;[P0960R3 允许从带圆括号的值列表初始化聚合](https://wg21.link/P0960R3) | 否 |
| &nbsp;&nbsp;[P1064R0 允许在常量表达式中使用虚函数调用](https://wg21.link/P1064R0) | 否 |
| &nbsp;&nbsp;[P1073R3 即时函数](https://wg21.link/P1073R3) | 否 |
| &nbsp;&nbsp;[P1094R2 嵌套内联命名空间](https://wg21.link/P1094R2) | 否 |
| &nbsp;&nbsp;[P1139R2 解决与 ISO 10646 相关的用词问题](https://wg21.link/P1139R2) | 否 |
| &nbsp;&nbsp;[P1141R2 还有用于约束声明的另一种方法](https://wg21.link/P1141R2) | 否 |
| &nbsp;&nbsp;[P1143R2 constinit](https://wg21.link/P1143R2) | 否 |
| &nbsp;&nbsp;[P1152R4 弃用 volatile](https://wg21.link/P1152R4) | 否 |
| &nbsp;&nbsp;[P1236R1 带符号整数是补码](https://wg21.link/P1236R1) | 否 |
| &nbsp;&nbsp;[P1327R1 允许在常量表达式中使用 dynamic_cast 和多态 typeid](https://wg21.link/P1327R1) | 否 |
| &nbsp;&nbsp;[P1331R2 允许在 constexpr 上下文中进行平凡默认初始化](https://wg21.link/P1331R2) | 否 |
| &nbsp;&nbsp;[P1353R0 缺少功能测试宏](https://wg21.link/P1353R0) | 否 |
| &nbsp;&nbsp;[P1381R1 结构化绑定的引用捕获](https://wg21.link/P1381R1) | 否 |
| &nbsp;&nbsp;[P1452R2 采用 return-type-requirements 的非一致性语义](https://wg21.link/P1452R2) | 否 |
| &nbsp;&nbsp;[P1616R1 通过受约束的模板使用不受约束的 TTP](https://wg21.link/P1616R1) | 否 |
| &nbsp;&nbsp;[P1668R1 允许 constexpr 函数中存在未计算的内联程序集](https://wg21.link/P1668R1) | 否 |
| &nbsp;&nbsp;[P1766R1 缓解次要模块问题](https://wg21.link/P1766R1) | 否 |
| &nbsp;&nbsp;[P1811R0 放宽对重导出稳定性的重定义限制](https://wg21.link/P1811R0) | 否 |
| &nbsp;&nbsp;[P1814R0 用于别名模板的 CTAD](https://wg21.link/P1814R0) | 否 |
| &nbsp;&nbsp;[P1816R0 用于聚合的 CTAD](https://wg21.link/P1816R0) | 否 |
| &nbsp;&nbsp;[P1874R1 模块中非本地变量的动态初始化顺序](https://wg21.link/P1874R1) | 否 |
| &nbsp;&nbsp;[P1907R1 与非类型模板参数的不一致](https://wg21.link/P1907R1) | 否 |
| &nbsp;&nbsp;[P1971R0 2019 年 11 月（贝尔法斯特）会议上用于 NB 注释的核心更改](https://wg21.link/P1971R0) | 否 |
| &nbsp;&nbsp;[P1972R0 构造指向函数的指针时，US105 检查对非模板约束的满意度](https://wg21.link/P1972R0) | 否 |
| &nbsp;&nbsp;[P1975R0 修复带圆括号的聚合初始化的措词](https://wg21.link/P1975R0) | 否 |
| &nbsp;&nbsp;[P1979R0 解析为 US086](https://wg21.link/P1979R0) | 否 |
| &nbsp;&nbsp;[P1980R0 CA096:非依赖项需求子句的声明匹配](https://wg21.link/P1980R0) | 否 |

## <a name="standard-library-features"></a>标准库功能

|  |  |
|--|--|
| __C++20 标准库功能__ | __支持__ |
| &nbsp;&nbsp;[P0809R0 比较无序容器](https://wg21.link/p0809r0) | VS 2010 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0858R0 Constexpr 迭代器要求](https://wg21.link/p0858r0) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0777R1 避免不必要的衰减](https://wg21.link/p0777r1) | VS 2017 15.7 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P1164R1 让 create_directory() 变得直观](https://wg21.link/P1164R1) | VS 2019 16.0 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0550R2 remove_cvref](https://wg21.link/p0550r2) | VS 2019 16.0 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0318R1 unwrap_reference、unwrap_ref_decay](https://wg21.link/p0318r1) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0457R2 用于 basic_string/basic_string_view 的 starts_with()/ends_with()](https://wg21.link/p0457r2) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0458R2 用于有序和无序关联容器的 contains()](https://wg21.link/p0458r2) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0646R1 list/forward_list remove()/remove_if()/unique() 返回 size_type](https://wg21.link/p0646r1) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0769R2 shift_left()、shift_right()](https://wg21.link/p0769r2) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0887R1 type_identity](https://wg21.link/p0887r1) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0020R6 atomic\<float>、atomic\<double>、atomic\<long double>](https://wg21.link/p0020r6) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0463R1 endian](https://wg21.link/p0463r1) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0482R6 char8_t：用于 UTF-8 字符和字符串的类型](https://wg21.link/P0482R6) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0600R1 用于 STL 的 \[\[nodiscard\]\]（第 1 部分）](https://wg21.link/p0600r1) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0653R2 to_address()](https://wg21.link/p0653r2) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0754R2 \<version>](https://wg21.link/p0754r2) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0771R1 用于 std::function 的移动构造函数的 noexcept](https://wg21.link/P0771R1) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0487R1 修复 operator>>(basic_istream&, CharT*)](https://wg21.link/P0487R1) | VS 2019 16.3 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0616R0 在 \<numeric> 中使用 move()](https://wg21.link/p0616r0) | VS 2019 16.3 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0758R1 is_nothrow_convertible](https://wg21.link/P0758R1) | VS 2019 16.3 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0898R3 标准库概念](https://wg21.link/P0898R3) | VS 2019 16.3 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0919R3 无序容器的异类查找](https://wg21.link/P0919R3) | VS 2019 16.3 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1754R1 将概念重命名为 standard_case](https://wg21.link/P1754R1) | VS 2019 16.4 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0325R4 LFTS 中的 to_array（包含更新）](https://wg21.link/P0325R4) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0340R3 SFINAE 友好型 underlying_type](https://wg21.link/P0340R3) | VS 2019 16.5 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0356R5 bind_front()](https://wg21.link/P0356R5) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0439R0 枚举类 memory_order](https://wg21.link/p0439r0) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0553R4 \<旋转和计数函数](https://wg21.link/P0553R4) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0556R3 \< bit> ispow2(), ceil2(), floor2(), log2p1()](https://wg21.link/P0556R3) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0595R2 is_constant_evaluated()](https://wg21.link/P0595R2) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0631R8 \<数学常量](https://wg21.link/P0631R8) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0738R2 istream_iterator 清理](https://wg21.link/P0738R2) | VS 2019 16.5 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0767R1 弃用 is_pod](https://wg21.link/P0767R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0966R1 string::reserve() 不得收缩](https://wg21.link/P0966R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1209R0 erase_if()、erase()](https://wg21.link/P1209R0) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1227R2 有符号的 std::ssize()、无符号的 span::size()](https://wg21.link/P1227R2) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1355R2 ceil2() 的窄协定](https://wg21.link/P1355R2) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1357R1 is_bounded_array、is_unbounded_array](https://wg21.link/P1357R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1612R1 将 endian 重定位到 \<bit>](https://wg21.link/P1612R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1651R0 bind_front() 不应展开 reference_wrapper](https://wg21.link/P1651R0) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1690R1 无序容器的细化异类查找](https://wg21.link/P1690R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1902R1 缺少功能测试宏 2017-2019](https://wg21.link/P1902R1) | VS 2019 16.5 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0019R8 atomic_ref](https://wg21.link/P0019R8) | 否 |
| &nbsp;&nbsp;[P0053R7 \<syncstream>](https://wg21.link/p0053r7)<br/>&nbsp;&nbsp;[P0753R2 osyncstream 操控器](https://wg21.link/p0753r2) | 否 |
| &nbsp;&nbsp;[P0122R7 \<span>](https://wg21.link/p0122r7) | 否 |
| &nbsp;&nbsp;[P0202R3 \<algorithm> 和 exchange() 的常量表达式](https://wg21.link/p0202r3) | 否 |
| &nbsp;&nbsp;[P0339R6 polymorphic_allocator<>](https://wg21.link/P0339R6) | 否 |
| &nbsp;&nbsp;[P0355R7 \<chrono> 日历和时区](https://wg21.link/p0355r7) | 否 |
| &nbsp;&nbsp;[P0357R3 在 reference_wrapper 中支持不完整类型](https://wg21.link/P0357R3) | 否 |
| &nbsp;&nbsp;[P0415R1 \<complex> 的常量表达式（续）](https://wg21.link/p0415r1) | 否 |
| &nbsp;&nbsp;[P0475R1 逐块式构造的保证复制消除](https://wg21.link/P0475R1) | 否 |
| &nbsp;&nbsp;[P0476R2 \< bit> bit_cast](https://wg21.link/P0476R2) | 否 |
| &nbsp;&nbsp;[P0528R3 对包含填充位的结构执行原子比较和交换](https://wg21.link/P0528R3) | 否 |
| &nbsp;&nbsp;[P0591R4 Uses-Allocator 构造的实用函数](https://wg21.link/P0591R4) | 否 |
| &nbsp;&nbsp;[P0608R3 改进变体的转换构造函数/赋值](https://wg21.link/P0608R3) | 否 |
| &nbsp;&nbsp;[P0619R4 在 C++20 中删除 C++17 已弃用的功能](https://wg21.link/P0619R4) | 否 |
| &nbsp;&nbsp;[P0653R2 to_address()](https://wg21.link/p0653r2) | 否 |
| &nbsp;&nbsp;[P0655R1 访问\<R>()](https://wg21.link/P0655R1) | 否 |
| &nbsp;&nbsp;[P0674R1 数组的 make_shared()](https://wg21.link/p0674r1) | 否 |
| &nbsp;&nbsp;[P0718R2 atomic\<shared_ptr\<T>>、atomic\<weak_ptr\<T>>](https://wg21.link/p0718r2) | 否 |
| &nbsp;&nbsp;[P0768R1 宇宙飞船比较运算符 \<=> 的库支持](https://wg21.link/p0768r1) | 否 |
| &nbsp;&nbsp;[P0811R3 midpoint()、lerp()](https://wg21.link/P0811R3) | 否 |
| &nbsp;&nbsp;[P0879R0 交换函数的常量表达式](https://wg21.link/P0879R0) | 否 |
| &nbsp;&nbsp;[P0896R4 \<ranges\>](https://wg21.link/P0896R4) | 否 |
| &nbsp;&nbsp;[P0912R5 协同例程的库支持](https://wg21.link/P0912R5) | 否 |
| &nbsp;&nbsp;[P0920R2 预先计算的哈希值查找](https://wg21.link/P0920R2) | 否 |
| &nbsp;&nbsp;[P0935R0 删除不必要的显式默认构造函数](https://wg21.link/P0935R0) | 否 |
| &nbsp;&nbsp;[P1001R2 execution::unseq](https://wg21.link/P1001R2) | 否 |
| &nbsp;&nbsp;[P1006R1 pointer_traits<T*>::pointer_to() 的常量表达式](https://wg21.link/P1006R1) | 否 |
| &nbsp;&nbsp;[P1007R3 assume_aligned()](https://wg21.link/P1007R3) | 否 |
| &nbsp;&nbsp;[P1020R1 包含默认初始化的智能指针创建函数](https://wg21.link/P1020R1) | 否 |
| &nbsp;&nbsp;[P1023R0 用于 std::array 比较的常量表达式](https://wg21.link/P1023R0) | 否 |
| &nbsp;&nbsp;[P1032R1 其他常量表达式](https://wg21.link/P1032R1) | 否 |
| &nbsp;&nbsp;[P1165R1 在 basic_string 的 operator+() 中一致地传播有状态分配器](https://wg21.link/P1165R1) | 否 |
| &nbsp;&nbsp;[P1285R0 改进类型特征的完整性要求](https://wg21.link/P1285R0) | 否 |
| __C++17 标准库功能__ | __支持__ |
| &nbsp;&nbsp;[LWG 2221 用于 nullptr 的格式化输出运算符](https://cplusplus.github.io/LWG/issue2221) | VS 2019 16.1 |
| &nbsp;&nbsp;[N3911 void_t](https://wg21.link/n3911) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4089 unique_ptr\<T[]> 中的安全转换](https://wg21.link/n4089) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4169 invoke()](https://wg21.link/n4169) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4190 删除 auto_ptr、random_shuffle() 和旧的 \<功能> 内容](https://wg21.link/n4190) | VS 2015 <sup>[rem](#note_rem)</sup> |
| &nbsp;&nbsp;[N4258 noexcept 清理](https://wg21.link/n4258) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4259 uncaught_exceptions()](https://wg21.link/n4259) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4277 可完全复制的 reference_wrapper](https://wg21.link/n4277) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4279 map/unordered_map 的 insert_or_assign()/try_emplace()](https://wg21.link/n4279) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4280 size()、empty()、data()](https://wg21.link/n4280) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4366 精确限制 unique_ptr 分配](https://wg21.link/n4366) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4387 改进 pair 和 tuple](https://wg21.link/n4387) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4389 bool_constant](https://wg21.link/n4389) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4508 shared_mutex (Untimed)](https://wg21.link/n4508) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4510 支持 vector/list/forward_list 中的不完整类型](https://wg21.link/n4510) | VS 2013 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4562 库基础知识：\<algorithm> sample()](https://wg21.link/n4562#alg.random.sample) | VS 2017 15.0 |
| &nbsp;&nbsp;[N4562 库基础知识：\<any>](https://wg21.link/n4562#any) | VS 2017 15.0 |
| &nbsp;&nbsp;[N4562 库基础知识：\<memory_resource>](https://wg21.link/n4562#memory.resource.synop)<br/>&nbsp;&nbsp;[P0337R0 删除 polymorphic_allocator 分配](https://wg21.link/p0337r0) | VS 2017 15.6 |
| &nbsp;&nbsp;[N4562 库基础知识：\<optional>](https://wg21.link/n4562#optional) | VS 2017 15.0 |
| &nbsp;&nbsp;[N4562 库基础知识：\<string_view>](https://wg21.link/n4562#string.view) | VS 2017 15.0 |
| &nbsp;&nbsp;[N4562 库基础知识：\<tuple> apply()](https://wg21.link/n4562#tuple) | VS 2017 15.0 |
| &nbsp;&nbsp;[N4562 库基础知识：Boyer-Moore search()](https://wg21.link/n4562#func.searchers.boyer_moore)<br/>&nbsp;&nbsp;[P0253R1 修复搜索器返回类型](https://wg21.link/p0253r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0003R5 删除动态异常规范](https://wg21.link/p0003r5) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0004R1 删除已弃用的 Iostreams 别名](https://wg21.link/p0004r1) | VS 2015.2 <sup>[rem](#note_rem)</sup> |
| &nbsp;&nbsp;[P0005R4 not_fn()](https://wg21.link/p0005r4)<br/>&nbsp;&nbsp;[P0358R1 not_fn() 的修补程序](https://wg21.link/p0358r1) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0006R0 类型特征（is_same_v 等）的变量模板](https://wg21.link/p0006r0) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0007R1 as_const()](https://wg21.link/p0007r1) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0013R1 逻辑运算符类型特征（conjunction 等）](https://wg21.link/p0013r1) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0024R2 并行算法](https://wg21.link/p0024r2)<br/>&nbsp;&nbsp;[P0336R1 重命名并行执行策略](https://wg21.link/p0336r1)<br/>&nbsp;&nbsp;[P0394R4 并行算法应该对异常调用 terminate()](https://wg21.link/p0394r4)<br/>&nbsp;&nbsp;[P0452R1 统一 \<numeric> 并行算法](https://wg21.link/p0452r1) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0025R1 clamp()](https://wg21.link/p0025r1) | VS 2015.3 |
| &nbsp;&nbsp;[P0030R1 hypot(x, y, z)](https://wg21.link/p0030r1) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0031R0 \<数组> (Again) 和 \<迭代器>的 constexpr](https://wg21.link/p0031r0) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0032R3 variant/any/optional 的同类接口](https://wg21.link/p0032r3) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0033R1 重新组织 enable_shared_from_this](https://wg21.link/p0033r1) | VS 2017 15.5 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0040R3 扩展内存管理工具](https://wg21.link/p0040r3) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0063R3 C11 标准库](https://wg21.link/p0063r3) | VS 2015 <sup>[C11](#note_C11)、[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0067R5 基本字符串转换](https://wg21.link/p0067r5) | VS 2019 16.4 <sup>[charconv](#note_charconv)</sup> |
| &nbsp;&nbsp;[P0074R0 owner_less\<>](https://wg21.link/p0074r0) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0077R2 is_callable、is_nothrow_callable](https://wg21.link/p0077r2) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0083R3 拼接映射和集](https://wg21.link/p0083r3)<br/>&nbsp;&nbsp;[P0508R0 阐明 insert_return_type](https://wg21.link/p0508r0) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0084R2 Emplace 返回类型](https://wg21.link/p0084r2) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0088R3 \<variant>](https://wg21.link/p0088r3) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0092R1 \<chrono> floor()、ceil()、round()、abs()](https://wg21.link/p0092r1) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0152R1 atomic::is_always_lock_free](https://wg21.link/p0152r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0154R1 hardware_destructive_interference_size 等](https://wg21.link/p0154r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0156R0 可变参数 lock_guard](https://wg21.link/p0156r0) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0156R2 将可变参数 lock\_guard 重命名为 scoped\_lock](https://wg21.link/p0156r2) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0163R0 shared_ptr::weak_type](https://wg21.link/p0163r0) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0174R2 弃用残留库部分](https://wg21.link/p0174r2) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0185R1 is_swappable、is_nothrow_swappable](https://wg21.link/p0185r1) | VS 2015.3 |
| &nbsp;&nbsp;[P0209R2 make_from_tuple()](https://wg21.link/p0209r2) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0218R1 \<filesystem>](https://wg21.link/p0218r1)<br/>&nbsp;&nbsp;[P0219R1 文件系统的相对路径](https://wg21.link/p0219r1)<br/>&nbsp;&nbsp;[P0317R1 文件系统的目录项缓存](https://wg21.link/p0317r1)<br/>&nbsp;&nbsp;[P0392R0 文件系统路径中支持 string_view](https://wg21.link/p0392r0)<br/>&nbsp;&nbsp;[P0430R2 支持非 POSIX 文件系统](https://wg21.link/p0430r2)<br/>&nbsp;&nbsp;[P0492R2 解析文件系统的 NB 注释](https://wg21.link/p0492r2) | VS 2017 15.7 <sup>[E](#note_E)</sup> |
| &nbsp;&nbsp;[P0220R1 Library Fundamentals V1](https://wg21.link/p0220r1) | VS 2017 15.6 |
| &nbsp;&nbsp;[P0226R1 特殊数学函数](https://wg21.link/p0226r1) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0254R2 将 string_view 和 std::string 集成](https://wg21.link/p0254r2) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0258R2 has_unique_object_representations](https://wg21.link/p0258r2) | VS 2017 15.3 <sup>[G](#note_G)</sup> |
| &nbsp;&nbsp;[P0272R1 非常量 basic_string::data()](https://wg21.link/p0272r1) | VS 2015.3 |
| &nbsp;&nbsp;[P0295R0 gcd()、lcm()](https://wg21.link/p0295r0) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0298R3 std::byte](https://wg21.link/p0298r3) | VS 2017 15.3 <sup>[17](#note_17)、&nbsp;[byte](#note_byte)</sup> |
| &nbsp;&nbsp;[P0302R1 删除 std::function 中的分配器支持](https://wg21.link/p0302r1) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0307R2 使 Optional 再次大于等于](https://wg21.link/p0307r2) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0393R3 使 Variant 大于等于](https://wg21.link/p0393r3) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0403R1 \<string_view>（“meow”sv 等）的 UDL](https://wg21.link/p0403r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0414R2 shared_ptr\<T[]>、shared_ptr\<T[N]>](https://wg21.link/p0414r2)<br/>&nbsp;&nbsp;[P0497R0 修复数组的 shared_ptr](https://wg21.link/p0497r0) | VS 2017 15.5 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0418R2 原子 compare_exchange memory_order 要求](https://wg21.link/p0418r2) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0426R1 char_traits 的 constexpr](https://wg21.link/p0426r1) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0433R2 将类模板的模板推导集成到标准库中](https://wg21.link/p0433r2)<br/>&nbsp;&nbsp;[P0739R0 改进集成到标准库中的类模板参数推导](https://wg21.link/p0739r0) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0435R1 修改 common_type](https://wg21.link/p0435r1)<br/>&nbsp;&nbsp;[P0548R1 调整 common\_type 和持续时间](https://wg21.link/p0548r1) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0504R0 再次访问 in_place_t/in_place_type_t\<T>/in_place_index_t\<I>](https://wg21.link/p0504r0) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0505R0 \<chrono> (Again) 的 constexpr](https://wg21.link/p0505r0) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0510R0 拒绝 Nothing、数组、引用和不完整类型的 variant](https://wg21.link/p0510r0) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0513R0 中毒哈希](https://wg21.link/p0513r0)<br/>&nbsp;&nbsp;[P0599R1 noexcept 哈希](https://wg21.link/p0599r1) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0516R0 将 shared_future 复制标记为 noexcept](https://wg21.link/p0516r0) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0517R0 从 future_errc 构造 future_error](https://wg21.link/p0517r0) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0521R0 弃用 shared_ptr::unique()](https://wg21.link/p0521r0) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0558R1 解决 atomic\<T> 命名基类不一致问题](https://wg21.link/p0558r1) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0595R2 std::is_constant_evaluated()](https://wg21.link/P0595R2) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0602R4 在 variant/optional 中传播复制/移动平凡操作](https://wg21.link/P0602R4) | VS 2017 15.3<sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0604R0 将 is\_callable/result\_of 更改为 invoke\_result、is\_invocable、is\_nothrow\_invocable](https://wg21.link/p0604r0) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0607R0 标准库的内联变量](https://wg21.link/p0607r0) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0618R0 弃用 \<codecvt>](https://wg21.link/p0618r0) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0682R1 修复基本字符串转换](https://wg21.link/P0682R1) | VS 2015 15.7 <sup>[17](#note_17)</sup> |
| __C++14 标准库功能__ | __支持__ |
| &nbsp;&nbsp;[N3462 SFINAE 友好的 result_of](https://wg21.link/n3462) | VS 2015.2 |
| &nbsp;&nbsp;[N3302 \<complex> 的 constexpr](https://wg21.link/n3302) | VS 2015 |
| &nbsp;&nbsp;[N3469 \<chrono> 的 constexpr](https://wg21.link/n3469) | VS 2015 |
| &nbsp;&nbsp;[N3470 \<数组> 的 constexpr](https://wg21.link/n3470) | VS 2015 |
| &nbsp;&nbsp;[N3471 \<initializer_list>、\<tuple> 和 \<utility> 的 constexpr](https://wg21.link/n3471) | VS 2015 |
| &nbsp;&nbsp;[N3545 integral_constant::operator()()](https://wg21.link/n3545) | VS 2015 |
| &nbsp;&nbsp;[N3642 \<chrono>、\<字符串>（1729ms、“meow”s 等）的 UDL](https://wg21.link/n3642) | VS 2015 |
| &nbsp;&nbsp;[N3644 Null 向前迭代器](https://wg21.link/n3644) | VS 2015 |
| &nbsp;&nbsp;[N3654 quoted()](https://wg21.link/n3654) | VS 2015 |
| &nbsp;&nbsp;[N3657 异类关联查找](https://wg21.link/n3657) | VS 2015 |
| &nbsp;&nbsp;[N3658 integer_sequence](https://wg21.link/n3658) | VS 2015 |
| &nbsp;&nbsp;[N3659 shared_mutex（定时）](https://wg21.link/n3659) | VS 2015 |
| &nbsp;&nbsp;[N3668 exchange()](https://wg21.link/n3668) | VS 2015 |
| &nbsp;&nbsp;[N3669 修复不包含常量的 constexpr 成员函数](https://wg21.link/n3669) | VS 2015 |
| &nbsp;&nbsp;[N3670 get\<T>()](https://wg21.link/n3670) | VS 2015 |
| &nbsp;&nbsp;[N3671 Dual-Range equal()、is_permutation()、mismatch()](https://wg21.link/n3671) | VS 2015 |
| &nbsp;&nbsp;[N3778 调整大小的释放](https://wg21.link/n3778) | VS 2015 |
| &nbsp;&nbsp;[N3779 \<complex>（3.14i 等）的 UDL](https://wg21.link/n3779) | VS 2015 |
| &nbsp;&nbsp;[N3789 \<功能> 的 constexpr](https://wg21.link/n3789) | VS 2015 |
| &nbsp;&nbsp;[N3887 tuple_element_t](https://wg21.link/n3887) | VS 2015 |
| &nbsp;&nbsp;[N3891 将 shared_mutex（定时）重命名为 shared_timed_mutex](https://wg21.link/n3891) | VS 2015 |
| &nbsp;&nbsp;[N3346 容器元素的最低要求](https://wg21.link/n3346) | VS 2013 |
| &nbsp;&nbsp;[N3421 透明运算符函子（小于\<> 等）](https://wg21.link/n3421) | VS 2013 |
| &nbsp;&nbsp;[N3655 \<type_traits>（decay_t 等）的别名模板](https://wg21.link/n3655) | VS 2013 |
| &nbsp;&nbsp;[N3656 make_unique()](https://wg21.link/n3656) | VS 2013 |

一起列出的一组论文表示一项标准功能以及一个或多个批准的改进或扩展。 这些功能可一起实现。

### <a name="supported-values"></a>支持的值

“否”  表示尚未实现。\
“部分”  表示实现不完整。 有关详细信息，请参阅“注释”部分。\
“VS 2010”  表示在 Visual Studio 2010 中支持的功能。\
“VS 2013”  表示在 Visual Studio 2013 中支持的功能。\
“VS 2015”  表示在 Visual Studio 2015 RTW 中支持的功能。\
“VS 2015.2”  和“VS 2015.3”  分别表示在 Visual Studio 2015 Update 2 和 Visual Studio 2015 Update 3 中支持的功能。\
“VS 2017 15.0”  表示 Visual Studio 2017 版本 15.0 (RTW) 中支持的功能。\
“VS 2017 15.3”  表示 Visual Studio 2017 15.3 版中支持的功能。\
“VS 2017 15.5”  表示 Visual Studio 2017 15.5 版中支持的功能。\
“VS 2017 15.7”  表示 Visual Studio 2017 15.7 版中支持的功能。\
“VS 2019 16.0”  表示 Visual Studio 2019 版本 16.0 (RTW) 中支持的功能。\
“VS 2019 16.1”  表示 Visual Studio 2019 版本 16.1 中支持的功能。\
“VS 2019 16.2”  表示 Visual Studio 2019 版本 16.2 中支持的功能。\
“VS 2019 16.3”  表示 Visual Studio 2019 版本 16.3 中支持的功能。\
“VS 2019 16.4”  表示 Visual Studio 2019 版本 16.4 中支持的功能。\
“VS 2019 16.5”  表示 Visual Studio 2019 版本 16.5 中支持的功能。

### <a name="notes"></a>说明

<a name="note_A"></a>__A__：在 [/std:c++14](../build/reference/std-specify-language-standard-version.md) 模式下，动态异常规范一直处于未实现状态，且 `throw()` 仍被视为 `__declspec(nothrow)` 的同义词。 在 C++17 中，动态异常规范大部分已被 P0003R5 删除，只有一个残留部分：`throw()` 已遭弃用，并被要求起到 `noexcept` 的同义词作用。 在 [/std:c++17](../build/reference/std-specify-language-standard-version.md) 模式下，MSVC 现通过赋予 `throw()` 与 `noexcept` 相同的行为（即通过终止强制执行）来符合标准。

编译器选项 [/Zc:noexceptTypes](../build/reference/zc-noexcepttypes.md) 请求 `__declspec(nothrow)` 的旧行为。 很可能 `throw()` 会从 C++20 中删除。 为帮助迁移代码，以响应标准和实现中的这些更改，在 [/std:c++17](../build/reference/std-specify-language-standard-version.md) 和 [/permissive-](../build/reference/permissive-standards-conformance.md) 下添加了异常规范问题的新编译器警告。

<a name="note_B"></a>__B__：受 Visual Studio 2017 版本 15.7 中的 [/permissive-](../build/reference/permissive-standards-conformance.md) 模式支持。 有关详细信息，请参阅 [MSVC 引入两阶段名称查找支持](https://devblogs.microsoft.com/cppblog/two-phase-name-lookup-support-comes-to-msvc/)。

<a name="note_C"></a>__C__：编译器对 C99 预处理器规则的支持在 Visual Studio 2017 中不完整。 我们正在修改预处理器，已开始在 Visual Studio 2017 版本 15.8 中交付这些更改，并提供 [/experimental:preprocessor](../build/reference/experimental-preprocessor.md) 编译器开关。

<a name="note_D"></a>__D__：在 [/std:c++14](../build/reference/std-specify-language-standard-version.md) 下受支持，并且出现可取消的警告 [C4984](../error-messages/compiler-warnings/compiler-warning-c4984.md)。

<a name="note_E"></a>__E__：此为全新实现，与之前的 `std::experimental` 版本不兼容，这对符号链接支持、bug 修复以及更改必须符合标准的行为而言是必不可少的。 目前，添加 \<filesystem> 可提供新 `std::filesystem` 和旧 `std::experimental::filesystem`，而添加 \<experimental/filesystem> 则仅提供旧实验性实现。 在下一突破性 ABI 版本的库中，实验性实现将会被删除。

<a name="note_G"></a>__G__：受编译器内部函数支持。

<a name="note_14"></a>__14__ 即使指定了 [/std:c++14](../build/reference/std-specify-language-standard-version.md)（默认值），这些 C++17/20 功能也始终处于启用状态。 这是因为在引入 /std  选项之前实现了该功能，或者因为条件实现异常复杂。

<a name="note_17"></a>__17__ 这些功能由 [/std:c++17](../build/reference/std-specify-language-standard-version.md)（或 [/std:c++latest](../build/reference/std-specify-language-standard-version.md)）编译器选项启用。

<a name="note_20"></a>__20__：这些功能由 [/std:c++latest](../build/reference/std-specify-language-standard-version.md) 编译器选项启用。 C++20 实现完成后，将添加新的 **/std:c++20** 编译器选项，在该选项下，这些功能也将可用。

<a name="note_byte"></a>__byte__`std::byte` 由 [/std:c++17](../build/reference/std-specify-language-standard-version.md)（或 [/std:c++latest](../build/reference/std-specify-language-standard-version.md)）启用，但由于它在某些情况下可能会与 Windows SDK 标头冲突，因此它具有细化的选择退出宏。 可以通过将 `_HAS_STD_BYTE` 定义为 `0` 将其禁用。

<a name="note_C11"></a>__C11__ 通用 CRT 实现了 C++17 所需的部分 C11 标准库，不包括 C99 `strftime()` E/O 备用转换说明符、C11 `fopen()` 独占模式和 C11 `aligned_alloc()`。 后者不太可能实现，因为 C11 以与 `free()` 的 Microsoft 实现不兼容的方式指定了 `aligned_alloc()`，即 `free()` 必须能够处理高度一致的分配。

指定 [/std:c++17](../build/reference/std-specify-language-standard-version.md)（或 [/std:c++latest](../build/reference/std-specify-language-standard-version.md)）编译器选项后会删除 <a name="note_rem"></a>__rem__ 功能。 可以重新启用这些功能，以使用下面这些宏轻松转换为较新的语言模式：`_HAS_AUTO_PTR_ETC`、`_HAS_FUNCTION_ALLOCATOR_SUPPORT`、`_HAS_OLD_IOSTREAMS_MEMBERS` 和 `_HAS_UNEXPECTED`。

<a name="note_charconv"></a>__charconv__ `from_chars()`和 `to_chars()` 适用于整数。 浮点 `from_chars()` 和浮点 `to_chars()` 的时间线如下所示：
- VS 2017 15.7：整数 `from_chars()` 和 `to_chars()`。
- VS 2017 15.8：浮点 `from_chars()`。
- VS 2017 15.9：浮点 `to_chars()` 重载，以实现最短十进制。
- VS 2019 16.0：浮点 `to_chars()` 重载，以实现最短十六进制和十六进制精度。
- VS 2019 16.2：浮点 `to_chars()` 重载，以实现固定精度和科学记数法精度。
- VS 2019 16.4：浮点 `to_chars()` 重载，以实现常规精度。

<a name ="note_parallel"></a> __parallel__ C++17 的并行算法库是完整的。 “完整”并不意味着每种算法在各种情况下都是并行执行的。 我们已将最重要的算法并行执行，而且即使算法未并行执行，我们也提供执行策略签名。 实现的中央内部头 yvals_core.h 包含以下“并行算法备注”：C++ 允许将并行算法作为对串行算法的调用来实现。 此实现并行执行几个常见算法调用，但不是全部。

以下算法并行执行：

- `adjacent_difference`、`adjacent_find`、`all_of`、`any_of`、`count`、`count_if`、`equal`、`exclusive_scan`、`find`、`find_end`、`find_first_of`、`find_if`、`find_if_not`、`for_each`、`for_each_n`、`inclusive_scan`、`is_heap`、`is_heap_until`、`is_partitioned`、`is_sorted`、`is_sorted_until`、`mismatch`、`none_of`、`partition`、`reduce`、`remove`、`remove_if`、`replace`、`replace_if`、`search`、`search_n`、`set_difference`、`set_intersection`、`sort`、`stable_sort`、`transform`、`transform_exclusive_scan`、`transform_inclusive_scan`、`transform_reduce`

以下算法目前不并行执行：

- 目标硬件上的并行性能没有显著提升；只用于复制或置换无分支的元素的所有算法通常会受内存带宽限制：
  - `copy`, `copy_n`, `fill`, `fill_n`, `move`, `reverse`, `reverse_copy`, `rotate`, `rotate_copy`, `shift_left`, `shift_right`, `swap_ranges`
- 对用户并行性要求存在混淆；可能出现在上述类别中：
  - `generate`，`generate_n`
- 疑为不可实现的有效并行性：
  - `partial_sort`，`partial_sort_copy`
- 尚未评估；并行性可能在未来的版本中实现，且可能是有益的：
  - `copy_if`、`includes`、`inplace_merge`、`lexicographical_compare`、`max_element`、`merge`、`min_element`、`minmax_element`、`nth_element`、`partition_copy`、`remove_copy`、`remove_copy_if`、`replace_copy`、`replace_copy_if`、`set_symmetric_difference`、`set_union`、`stable_partition`、`unique`、`unique_copy`

## <a name="see-also"></a>请参阅

[C++ 语言参考](../cpp/cpp-language-reference.md)\
[C++ 标准库](../standard-library/cpp-standard-library-reference.md)\
[Visual Studio 中的 C++ 符合性改进](cpp-conformance-improvements.md)\
[Visual Studio 中 Visual C++ 的新增功能](what-s-new-for-visual-cpp-in-visual-studio.md)\
[Visual C++ 更改历史记录 (2003 - 2015)](../porting/visual-cpp-change-history-2003-2015.md)\
[Visual C++ 新增功能 (2003 - 2015)](../porting/visual-cpp-what-s-new-2003-through-2015.md)\
[C++ 团队博客](https://devblogs.microsoft.com/cppblog/)
