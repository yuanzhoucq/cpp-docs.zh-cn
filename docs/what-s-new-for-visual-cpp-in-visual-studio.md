---
title: "Visual Studio 中 Visual C++ 的新增功能 | Microsoft Docs"
ms.custom: 
ms.date: 8/2/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: b90891be2ca726bb6cdd28d024cda68494e69af4
ms.openlocfilehash: 9103da7fb4e10553d2558b15a24bc6a894dd1eff
ms.contentlocale: zh-cn
ms.lasthandoff: 08/15/2017

---

# <a name="whats-new-for-visual-c-in-includevsdev15mdmiscincludesvsdev15mdmd"></a>[!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] 中 Visual C++ 的新增功能

[!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] 向 Visual C++ 环境引入了许多更新和修补程序。 我们修复了编译器和工具中的 250 多个 bug 和已报告问题，其中很多是客户通过 [Microsoft Connect](https://connect.microsoft.com/VisualStudio "Microsoft Connect") 提交的。 感谢你报告 bug！  有关整个 Visual Studio 中新增功能的详细信息，请访问 中的[新增功能[!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)]](https://go.microsoft.com/fwlink/?linkid=834481)。

<!--The compiler and tools version number in [!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] is 14.10.24629. -->


## <a name="c-compiler"></a>C++ 编译器

### <a name="c-conformance-improvements"></a>C++ 的符合性改进
在此版本中，我们更新了 C++ 编译器和标准库，不仅增强了对 C++11 和 C++14 功能的支持，还初步提出了对预期推出的特定 C++17 标准功能的支持。 有关详细信息，请参阅 [Visual Studio 2017 中 C++ 的符合性改进](cpp-conformance-improvements-2017.md)。

### <a name="new-compiler-switches"></a>新的编译器开关  

 -**/std:c++14** 和 **/std:c++latest**：这些编译器开关使你可以选择在项目中加入特定版本的 ISO C++ 编程语言。 有关详细信息，请参阅 [-std（指定语言标准版本）](build/reference/std-specify-language-standard-version.md)。 大多数新的草案标准功能由 /std:c++lates 开关保护。 

**Visual Studio 2017 版本 15.3**：**/std:c++17** 选项启用由 Visual C++ 编译器实现的一组 C++17 功能。 此选项禁用 C++ 标准的工作草案和缺陷更新的最新版本中已更改或新的功能的编译器和标准库支持。

-[/permissive-](build/reference/permissive-standards-conformance.md)：启用所有严格标准符合性编译器选项，并禁用大部分特定于 Microsoft 的编译器扩展（但也有一些除外，例如 __declspec(dllimport)）。 （默认情况下为关，但在未来的某个时刻将默认为开。）

-[/diagnostics](build/reference/diagnostics-compiler-diagnostic-options.md)：启用显示行号、行号和列，或行号和列及脱字号（位于诊断错误或警告所在代码行的下方）。

-[/debug:fastlink](build/reference/debug-generate-debug-info.md)：  
通过避免将所有调试信息复制到 PDB 文件，实现最高达 30％ 更快的增量链接时间（与Visual Studio 2015 相比）。 PDB 文件改为指向用于创建可执行文件的对象和库文件的调试信息。 请参阅 [Faster C++ build cycle in VS “15” with /Debug:fastlink](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/faster-c-build-cycle-in-vs-15-with-debugfastlink/)（使用 /Debug:fastlink 在 VS “15” 中获得更快的生成周期）和 [Recommendations to speed C++ builds in Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2016/10/26/recommendations-to-speed-c-builds-in-visual-studio/)（在 Visual Studio 中加速 C++ 生成的建议）。

[!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] 允许结合使用 /sdl 和 /await。 删除了协同程序的 /RTC 限制。 

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen、安全性、诊断和版本控制
此版本在优化、代码生成、工具集版本控制和诊断方面做出了若干改进。 显著改进包括：  

- 改进了循环的代码生成：支持常量整数除法的自动矢量化，优化了 memset 模式的识别。
- 提高了代码安全性：改进了缓冲区溢出编辑器诊断的显示，/guard:cf 现可保护生成转移表的切换语句。
- 版本控制：内置预处理器宏_MSC_VER 的值现在会在每次 Visual C++ 工具集更新时单调更新。 有关详细信息，请参阅 [Visual C++ Compiler Version](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/visual-c-compiler-version/)（Visual C++ 编译器版本）。
- 新工具集布局：编译器和相关生成工具在开发计算机上有了新的位置和目录结构。 新布局支持并行安装多个版本的编译器。 有关详细信息，请参阅 [Compiler Tools Layout in Visual Studio "15"](https://blogs.msdn.microsoft.com/vcblog/2016/10/07/compiler-tools-layout-in-visual-studio-15/)（Visual Studio“15”中的编译器工具布局）。
- 改进了诊断：输出窗口现在会显示发生错误的列。 有关详细信息，请参阅 [C++ compiler diagnostics improvements in VS “15” Preview 5](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/c-compiler-diagnostics-improvements-in-vs-15-rc/)（VS“15”预览版 5 中的 C++ 编译器诊断改进）。
- 使用协同程序时，实验关键字“yield”（在 /await switch 下可用）已被删除。 应更新代码，以改为使用 `co_yield`。 有关详细信息，请参阅 [Visual C++ 团队博客](https://blogs.msdn.microsoft.com/vcblog/)。 

**Visual Studio 2017 版本 15.3**：对编译器中的诊断进行的其他改进。 有关详细信息，请参阅 [Visual Studio 2017 15.3.0 中的诊断改进](https://blogs.msdn.microsoft.com/vcblog/2017/07/21/diagnostic-improvements-in-vs2017-15-3-0/)。

## <a name="c-libraries"></a>C++ 库

### <a name="standard-library-improvements"></a>标准库改进：

* 对 basic_string _ITERATOR_DEBUG_LEVEL != 0 诊断进行了小幅改进。 在字符串机制中进行 IDL 检查现在将报告触发该检查的特定行为。 例如，现在会收到“无法取消引用字符串迭代器，因为其已超出范围（例如末尾迭代器）”，而不是“字符串迭代器不可取消引用”。
* 性能改进：basic_string::find(char) 重载仅调用 traits::find 一次。 以前会将此操作实施为针对长度为 1 的字符串的常规字符串搜索。
* 性能改进：basic_string::operator== 现会在比较字符串内容之前检查字符串的大小。
* 性能改进：删除了 basic_string 中编译器优化程序难以分析的控制耦合。 解决了 VSO# 262848“\<string\>: reserve() 执行了过多操作”。 请注意，对于所有短字符串，调用 reserve 后即使不执行任何操作仍会耗用资源。
* 我们添加了 \<any\>、\<string_view\>、apply()、make_from_tuple()。
* 对 std:: vector 进行了全面改进以提高正确性和性能：现可按标准版的要求正确处理插入/定位期间的别名化，在标准版需要时可通过 move_if_noexcept() 和其他逻辑提供强大的异常保障，并且插入/定位执行的元素操作减少。
* 现在 C++ 标准库会避免取消引用 null 复杂精致指针。
* 增添了 \<optional\>、\<variant\>、shared_ptr::weak_type 和 \<cstdalign\>。
* 在 min/max/minmax(initializer_list) 和 min_element/max_element/minmax_element() 中启用了 C++14 constexpr。
* 改进了 weak_ptr::lock() 性能。
* 修复了 std::promise 的移动赋值运算符，该运算符之前可导致代码永久受阻。
* 修复了编译器错误，将 atomic\<T \*\> 隐式转换为 T \*。
* pointer_traits\<Ptr\> 现可正确检测 Ptr::rebind\<U\>。
* 修复了 move_iterator 减法运算符中缺少的 const 限定符。
* 针对需要 propagate_on_container_copy_assignment 和 propagate_on_container_move_assignment 的有状态用户定义的分配器，修复了无提示的错误代码生成。
* atomic\<T\> 现可容忍重载的 operator&()。
* 为提高编译器吞吐量，C++ 标准库标头现不会包含非必需编译器内部函数的声明。
* 略微改进了针对错误的 bind() 调用的编译器诊断。
* 将 std::string/std::wstring 的移动构造函数的性能提升了超过 3 倍
* 有关标准库改进的完整列表，请参阅 [VS 2017 RTM 中的标准库修复](https://blogs.msdn.microsoft.com/vcblog/2017/02/06/stl-fixes-in-vs-2017-rtm/)。

#### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 版本 15.3

##### <a name="c17-features"></a>C++17 功能 
已经实现了几个其他的 C++17 功能。 有关详细信息，请参阅 [Visual C++ 语言一致性](visual-cpp-language-conformance.md)。

##### <a name="other-new-features"></a>其他新增功能
* 实现了 P0602R0“变体和可选项应传播副本/移动琐碎事项”。
* 现在，标准库正式允许通过 /GR- 禁用动态 RTTI。 dynamic_pointer_cast() 和 rethrow_if_nested() 本质上需要 dynamic_cast，因此标准库现在将它们在 /GR- 下标记为 =delete。
* 即使已通过 /GR- 禁用了动态 RTTI，“静态 RTTI”（采用 typeid(SomeType) 形式）仍可用，并为多个标准库组件提供支持。 现在，标准库也支持通过 /D_HAS_STATIC_RTTI=0 禁用此功能。 请注意，这将禁用 std::any、std::function 的 target()、target_type() 和 shared_ptr 的 get_deleter()。

##### <a name="correctness-fixes"></a>正确性修复
* 现在，标准库容器将其 max_size() 绑定到numeric_limits\<difference_type\>::max() 而不是 size_type 的最大值。这确保来自该容器的迭代器上的 distance() 的结果在 distance() 的返回类型中是可表示的。
* 修复了缺少的指定 auto_ptr\<void\>。
* 如果 length 参数不是整数类型，则以前无法编译 meow_n() 算法；现在它们尝试将非整数长度转换为迭代器的 difference_type。
* normal_distribution\<float\> 不再在标准库中发出关于从双精度型收缩为浮点型的警告。
* 修复了一些 basic_string 操作，这些操作在检查最大大小溢出时与 npos 而不是 max_size() 进行比较。
* condition_variable::wait_for(lock, relative_time, predicate) 将在发生虚假唤醒时等待整个相对时间。 现在，它将仅等待单个相对时间间隔。
* future::get() 现在将根据标准要求使未来无效。
* iterator_traits\<void \*\> 曾经是一个硬错误，因为它尝试形成 void&;，它现在完全变成了一个空结构，以允许在“is iterator”SFINAE 条件中使用 iterator_traits。
* 修复了 Clang -Wsystem-headers 报告的一些警告。
* 还修复了 Clang -Wmicrosoft-exception-spec 报告的“声明中的异常规范与以前的声明不匹配”。
* 还修复了 Clang 和 C1XX 报告的 mem-initializer-list 排序警告。
* 当容器本身交换时，无序容器不会交换其哈希计算器或谓词。 现在它们会进行交换。
* 现在，许多容器交换操作被标记为 noexcept（因为我们的标准库从未打算在检测到 non-propagate_on_container_swap non-equal-allocator 未定义的行为条件时引发异常）。
* 许多 vector\<bool\> 操作现在被标记为 noexcept。
* 标准库现在将使用选择退出的转义交错线来强制执行匹配的分配器 value_types（在 C++17 模式中）。
* 修复了一些将 self-range 插入 basic_strings 会打乱字符串内容的情况。 （注意：标准库仍禁止将 self-range 插入到矢量）。
* basic_string::shrink_to_fit() 不再受分配器的 propagate_on_container_swap 的影响。
* std::decay 现在可以处理令人厌恶的函数类型（即 cv 限定和/或引用限定的函数类型）。
* 更改了 include 指令以正确使用区分大小写和正斜杠，从而提高可移植性。
* 修复了警告 C4061“枚举‘Kitten’的 switch 中的枚举器‘Meow’未按 case 标签进行显式处理”。 此警告默认关闭，并且已作为警告的标准库的常规策略的一个异常进行了修复。 （标准库是 /W4 清理，但并不会试图成为 /Wall 清理。 许多默认关闭的警告会导致过多的干扰，不打算定期使用。）
* 改进了 std::list 的调试检查。 列表迭代器现在检查 operator->()，而且 list::unique() 现在将迭代器标记为无效。
* 修复了元组中的 use-allocator 元编程。

##### <a name="performancethroughput-fixes"></a>性能/吞吐量修复
* 解决了与 noexcept 的交互，从而防止将 std::atomic 的实现内联到使用结构化异常处理 (SEH) 的函数中的问题。
* 更改了标准库的内部 _Deallocate() 函数，以优化为较小的代码，从而允许将其内联到更多的位置。
* 更改了 std::try_lock() 以使用包扩展，而不是递归。
* 改进了 std::lock() 的死锁避免算法以使用 lock() 操作，而不是在所有锁的 try_lock() 上旋转。
* 启用了 system_category::message() 中的命名返回值优化。
* 连接和析取现在实例化 N + 1 类型，而不是 2N + 2 类型。
* std::function 不再实例化每个类型擦除的可调用项的分配器支持机制，从而提高吞吐量，并缩减将许多不同的 lambda 传递给 std::function 的程序中的 .obj 大小。
* allocator_traits\<std::allocator\> 包含手动内联的 std::allocator 操作，从而缩减仅通过 allocator_traits 与 std::allocator 交互的代码（即大多数代码）中的代码大小。
* C++11 最小分配器接口现在由标准库直接调用 allocator_traits 进行处理，而不是将分配器包装在内部类 _Wrap_alloc 中。 这减少了为分配器支持生成的代码大小，提高了优化器在某些情况下对标准库容器进行推理的能力，并提供了更好的调试体验（正如现在看到了分配器类型，而不是调试器中的 _Wrap_alloc\<你的分配器类型\>）。
* 删除了自定义 allocator::reference 的元编程，实际上不允许自定义的分配器。 （分配器可以使容器使用设想的指针，但不可以使用设想的引用。）
* 编译器前端已学会在基于范围的 for 循环中展开调试迭代器，从而提高调试版本的性能。
* shrink_to_fit() 和 reserve() 的 basic_string 的内部收缩路径不再位于重新分配操作的路径中，从而减少所有转变成员的代码大小。
* basic_string 的内部增长路径不再位于 shrink_to_fit() 的路径中。
* basic_string 的转变操作现在已纳入到非分配快速路径和分配慢速路径函数，从而使其更有可能将常见的无重新分配的情况内联到调用方中。
* basic_string 的转变操作现在构造所需状态的重新分配缓冲区，而不是就地调整大小。 例如，在字符串的开头插入现在将在插入之后移动内容一次（向下移动或移动到新分配的缓冲区），而不是在重新分配的情况下移动两次（移动到新分配的缓冲区，然后向下移动）。
* 在 \<string\> 中调用 C 标准库的操作现在缓存 errno 的地址以消除与 TLS 的重复交互。
* 简化了 is_pointer 的实现。
* 完成了将基于函数的表达式 SFINAE 更改为基于 struct/void_t。
* 标准库算法现在避免使用后增量迭代器。
* 修复了在 64 位系统上使用 32 位分配器时的截断警告。
* 通过重复使用缓冲区（如果可能），在非 POCMA 非等分配器情况下，std::vector 移动赋值现在更高效。

##### <a name="readability-and-other-improvements"></a>可读性和其他改进
* 标准库现在无条件地使用 C++14 constexpr，而不是有条件定义的宏。
* 标准库现在内部使用别名模板。
* 标准库现在内部使用 nullptr，而不是 nullptr_t{}。 （已根除 NULL 的内部使用。 正在逐渐清理 0 作为 null 的内部使用。）
* 标准库现在内部使用 std::move()，而不是在风格上误用 std::forward()。
* 已将 static_assert(false, "message") 更改为 #error 消息。 这提高了编译器诊断，因为 #error 立即停止编译。
* 标准库不再将函数标记为 __declspec(dllimport)。 新式链接器技术不再需要此操作。
* 已将 SFINAE 提取到默认模板参数，与返回类型和函数参数类型相比，这可以减少混乱。
* \<random\> 中的调试检查现在使用标准库的常用机制，而不是使用将 fputs() 调用到 stderr 的内部函数 _Rng_abort()。 保留此函数的实现以实现二进制兼容性，但在标准库的下一个二进制不兼容版本中已删除。 

### <a name="open-source-library-support"></a>开源库支持  
Vcpkg 是一款开源命令行工具，能极大简化在 Visual Studio 中获取和生成开源 C++ 静态库和 DLLS 的过程。 有关详细信息，请参阅 [vcpkg：用于 C++ 的程序包管理器 ](vcpkg.md)。

### <a name="cpprest-sdk-290"></a>CPPRest SDK 2.9.0  
CPPRestSDK（C++ 的跨平台 Web API）已更新到版本 2.9.0。 有关详细信息，请参阅 [CppRestSDK 2.9.0 is available on GitHub](https://blogs.msdn.microsoft.com/vcblog/2016/10/21/cpprestsdk-2-9-0-is-available-on-github/)（GitHub 上提供了 CppRestSDK 2.9.0）。

### <a name="atl"></a>ATL
* 另外进行了另一组名称查找符合性修复
* 现有的移动构造函数和移动赋值运算符现已正确地标记为非引发
* 取消禁止有关 atlstr.h 中本地静态变量的线程安全初始化的有效警告 C4640
* 在 [使用 ATL 和生成 DLL] 时，本地静态变量的线程安全初始化会在 XP 工具集中自动关闭。 这种情况不会再出现。 如果需要关闭线程安全初始化，则可以在项目设置中添加 /Zc:threadSafeInit-。 

### <a name="visual-c-runtime"></a>Visual C++ 运行时
* 为控制流防护符号新增了标头“cfguard.h”。 

## <a name="c-ide"></a>C++ IDE

* 现针对 C++ 本机项目和 C++ /CLI 项目有了更佳的配置更改性能，后者的性能增加更为明显。 第一次激活解决方案配置时，现在的速度会更快，且此解决方案配置的所有后续激活几乎可瞬时完成。

**Visual Studio 2017 版本15.3**：
* 多个项目和代码向导已按照签名对话框样式重新编写。
* “添加类”现在直接启动“添加类向导”。 以前此处的其他所有项现在位于“添加”>“新建项”。
* Win32 项目现在位于“新建项目”对话框中的“Windows 桌面”类别下。
* Windows 控制台和桌面应用程序模板现在可以在不显示向导的情况下创建项目。 现在，在相同的类别下有一个新的 Windows 桌面向导，显示和以前相同的选项。

### <a name="intellisense"></a>Intellisense  
* 现在默认使用全新的基于 SQLite 的数据库引擎。 这将提高数据库操作（如“转到定义”和“查找所有引用”）的速度，并将极大地缩短初始解决方案分析时间。 设置已移至“工具”>“选项”>“文本编辑器”>“C/C++”>“高级”下（之前位于...“C/C++”>“实验”下）。

* 我们改进了不使用预编译标头的项目和文件的 IntelliSense 性能 - 为当前文件中的标头创建自动预编译标头。

* 还为错误列表中的 IntelliSense 错误添加了错误筛选和帮助。 单击错误列现在允许进行筛选。 此外，单击特定错误或按 F1 将启动错误消息的联机搜索。

  ![错误列表](media/ErrorList1.png "错误列表")

  ![筛选的错误列表](media/ErrorList2.png "筛选的错误列表")

* 增添了按类型筛选“成员列表”项的功能。

  ![成员列表筛选](media/mlfiltering.png "成员列表筛选")

* 添了新的实验性预测 IntelliSense 功能，此功能可根据上下文筛选成员列表中的所示内容。 请参阅 [C++ IntelliSense Improvements – Predictive IntelliSense & Filtering](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/c-intellisense-improvements-predictive-intellisense-filtering/)（C++ IntelliSense 改进 - 预测 IntelliSense 和筛选）

* 即使在复杂基本代码中，“查找所有引用”(Shift+F12) 现在也可帮助轻松进行查找。 它提供高级分组、筛选、排序、在结果中搜索以及（适用于某些语言的）着色，以便你清楚了解自己的引用。 对于 C++ 而言，新的UI 包括有关是否要从变量读取或向其写入的信息。

* 已将“点到箭头”IntelliSense 功能从实验级提升为高级，且现在为默认启用。 编辑器功能“展开作用域”和“展开优先级”也已从实验级提升为高级。

* 实验性的重构功能“更改签名”和“提取函数”现默认可用。

* 用于 C++ 项目的实验性功能“快速项目加载”。 下次打开 C++ 项目时，加载速度将更快，并且越来越快！

其中一些功能与其他语言通用，有些则特定于 C++。 有关这些新增功能的详细信息，请参阅[发布 Visual Studio “15”](https://blogs.msdn.microsoft.com/visualstudio/2016/10/05/announcing-visual-studio-15-preview-5/)。 


### <a name="support-for-non-msbuild-projects-with-open-folder"></a>支持包含“打开文件夹”的非 MSBuild 项目
Visual Studio 2017 引入了“打开文件夹”功能，使得能够在包含源代码的文件夹中进行编码、生成和调试，而无需创建任何解决方案或项目。 这使得新手使用 Visual Studio 变得异常简单，即使你的项目不是基于 MSBuild。 使用“打开文件夹”，可获得 Visual Studio 为 MSBuild 所提供的强大代码理解、编辑、生成和调试功能。 有关详细信息，请参阅 [Visual C++ 中的“打开文件夹”项目](ide/non-msbuild-projects.md)。

* 改进了“打开文件夹”体验。 可通过以下 json 文件自定义体验：
  - 使用 CppProperties.json 可自定义 IntelliSense 和浏览体验。
  - 使用 Tasks.json 可自定义生成步骤。 
  - 使用 Launch.json 可自定义调试体验。

**Visual Studio 2017 版本15.3**： 
* 改进了对备用编译器和生成环境（如 MinGW 和 Cygwin）的支持。 有关详细信息，请参阅[将 MinGW 和 Cygwin 与 Visual C++ 和“打开文件夹”结合使用](https://blogs.msdn.microsoft.com/vcblog/2017/07/19/using-mingw-and-cygwin-with-visual-cpp-and-open-folder/)。
* 添加了支持，以定义“CppProperties.json”和“CMakeSettings.json”中的全局和特定于配置的环境变量。 “launch.vs.json”中定义的调试配置和“tasks.vs.json”中的任务可以使用这些环境变量。
* 改进了对 CMake 的 Ninja 生成器的支持，包括轻松定位 64 位平台的能力。

### <a name="cmake-support-via-open-folder"></a>通过“打开文件夹”支持 CMake
Visual Studio 2017 支持在不转换为 MSBuild 项目文件 (.vcxproj) 的情况下使用 CMake 项目。 有关详细信息，请参阅 [Visual C++ 中的 CMake 项目](ide/cmake-tools-for-visual-cpp.md)。 使用“打开文件夹”打开 CMake 项目时会自动配置用于 C++ 编辑、构建和调试的环境。

* 无需在根文件夹中创建 CppProperties.json 文件，C++ IntelliSense 便可正常工作。 此外，我们增添了一个新的下拉列表，允许用户在分别由 CMake 和 CppProperties.json 文件提供的配置之间轻松切换。

* 通过 CMakeLists.txt 文件所在的同一文件夹中的 CMakeSettings.json 文件提供进一步的配置支持。

  ![Cmake 打开文件夹](media/cmake_cpp.png "CMake 打开文件夹")

**Visual Studio 2017 版本 15.3**：添加了对 CMake Ninja 生成器的支持。 有关详细信息，请参阅 [Visual Studio 中的 CMake 支持 – 2017 15.3 Preview 2 中的新增功能](https://blogs.msdn.microsoft.com/vcblog/2017/06/14/cmake-support-in-visual-studio-whats-new-in-2017-15-3-preview-2/)。 

## <a name="c-installation-workloads"></a>C++ 安装工作负荷 

### <a name="windows-desktop-development-with-c"></a>使用 C++ 的 Windows 桌面开发：  
现提供原始 C++ 工作流的更细化的安装体验。 我们添加了可选组件，使你能够仅安装所需工具。  请注意，在安装程序用户界面中列出的组件的安装大小的指示并不准确，而且它低估了整个大小。

若要在 C++ 桌面工作负载中成功创建 Win32 项目，则必须安装工具集和 Windows SDK。 安装推荐（选中）的组件“VC++ 2017 v141 工具集（x86、x64）”和“Windows 10 SDK (10.0.14393)”可以确保正常运行。 如果未安装所需工具，将无法成功创建项目，且向导将挂起。

### <a name="linux-development-with-c"></a>使用 C++ 的 Linux 开发：  
热门扩展“[用于 Linux 开发的 Visual C++](https://visualstudiogallery.msdn.microsoft.com/725025cf-7067-45c2-8d01-1e0fd359ae6e)”现已纳入 Visual Studio。 此安装提供开发和调试运行在 Linux 环境中的 C++ 应用程序所需的一切信息。  

**Visual Studio 2017 版本 15.2**：跨平台代码共享和类型可视化的改进。 有关详细信息，请参阅[跨平台代码共享和类型可视化的 Linux C++ 改进](https://blogs.msdn.microsoft.com/vcblog/2017/05/10/linux-cross-platform-and-type-visualization/)。

### <a name="game-development-with-c"></a>使用 C++ 的游戏开发：  
以 DirectX 或 Cocos2d 为后盾，利用 C++ 的强大功能构建专业游戏。  

### <a name="mobile-development-with-c-android-and-ios"></a>使用 C++ 的移动开发（Android 和 iOS）：  
现可利用 Visual Studio 创建和调试面向 Android 和 iOS 的移动应用。  

### <a name="universal-windows-apps"></a>通用 Windows 应用：  
C++ 是通用 Windows 应用工作负荷的可选组件。  当前必须手动完成 C++ 项目的升级。 如果在 Visual Studio 2017 中打开面向 v140 的 UWP 项目，且如果没有安装 Visual Studio 2015，则需要在项目属性页中选择 v141 平台工具集。

## <a name="new-options-for-c-on-universal-windows-platform"></a>通用 Windows 平台上 C++ 的新选项
现在，你拥有了为通用 Windows 平台和 Windows 应用商店编写和打包 C++ 应用程序的新选项：可使用 Desktop App Converter 打包现有的桌面应用程序，用于通过 Windows 应用商店部署。 有关详细信息，请参阅 [Using Visual C++ Runtime in Centennial project](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project/)（在 Centennial 项目中使用 Visual C++ 运行时）和 [Bring your desktop app to the Universal Windows Platform (UWP) with the Desktop Bridge](https://msdn.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-root)（使用桌面桥将桌面应用引入通用 Windows 平台 (UWP)）。

在编写新代码时可使用 C ++ / WinRT，它是 Windows 运行时的标准 C ++ 语言投影，仅在头文件中实现。 它使你可以使用任何符合兼容的 C++ 编译器创作和使用 Windows 运行时 API。 C++/WinRT 旨在为 C++ 开发人员提供对新式 Windows API 的优先访问权限。 有关详细信息，请参阅 [GitHub 上提供的 C++/WinR](https://moderncpp.com/)。


## <a name="clangc2-platform-toolset"></a>Clang/C2 平台工具集
[!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] 附带的 Clang/C2 工具集现在支持 /bigobj 开关，这对生成大项目来说至关重要。 它还在编译器的前端和后端进行了多项重要的 bug 修复。

## <a name="c-code-analysis"></a>C++ 代码分析

用于强制执行 [C++ 核心准则](https://github.com/isocpp/CppCoreGuidelines) 的 C++ 核心检查器现已通过 Visual Studio 分发。 只需在项目“属性”页的“代码分析扩展”对话框中启动检查器，即会在运行代码分析时包含扩展。 

![CppCoreCheck](media/CppCoreCheck.png "CppCoreCheck 属性页") 

**Visual Studio 2017 版本 15.3**：添加了对与资源管理相关的规则的支持。 有关详细信息，请参阅[使用 C++ 核心准则检查器](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers)。

## <a name="unit-testing"></a>单元测试

新的 Visual Studio 扩展使用户可以直接在 Visual Studio 中基于 Google Test 和 Boost.Test 运行单元测试。 有关详细信息，请参阅 [C++ 单元测试更新：宣布 Boost.Test 适配器和改进的 Google Test 支持](https://blogs.msdn.microsoft.com/vcblog/2017/08/04/c-unit-testing-updates-announcing-boost-test-adapter-and-improved-google-test-support/)。

## <a name="visual-studio-graphics-diagnostics"></a>Visual Studio 图形诊断

Visual Studio 图形诊断是一套工具，用于记录、分析 Direct3D 应用中的渲染和性能问题。 可对在 Windows 电脑上、在 Windows 设备模拟器中或在远程电脑或设备上本地运行的应用使用图形诊断功能。

* **顶点和几何着色的输入和输出：**查看顶点着色和几何着色的输入和输出一直以来是最渴求的功能之一，工具中现已支持此功能。 只需在“管道阶段”视图中选择“VS”或“GS”阶段，即可在下面的表中开始检查其输入和输出。

  ![着色器的输入/输出](media/io-shaders.png)

* **在对象表中搜索和筛选：**提供一种快捷简单的方法来查找所需资源。

  ![搜索](media/search.png)
   
* **资源历史记录：**这种新视图提供了一种简化的方式，以在渲染捕获的帧期间使用资源时查看该资源的整个修改历史记录。 若要调用任何资源的历史记录，只需单击任意资源超链接旁边的时钟图标。

  ![资源历史记录](media/resource-history.png)

  这将显示新的资源历史记录工具窗口，它由资源的更改历史记录所填充。

  ![资源历史记录更改](media/resource-history-change.png)

  请注意，如果在捕获帧时启用了完整调用堆栈捕获（“Visual Studio”>“工具”>“选项”>“图形诊断”），则可在你的 Visual Studio 项目中对每个更改事件的上下文进行快速推导和检查。  

* **API 统计信息**：在帧中查看 API 使用情况的高级摘要。 这样可以轻松发现那些你未意识到正在调用的，或调用太多次的调用。 可在 Visual Studio 图形分析器中通过“视图”>“API 统计信息”使用此窗口。

  ![API 统计信息](media/api-stats.png)

* **内存统计信息：**查看驱动程序为你在帧中所创建的资源分配了多少内存。 可在 Visual Studio 图形分析器中通过“视图”>“内存统计信息”使用此窗口。 通过右键单击并选择“全部复制”，可将数据复制到 CSV 文件，以便在电子表格中查看。

  ![内存统计信息](media/memory-stats.png)
 
* **框架验证：**新的错误和警告列表提供了一种简单的方式，以导航到基于潜在问题（由 Direct3D 调试层检测）的事件列表。 在 Visual Studio 图形分析器中单击“视图”->“帧验证”，可打开该窗口。 然后单击“运行验证”，以开始分析。 这可能耗费数分钟时间，具体取决于帧的复杂性。

  ![帧验证](media/frame-validation.png)
 
* **对 D3D12 的帧分析：**使用帧分析来分析具有定向“假设”试验的绘图调用性能。 切换至“帧分析”选项卡，然后运行分析以查看报告。 有关详细信息，请观看 [GoingNative 25: Visual Studio Graphics Frame Analysis](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool)（GoingNative 25：Visual Studio 图形帧分析）视频。

  ![帧分析](media/frame-analysis.png)

* **GPU 使用情况改进：**使用 GPU 视图或 Windows Performance Analyzer (WPA) 工具，打开通过 Visual Studio GPU 使用情况探查器获取的跟踪，以便获取更详细的分析。 如果安装了 Windows Performance Toolkit，则在会话概述的右下方将有两个超链接，一个指向 WPA，另一个指向 GPU 视图。

  ![GPU 使用情况](media/gpu-usage.png)
 
  通过此链接在 GPU 视图中打开的跟踪支持在 VS 和 GPU 视图之间的时间线中进行同步缩放和平移。 VS 中的复选框用于控制是否启用同步。 

  ![GPU 视图](media/gpu-view.png) 


 

