---
title: Visual Studio C++ 示例
description: GitHub 上的存档 Visual Studio C++ 示例存储库中提供的示例的摘要说明。
ms.date: 03/23/2020
ms.technology: cpp-language
ms.assetid: 76798022-5886-48e7-a7f2-f99352b15cbf
ms.openlocfilehash: 0862f6b512f7278f878ade53b320ad5298bccf68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "80215093"
---
# <a name="visual-studio-c-samples"></a>Visual Studio C++ 示例

Visual Studio C++ 示例可在 Web 上找到。 Microsoft 已生成许多 C++ 示例，这些示例演示了跨多种技术的不同功能。 下面介绍是一些查找其他示例的位置：

- [Microsoft Docs 示例 - C++](https://docs.microsoft.com/samples/browse/?term=c%2B%2B)

- [GitHub 上的 Windows 示例](https://microsoft.github.io/windows/)

- [Windows 开发人员中心代码示例](https://developer.microsoft.com/windows/samples)

- [CodePlex 示例存档](https://archive.codeplex.com/)

- [ADO 代码示例](/office/client-developer/access/desktop-database-reference/ado-code-examples-in-microsoft-visual-c)

- [Windows 硬件开发示例](https://docs.microsoft.com/samples/browse/?products=windows-wdk)

## <a name="archived-c-samples-on-github"></a>GitHub 上的存档 C++ 示例

Visual Studio 在以前的版本中包含了 C++ 示例代码。 该示例代码要么已与 Visual Studio 一起安装，要么已作为单独的下载项提供。 文档中的许多文章都参考了这些示例。 Visual Studio 不会再安装它们。 相反，GitHub 上提供了存储库。 下表包含每个示例的说明，以及指向存储库中示例目录的链接。

[!INCLUDE[note_security_samplecode](includes/note_security_samplecode_md.md)]

## <a name="atl-samples"></a>ATL 示例

### <a name="atl-samples---advanced"></a>ATL 示例 - 高级

| 示例名称 | 描述 |
|--|--|
| [ActiveDoc](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 演示如何实现活动文档服务器 (Active Document Server)。 |
| [Async](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 通过 URL 异步下载数据。 |
| [ATLButton](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 创建一个根据自身的状态用三种不同的位图显示自身的按钮。 |
| [ATLDuck](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 演示如何与 ATL 控件一起使用连接点。 |
| [ATLSecurity](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 演示如何使用 ATL 安全类来检查安全设置。 |
| [ATLTraceTool](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 显示由 `ATLTRACE2` 宏生成的输出。 |
| [“连接”](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 说明如何在多线程环境中实现和使用连接点（IConnectionPointContainer 和 IConnectionPoint 接口）。 |
| [CThreadPool](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 演示如何在应用程序中使用线程池，以及实现线程池可以如何提高应用程序的性能。 |
| [DCOM](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 演示如何从运行于不同计算机上的多个客户端调用 COM 对象（在 Windows 服务中实现）。 |
| [MFCATL](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 说明如何能在 MFC 服务器 EXE 中使用 ATL COM 对象。 |

### <a name="atl-samples---controls"></a>ATL 示例 - 控件

| 示例名称 | 描述 |
|--|--|
| [ATLFire](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Controls) | 演示如何用 ATL 生成有窗口控件。 |
| [CDInfo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Controls) | 播放 CD 乐曲并在工具提示和饼图显示中显示有关这些曲目的信息。 |
| [Circ](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Controls) | 创建一个说明属性页并绘制圆形的控件。 |
| [多边形](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Controls) | 生成一个实现自定义属性、事件、属性页和对象安全的控件。 |
| [SubEdit](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Controls) | 创建一个具有超类的 Windows 控件。 |

### <a name="atl-samples---general"></a>ATL 示例 - 常规

| 示例名称 | 描述 |
|--|--|
| [ATLCollections](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 说明 `ICollectionOnSTLImpl` 和 `CComEnumOnSTL` 的使用及自定义复制策略类的实现。 |
| [ATLCon](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 说明简单的控件容器。 |
| [ATLSafeArray](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 演示如何使用 `CComSafeArray` 创建并维护 `SAFEARRAY`；还演示如何将 `SAFEARRAY` 从组件传递到脚本。 |
| [AutoThread](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 演示如何使用 `CComAutoThreadModule` 类。 |
| [Beeper](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 实现 `BSTR` 的集合/枚举的分离式接口。 |
| [CircColl](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 使用 ATL 和标准 C++ 库实现对象的集合/枚举。 |
| [COMMap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 演示带有编译器 COM 支持的 COM 接口映射项宏。 |
| [CustomString](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 演示如何使用 `CStringT` 的自定义内存分配器来提高多线程应用程序的性能。 |
| [DispSink](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 演示如何在调度接口上使用连接点。 |

### <a name="atl-samples---oledb---consumer"></a>ATL 示例 - OLEDB - 使用方

| 示例名称 | 描述 |
|--|--|
| [CatDB](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) | 显示 OLE DB 提供程序的架构信息，如表和列。 |
| [DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) | 演示一个中级应用程序，它依赖 `CManualAccessor` 类来完全控制应用程序的数据绑定。 |
| [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) | 演示如何使用动态访问器和架构行集合类从数据库中读取元数据。 |
| [MultiRead](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) | 使用多个线程读取数据库中的表。 |

### <a name="atl-samples---oledb---provider"></a>ATL 示例 - OLEDB - 提供方

| 示例名称 | 描述 |
|--|--|
| [AdvancedPV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider) | 实现可更新的 OLE DB 提供程序。 演示一些高级技术。 |
| [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider) | 实现可更新（读/写）的 OLE DB 提供程序。 |

## <a name="clr-and-language-samples---windows-forms"></a>CLR 和语言示例 - Windows 窗体

| 示例名称 | 描述 |
|--|--|
| [BirthdayPicker](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language/Windows%20Forms) | 演示如何在 C++ 应用程序中使用 .NET Framework 资源机制。 还演示一些常见的 Window 窗体组件。 |
| [计算器](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language/Windows%20Forms) | 使用 C++ 和 .NET Framework Windows 窗体类实现一个简单的袖珍计算器。 |
| Scribble（使用 MFC） | Scribble 示例的 MFC 实现，进行了更新和扩展以包括新的 .NET 功能。 |
| [Scribble（Windows 窗体）](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language/General) | Scribble 示例的 Windows 窗体实现，进行了更新和扩展以包括新的 .NET 功能。 |
| [STLCLR](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/CLR/stlclr/StlClr%20Sample) | 演示一些可在使用 STL/CLR 库时使用的功能。 |

## <a name="com-events-samples"></a>COM 事件示例

| 示例名称 | 描述 |
|--|--|
| [COMEvents](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples) | 演示使用 COM 的事件处理。 |

## <a name="comtypelibfor7-samples"></a>ComTypeLibfor7 示例

| 示例名称 | 描述 |
|--|--|
| [ACDual](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 向自动化应用程序添加双重接口。 |
| [ADOSamp](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 实现三层客户端/服务器应用程序。 |
| [AllInOne](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 使用 ATL 实现一种服务器，它公开 STL 集合，并由 MFC 应用程序中的编译器 COM 支持控制。 |
| [COMMap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 演示带有编译器 COM 支持的 COM 接口映射项宏。 |
| [“连接”](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 演示如何在多线程环境中使用和实现连接点（`IConnectionPointContainer` 和 `IConnectionPoint` 接口）。 |
| [DCOM](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 演示如何从运行于不同计算机上的多个客户端调用 COM 对象（在 Windows 服务中实现）。 |
| [FreeThrd](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 演示带有编译器 COM 支持的多线程客户端和自由线程服务器。 |
| [InProc](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 演示带有编译器 COM 支持的进程内自动化服务器应用程序。 |
| [Labrador](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 实现一个没有任何用户接口的 EXE 服务器。 |
| [MFCCalc](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 演示带有编译器 COM 支持的自动化服务器应用程序。 |

## <a name="compiler-samples"></a>编译器示例

### <a name="compiler-samples---general"></a>编译器示例 - 常规

| 示例名称 | 描述 |
|--|--|
| [ccWrapper](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Compiler) | 演示如何将 C/C++ 编译器标志从其他编译器映射到 Visual C++ 编译器 (cl.exe) 中。 |

### <a name="compiler-samples---masm"></a>编译器示例 - MASM

| 示例名称 | 描述 |
|--|--|
| [EuclidStep1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Compiler/MASM) | 纯 C 项目，它演示了用于查找最大公约数的欧几里得算法。 |
| [EuclidStep2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Compiler/MASM) | EuclidStep1 的扩展，它是 C 与 MASM 混合编程的项目。 欧几里得算法的核心从 `.c` 文件移到 .`.asm` 文件，并且 `.c` 文件调用 `.asm` 文件     。 |
| [PrimesStep1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Compiler/MASM) | 纯 C 项目，它演示了用于查找质数的埃拉托色尼斯筛法。 |
| [PrimesStep2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Compiler/MASM) | PrimesStep1 的扩展，它是 C 和 MASM 混合编程的项目，该项目将核心算法移到 `.asm` 文件  。 |
| [PrimesStep3](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Compiler/MASM) | PrimesStep2 的扩展，它添加一个 C 头文件和一个 `.asm` 包含文件，分别用来声明外部函数和全局数据结构  。 |

## <a name="crt-samples"></a>CRT 示例

| 示例名称 | 描述 |
|--|--|
| [CPUID](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt) | 确定正在运行的 CPU 的性能。 |
| [CRT_Dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt) | 阐释 C 运行库的基本调试功能。 |
| [CRT_Dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt) | 说明 C 运行时调试挂钩函数。 |
| [DFACObjs](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt) | 演示如何使用 _CrtDoForAllClientObjects C 运行时函数来循环访问客户端对象的链接列表。 |
| [Report](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt) | 阐释 C 运行时调试报告函数。 |
| [RTC](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt) | 说明运行时错误检查功能。 |
| [SecureCRT](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt) | 本示例演示了如何升级原本使用已被否决的 CRT 函数的代码，以提高代码安全性。 |

## <a name="debugging-samples"></a>调试示例

| 示例名称 | 描述 |
|--|--|
| [EEAddIn](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples) | 使用“表达式计算器外接程序 API”来扩展本机调试器表达式计算器。 |

## <a name="fusion-samples"></a>合成示例

| 示例名称 | 描述 |
|--|--|
| [TraceMan](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples) | 提供有关与应用程序相关的程序集的信息，以及以可读的形式提供这些程序集在本机合成缓存中的状态的信息。 |

## <a name="hilo-sample"></a>Hilo 示例

| 示例名称 | 描述 |
|--|--|
| [Hilo](https://github.com/Microsoft/VCSamples/tree/master/VC2013Samples/Hilo) | Hilo 是一系列文章和示例应用程序。 它们演示了如何使用 Windows 7、Visual Studio 和 C++ 构建高性能的响应式客户端应用程序。 Hilo 提供源代码和指南，有助于你设计和开发引人注目的触控 Windows 应用程序。<br/><br/>此示例已针对 Visual Studio 2013 进行了更新。 它包括 AsyncLoaderMemoryManager.cpp 文件（第 36 行和第 37 行）的热修复，解决了常见的崩溃问题  。 |

## <a name="international-samples"></a>国际示例

| 示例名称 | 描述 |
|--|--|
| [IME](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/International) | 演示如何控制输入法编辑器模式以及如何实现 IME 级别 3。 |
| [SatDLL](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/International) | 演示在 Win32 应用程序中实现多语言资源的推荐方法。 |
| [UniRes](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/International) | 说明 Unicode 资源文件的用法。 |

## <a name="language-samples---general"></a>语言示例 - 常规

| 示例名称 | 描述 |
|--|--|
| [Data](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language) | 演示对 SQL 数据库的简单访问。 |
| [MEDriver](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language) | 说明如何通过从 COM 服务器的类型库自动生成的 .NET Framework 包装器使用 COM 事件（从非托管 COM 服务器激发）。 |
| [Nile](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language) | 演示 ASP.NET Web 窗体和 ASP.NET Web 服务。 |
| [QStat](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language/General) | 演示如何创建一个 DLL 来包装对 COM 对象的访问并将它的功能向 .NET Framework 客户端公开。 |
| [Scribble](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language/General) | 演示如何使用 C++/CLI 和 .NET Framework 类开发 Windows 窗体 MDI 应用程序。 |
| [TilePuzzle](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language/General) | 演示托管组件（用 C++ 和 C# 编写）和本机组件（使用 COM 特性用 C++ 编写）之间的互操作性。 |

## <a name="mfc-samples"></a>MFC 示例

### <a name="mfc-samples---advanced"></a>MFC 示例 - 高级

| 示例名称 | 描述 |
|--|--|
| [Collect](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 演示 MFC C++ 基于模板的集合类和标准的预生成集合类。 |
| [Cube](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 使用 MFC 设备上下文以及 OpenGL 的资源上下文的 OpenGL 应用程序。 |
| [DLLHusk](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 将基础类库的 DLL 版本与应用程序和自定义 DLL 共享。 |
| [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 可被静态或动态链接到 Microsoft 基础类库的常规 DLL。 |
| [MTGDI](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 使用框架的文档和视图单文档界面 (SDI) 支持，演示如何在多个线程间共享 GDI 资源。 |
| [MTMDI](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 多线程说明，其中在单独的用户界面线程中处理用户界面事件。 |
| [MTRecalc](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 多线程说明，其中在辅助线程中执行重新计算。 |
| [Mutex](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 基于对话框的应用程序，它创建两个 `CWinThread` 对象，并在用户的控制之下将它们用于执行任务。 |
| [Speakn](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 演示使用用户定义资源的多媒体声音。 |

### <a name="mfc-samples---controls"></a>MFC 示例 - 控件

| 示例名称 | 描述 |
|--|--|
| [Button](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 演示就地活动菜单、常用属性页和“关于”框控件选项的使用。 |
| [Circ](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 说明 ActiveX 控件的基础功能。 其中包括控件绘制、常用和自定义属性、常用和自定义事件、颜色和字体的使用、常用字体属性页、默认属性页和版本控制。 |
| [CmnCtrl](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 演示 MFC 在 wiprlhext 上提供的一些新控件：命令链接按钮 (`CButton`)、分页控件 (`CPagerCtrl`)、拆分按钮 (`CSplitButton`) 以及网络地址控件 (`CNetAddressCtrl`)。 |
| [Contain](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 说明一个可视化编辑容器应用程序。 |
| [Image](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 演示如何使用 MFC 生成能够异步下载数据的 ActiveX 控件。 |
| [Licensed](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 强制使用设计时和运行时许可证的控件。 |
| [本地化](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 具有本地化用户界面的控件，该用户界面演示如何使用单独的类型库和资源动态链接库 (DLL) 进行本地化。 |
| [NetAddr](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 演示 Windows Vista“网络地址验证工具”控件的使用。 |
| [Pal](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 显示调色板颜色的控件。 它演示只读属性、永久性 Get/Set 属性、永久性参数化属性和图片属性。 |
| [Push](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 从 Windows 所有者描述的按钮控件创建子类的控件。 它演示常用属性、自定义事件和图片容器。 |
| [RegSvr](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 说明自注册代码的调用。 |
| [SpinDial](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 一个具有可视的数值调节钮外观的控件，它用来说明属性页数据验证。 |
| [TestHelp](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 具有自己的帮助文件和工具提示的 ActiveX 控件。 |
| [时间](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 在运行时不可见并按设定的时间间隔引发计时器事件的控件。 说明通知函数和环境属性。 |
| [XList](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 从 Windows 列表框创建子类的控件，它显示文本或位图项。 |

### <a name="mfc-samples---general"></a>MFC 示例 - 常规

| 示例名称 | 描述 |
|--|--|
| [ClipArt](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | ClipArt 目录包含可用于自定义应用程序外观的示例资源。 |
| [CmnCtrl1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 演示如何使用 MFC 类（第 1 部分）创建和更改 Windows 公共控件的样式。 |
| [CmnCtrl2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 演示如何使用 MFC 类（第 2 部分）创建和更改 Windows 公共控件的样式。 |
| [CTaskDialog](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 演示 `CTaskDialog` 类的各种功能。 |
| [CtrlBars](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 自定义工具栏和状态栏、对话栏和浮动选项板。 |
| [CtrlTest](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 所有者描述列表框和菜单、自定义控件 (Custom Control)、位图按钮和数值调节钮控件 (Spin Control)。 |
| [DBVList](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 使用 `CListView` 和 `CDaoRecordset` 类实现虚拟列表视图功能，该功能可用于列表视图公共控件。 |
| [DIBLook](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 说明 DIB 和调色板的使用。 |
| [DlgCbr32](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 将工具栏和状态栏添加到基于对话框的应用程序。 |
| [DlgTempl](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 说明对话框模板的动态创建。 |
| [DockTool](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 拖动和浮动可停靠的工具栏。 |
| [Dynamenu](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 动态修改菜单中的项列表；处理在编译时未知的命令；以及更新此类命令的状态栏命令提示。 |
| [FileDlgWatcher](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 创建一个自定义对话框，该对话框演示在创建 `CFileDialog` 时会生成的事件。 |
| [Hello](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 演示带有菜单和“关于”框的单个应用程序窗口。 |
| [HelloApp](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 最简单的 MFC 示例，该示例演示如何用少量的代码行获取要显示在屏幕上的一个窗口。 |
| [ListHdr](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 演示如何使用公共控件 MFC 类 `CListCtrl` 和 `CHeaderCtrl`。 |
| [MDI](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 未使用文档和视图的 MDI 应用程序。 |
| [MDIDocVw](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 使用文档/视图体系结构的 MDI 示例的更新版本。 |
| [MMXSwarm](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 演示如何使用 `CImage`、`__m64` 数据类型和设备无关位图 (DIB)。 |
| [Modeless](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 演示如何将 MFC `CDialog` 对象作为无模式对话框使用。 |
| [Multipad](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 简单的文本编辑器，用户可用它一次打开和编辑多个文本文件。 |
| [Npp](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 演示如何实现类似于记事本的接口 (SDI) 应用程序。 可利用它编辑文本消息，并通过 Windows 消息 API 或 MAPI 将它们发送给其他用户或其他系统。 |
| [PropDlg](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 属性表（对话框）。 |
| [RowList](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 阐释列表视图中公共控件中的整行选择。 |
| [Scribble](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 提供 MFC 广泛功能的简单说明。 |
| [SimpleImage](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 说明如何加载、调整大小、转换和保存图像。 |
| [SnapVw](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 说明如何在 MDI 子框架窗口中使用属性页。 |
| [Spiro](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 说明如何使用 `CImageList` 以及如何在需要动画效果的应用程序中使用内存显示上下文的游戏。 |
| [Tracker](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 演示各种 `CRectTracker` 样式和选项。 |
| [VariantUse](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 说明变量数据类型的使用。 |
| [ViewEx](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 多个视图、滚动视图和拆分窗口。 |

### <a name="mfc-samples---internet"></a>MFC 示例 - Internet

| 示例名称 | 描述 |
|--|--|
| [DHTMLExplore](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/internet) | 演示如何处理 DHTML 事件和使用 DHTML DDX。 |
| [HTMLEdit](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/internet) | 包装 Internet Explorer MSHTML 编辑控件。 |
| [MFCIE](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/internet) | 演示 MFC `CHtmlView` 和 `CReBar` 类。 |
| [计划程序](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/internet) | 演示如何使用 Visual C++ 库类创建基于 HTML 的对话框。 |

### <a name="mfc-samples---ole"></a>MFC 示例 - OLE

| 示例名称 | 描述 |
|--|--|
| [ACDual](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 说明如何向基于 MFC 的自动化服务器添加双重接口支持。 |
| [AutoClik](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 阐释自动化功能。 包括 AUTODRIV，一个驱动 AUTOCLIK 示例应用程序的简单自动化客户端应用程序。 |
| [CalcDriv](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 自动化客户端。 |
| [DrawCli](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 功能完善的面向对象的绘图应用程序，也是 ActiveX 可视化编辑容器。 |
| [HierSvr](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 说明具有 OLE 拖放功能的服务器应用程序。 |
| [InProc](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 可作为客户端地址空间中的 DLL 加载的进程中自动化服务器。 |
| [IPDrive](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 驱动 INPROC 示例应用程序的简单自动化客户端应用程序。 |
| [MFCBind](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 演示如何创建活动文档（之前称为 DocObject）容器。 |
| [MFCCalc](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 实现简单计算器的自动化服务器。 |
| [OClient](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 具有拖放功能的 ActiveX 可视化编辑容器应用程序。 |
| [OLEView](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 通过自定义 OLE 接口实现 OLE 对象浏览器。 |
| [SuperPad](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 演示使用 CEditView 编辑文本的可视化编辑服务器。 |
| [TstCon](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 使用 MFC 的 OLE 嵌入支持实现 ActiveX 控件容器。 可以使用 TSTCON 测试 ActiveX 控件、更改它们的属性以及调用它们的方法。 |
| [WordPad](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 使用 MFC 的 Rich Edit 控件支持来创建基本的字处理应用程序。 |

### <a name="mfc-samples---utility"></a>MFC 示例 - 实用工具

| 示例名称 | 描述 |
|--|--|
| [GUIDGen](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/utility) | 一种简单的基于对话框的 MFC 应用程序，它可生成全局唯一标识符。 |
| [Makehm](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/utility) | 在资源标识和帮助上下文之间建立映射的控制台应用程序。 |

### <a name="mfc-samples---visual-c-2008-feature-pack"></a>MFC 示例 - Visual C++ 2008 功能包

| 示例名称 | 描述 |
|--|--|
| [CustomPages](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何将自定义页面添加到“自定义工具栏”对话框中。 |
| [DesktopAlertDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何实现桌面通知对话框（类似于即时消息应用程序的对话框）。 |
| [DlgToolTips](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何为对话框上的控件实现高级工具提示。 |
| [DrawClient](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何通过编辑容器支持将功能区的支持集成到绘图应用程序中。 |
| [DynamicMenu](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何在运行时对菜单栏上的菜单以及弹出菜单中进行动态更新。 |
| [资源管理器](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何实现类似于文件资源管理器的文件系统资源管理器。 它具有类似的用户界面元素和功能。 |
| [IEDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何实现与 Internet Explorer 具有类似用户界面元素和功能的应用程序。 |
| [MDITabsDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何创建一个使用新的选项卡式 MDI 文档界面（而不是传统 MDI 子窗口）的应用程序。 |
| [MenuSubSet](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何在应用程序启动时动态移除特定菜单项和子菜单。 |
| [MSMoneyDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何使用 MFC 创建与 Microsoft Money 类似的用户界面。 |
| [MSOffice2007Demo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何实现与 Office 2007 应用程序具有类似用户界面元素和有限类似功能的编辑器应用程序。 MSOffice2007Demo 示例实现完整的功能区用户界面，该界面与 Office 2007 应用程序类似。 某些功能区元素已连接到应用程序中的功能。 |
| [NewControls](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示在 MFC 中实现的许多控件的功能。 这些控件包括可自定义的按钮、颜色选取器控件和调色板、字体选择器、图像编辑器、属性网格、屏蔽编辑控件以及 shell 列表和树控件。 |
| [OutlookDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何创建与 Outlook 2003/2007 类似的应用程序。 |
| [OutlookMultiViews](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何在 SDI 应用程序中单个文档上的多个视图之间进行切换。 该示例使用 Outlook 栏控件列出了可用视图，并在它们之间进行切换。 |
| [OwnerDrawMenu](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 阐释如何动态绘制弹出菜单项。 |
| [PaletteDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 阐释如何创建一个具有所有者描述信息区域的多列工具栏。 单击“标准”工具栏上的“2”、“3”或“4”按钮可在运行时更改自定义工具栏的列数。 |
| [PropSheetDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示以下类型的属性表控件：简单、选项卡在左边、树控件在左边、OneNote 样式的选项卡、项列表在左边。 |
| [RebarTest](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示一个承载工具栏的可自定义的 Rebar 控件。 |
| [RibbonGadgets](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示可承载于功能区控件中的各种控件。 在主框架底部，你可以找到包含源代码文本的“源代码”窗口，此源代码文本概述了如何创建特定小工具。 |
| [RibbonMDI](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何将功能区控件与多文档界面结合使用。 |
| [RollupPane](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示一个浮动的“信息”窗格，该窗格会自动上卷。 你可以按浮动窗格标题上的固定按钮以打开和关闭卷动功能。 |
| [SetPaneSize](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何以编程方式设置停靠窗格大小。 |
| [滑块](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何实现一个承载外部控件的工具栏按钮。 |
| [StateCollection](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何实现为菜单栏、工具栏和停靠窗口保存和加载不同状态的应用程序。 |
| [StatusBarDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何将各种高级控件添加到状态栏中。 |
| [TabbedView](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何创建一个包含多个选项卡式视图（如 Excel 工作簿中的选项卡）的视图。 |
| [TabControl](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 使用不同的属性和视觉管理器演示 MFC 选项卡控件及其具有的不同外观。 |
| [TasksPane](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 使用各种属性和虚拟管理器演示 MFC 任务窗格类及其不同的外观。 |
| [ToolbarDateTimePicker](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何将日期/时间选取器控件与工具栏集成 |
| [ToolTipDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何使用高级 MFC 工具提示功能。 |
| [TrayMenu](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 说明使用带有系统托盘图标的 MFC 控件条菜单的能力。 它类似于显示器右下角的通知图标。 |
| [VisualStudioDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何实现具有 Visual Studio 的许多相同用户界面特性和功能的应用程序。 演示了许多 Visual Studio 用户界面元素，包括可自定义的停靠菜单栏、工具栏和窗口。 |
| [WordPad](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何实现模仿写字板功能（包括用户界面元素和某些功能）的应用程序。 |
| [WorkSpaceToolBar](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何将工具栏添加到停靠窗格中。 它与 Visual Studio 中的解决方案资源管理器中的工具栏类似。 |

### <a name="mfc-samples---windows-touch"></a>MFC 示例 - Windows Touch

| 示例名称 | 描述 |
|--|--|
| [GestureDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/WindowsTouch) | 演示 MFC 中的 Windows Touch 支持（需要触控硬件）。 |
| [TouchDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/WindowsTouch) | 演示 MFC 中的 Windows Touch 支持（需要触控硬件）。 |

## <a name="odbc-samples"></a>ODBC 示例

| 示例名称 | 描述 |
|--|--|
| [odbcsql](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/ODBC%20Database%20sample) | 该示例演示了如何使用 ODBC API 连接和访问数据库。 |

## <a name="os-samples"></a>OS 示例

| 示例名称 | 描述 |
|--|--|
| [GetImage](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples) | 演示 Windows 图像采集 (WIA) 应用程序编程接口 (API)。 |

## <a name="unix-samples"></a>Unix 示例

| 示例名称 | 描述 |
|--|--|
| [Unix - ccWrapper](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples) | 演示一种包装器，该包装器可将标志从 Sun Forte 和 gcc 编译器映射到 Microsoft Visual C++ 编译器 (cl.exe) 中。 |

## <a name="windows-8-samples"></a>Windows 8 示例

Windows 8 示例包包括为 Windows 8 开发和更新的所有应用代码示例。 示例包提供了一种一次下载所有示例的便捷方法。 此示例包中的示例可用于 C#、C++、VB.NET 和 JavaScript。 Windows 示例库包含代码示例，用于演练 Windows 8 和 Windows Server 2012 中提供的各种新编程模型、平台、功能和组件。 这些可下载的示例包含 Visual Studio 解决方案 (sln) 文件、源文件、资产、资源，以及成功编译和运行所必需的元数据  。

还包括其他信息，例如每个示例中演示的编程模型、平台、语言和 API。 请参阅 Windows 开发人员中心中的 Windows 8 文档提供的指南、教程和参考文章。 这些示例按原样提供，以演示 Windows 8 和 Windows Server 2012 的编程模型和功能 API 的功能。

| 示例名称 | 描述 |
|--|--|
| [后台传输示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了 Windows 运行时应用程序后台传输 API 的低能耗、低成本的灵活行为。 提供的示例方案涵盖文件下载和上传。 |
| [CryptoWinRT 示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用新的加密 API。 |
| [打印示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示应用如何集成 Windows 打印体验。 该示例中的演示方案包括：使用超级按钮和“打印”合约从应用打印以及从应用内打印的体验等。 |
| [HttpClient 示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 HttpClient 类和 IXMLHTTPRequest2 接口，通过 Windows 运行时提供的网络功能，从 HTTP 服务器上传和下载各种类型的内容。 |
| [加速度传感器示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 `Windows.Devices.Sensors.Accelerometer` API。 此示例允许用户查看 3 轴加速度传感器的 X 轴、Y 轴和 Z 轴的加速力。 可以选择三种方案之一。 |
| [帐户头像名称示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了获取当前登录的用户名的不同方法。 它还演示了如何获取和设置用于用户磁贴的图像。 |
| [应用设置示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 ApplicationSettings API 和“设置”浮出控件将应用的设置 UI 与“设置”超级按钮集成。 该示例使用 `Windows.UI.ApplicationSettings` 命名空间和 `WinJS.UI.SettingsFlyout`。 |
| [适用于相机的 Windows 应用商店设备应用示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何为相机创建 Windows 应用商店设备应用。 Windows 应用商店设备应用由 IHV 或 OEM 提供，以区分特定相机的拍摄体验。 |
| [C++ 简单博客读取器入门示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 该示例演示如何使用 XAML 在本机 C++ 中开发 Windows 应用商店应用以定义用户界面。 它是 Windows 开发人员中心上讨论的应用程序的完整工作版本。 |
| [读取和写入数据示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 DataReader 和 DataWriter 类来存储和检索数据。 |
| [应用程序数据示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Windows 运行时应用程序数据 API 存储和检索特定于每个用户和 Windows 应用商店应用的数据。 应用程序数据包括会话状态、用户首选项和其他设置。 |
| [自定义驱动程序访问示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 CreateDeviceAccessInstance 和 IDeviceIoControl 访问专用设备。 |
| [XAML ListView 和 GridView 控件示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 GridView 和 ListView 控件。 |
| [动画指标示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 `Windows.UI.Core`.AnimationMetrics 中的动画指标 API 访问用于定义 Windows 动画库中的动画的原始参数。 |
| [播放管理器 msAudioCategory 示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何为音频视频 (AV) 流选择正确的 msAudioCategory 类别，将其配置为音频播放流。 |
| [XAML DirectX 3D 射击类游戏示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在 C++ 应用中使用 DirectX（Direct3D 11.1、Direct2D、XInput 和 XAudio2）和 XAML 实现简单的第一人称 3D 游戏。 XAML 用于抬头显示和游戏状态消息。 |
| [XAML 滚动、平移和缩放示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 ScrollViewer 控件平移和缩放。 |
| [XAML FlipView 控件示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 FlipView 控件使用户能够浏览集合。 |
| [陀螺测试仪传感器示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 `Windows.Devices.Sensors.Gyrometer` API。 此示例允许用户查看 3 轴陀螺仪的 X 轴、Y 轴和 Z 轴的角速度。 |
| [适用于打印机的设备应用 SDK 示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何为打印机创建设备应用，可通过“磁贴”合约、printTaskSettings 合约和 backgroundTask 显示的 toast 激活打印机，以响应打印驱动程序事件。 |
| [后台任务示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Windows 运行时后台任务 API 创建和注册后台任务。 后台任务由系统或时间事件触发，并且可以受一个或多个条件的约束。 |
| [StreamSocket 示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示使用 Windows 运行时提供的网络功能的 StreamSocket 类的基础知识。 示例的客户端组件创建 TCP 套接字以建立网络连接、使用套接字发送数据等。 |
| [计划的通知示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何为应用使用计划磁贴更新、定期磁贴更新和 toast 通知。 此功能使你能够指定提供通知的确切时间，即使应用未运行也可实现。 |
| [播放管理器助手示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何为音频视频流选择正确的 msAudioCategory 类别，将其配置为音频播放流。 |
| [OrientationSensor 示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 `Windows.Devices.Sensors.OrientationSensor` API。 它允许用户查看反映当前设备方向的旋转矩阵和四元值。 |
| [文件访问示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何创建、读取、写入、复制和删除文件、如何检索文件属性，以及如何跟踪文件或文件夹以便应用可以再次访问该文件。 该示例使用 `Windows.Storage` 和 `Windows.Storage.AccessCache` API。 |
| [可移动存储示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 可移动存储示例演示如何将文件传输到可移动存储设备或从可移动存储设备传输文件。 此示例需要连接到系统的可移动存储设备，如相机、媒体播放器、移动电话或 U 盘。 |
| [XAML SurfaceImageSource DirectX 互操作示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 `SurfaceImageSource` 在 XAML 应用中包含 DirectX 内容。 此示例同时使用 C++ 和 C#。 |
| [与 WebSocket 连接的示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在连接的 Windows 应用商店应用中使用 WebSocket。 该示例介绍了基本功能，例如如何建立连接、发送和接收数据以及关闭连接。 |
| [配置媒体键示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在键盘上配置硬件媒体键。 然后，如何使用配置的键通过按或单击“播放”、“暂停”、“停止”等来控制音视频流。 |
| [XAML 个性动画示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在应用中使用内置的个性动画。 |
| [Toast 通知示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 该示例演示如何使用 Toast 通知：在屏幕右上角显示为弹出通知的通知。 用户可以选择 toast（触摸或单击）以启动关联的应用。 |
| [选取联系人应用示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用选取联系人选择一个或多个联系人。 它还包括选取联系人 API 的基本实现，以演示如何向用户显示联系人列表。 |
| [DirectX 大理石迷宫游戏示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 DirectX 构建基本 3D 游戏。 此游戏是一个简单的平衡球迷宫游戏，玩家需要使用倾斜控件滚动大理石通过各种各样的迷宫来完成闯关。 |
| [DirectX 明信片应用示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何利用 DirectX 和 XAML 的互操作性，使用 DirectX 和 C++ 来实现简单的 Windows 应用商店应用以创建明信片。 |
| [DirectX 3D 射击类游戏示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在 C++ 应用中使用 DirectX（Direct3D 11.1、Direct2D、XInput 和 XAudio2）实现简单的第一人称 3D 游戏。 |
| [XAML AppBar 控件示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 AppBar 控件向用户显示导航、命令和工具。 应用栏默认处于隐藏状态，用户可从屏幕的上边缘或下边缘轻扫来唤出该应用栏。 |
| [日期和时间格式设置示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在 `Windows.Globalization.DateTimeFormatting` 命名空间中使用 DateTimeFormatter 类根据用户的首选项显示日期和时间。 |
| [辅助磁贴示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何固定和使用辅助磁贴。 该磁贴可直接访问应用中的特定、非默认部分或体验，例如已保存的游戏或社交网络应用中的特定好友。 |
| [Input Touch 命中测试示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例使用多边形拼图合集来演示如何处理指针输入、实现 Input Touch 的自定义命中测试以及如何使用 C++ 和 DirectX 在 Windows 应用商店应用中处理操作。 |
| [网络信息示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Windows 运行时网络信息 API。 |
| [输入简化墨迹示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在 Windows 应用商店应用中使用墨迹功能。 |
| [StorageDataSource 和 GetVirtualizedFilesVector 示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何检索和显示用户图库中的图像。 |
| [基于边缘的手势调用示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 `EdgeGesture` 类侦听在基于边缘的 UI 中发生的事件。 |
| [检查当前会话是否为远程会话示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 以下示例演示了 `Windows.System.RemoteDesktop` API 的用法。 |
| [应用程序资源和本地化示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用应用程序资源将可本地化内容与应用程序代码分开。 该示例使用 `Windows.ApplicationModel.Resources.Core` 和 `Windows.Globalization` 命名空间，以及 `WinJS.Resources`。 |
| [上下文菜单示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何创建上下文菜单以及如何替换文本的默认上下文菜单。 此示例使用 `Windows.UI.Popups` API，包括 PopupMenu 和 oncontextmenu 事件。 |
| [地理位置示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 地理位置示例演示如何使用地理位置 API 获取用户电脑的地理位置。 应用可以使用地理位置 API 获取位置一次，也可以持续跟踪位置。 |
| [消息对话框示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 MessageDialog 显示对话框、设置命令及其操作以及更改默认按钮。 `Windows.UI.Popups` 命名空间包含 MessageDialog 类。 |
| [MediaStreamSource 媒体扩展示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在 Windows 应用商店应用中支持 Microsoft Silverlight MediaStreamSource 概念。 |
| [DirectWrite 竖排文字示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例使用 DirectWrite 和 Direct2D 在自定义布局形状中正确显示竖排文字。 |
| [DXGI 交换链旋转示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示 IDXGISwapChain1::SetRotation 方法，以及如何将该方法与 prerotated 内容结合使用以提高演示性能。 |
| [Direct2D 自定义图像效果示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用标准像素、顶点和计算着色器实现自定义 Direct2D 效果。 |
| [DirectX 触控输入示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在使用 Direct3D 编写的 C++ 应用中的 3D 环境中进行触屏和鼠标导航。 |
| [XInput 游戏控制器示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在 C++ 应用中使用 XInput API。 它读取来自 Xbox 游戏控制器的输入，并显示有关模拟杆移动和按钮按下的数据。 |
| [Direct3D-Direct2D 互操作示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何与 Direct2D 和 DirectWrite 进行互操作，以将文本写入 Direct3D 呈现器目标。 它是创建抬头显示器和基于文本的读出（如游戏和 3D 应用中的评分面板）的有效方法。 |
| [联合示例（Windows 8）](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了 Windows 8 的基本 Windows 应用商店应用，该应用可以从 Web 服务检索源。 此示例目前以 JavaScript、C#、C++ 和 VB 编程语言提供。 |
| [应用磁贴和徽章示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用应用磁贴，该磁贴是应用在“开始”屏幕中的表示和启动点。 它还演示了如何使用该磁贴上的徽章。 它是应用在应用未运行时向用户中继状态信息的方法。 |
| [XAML 用户和自定义控件示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何创建和使用 XAML `UserControl` 元素并为项目创建自定义控件。 |
| [Direct3D 资源加载示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何通过 DirectX 为 C++ 应用加载 Direct3D 资源。 |
| [XAML ListView 和 GridView 自定义交互示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示 `ListView` 控件的交互模型。 |
| [XAML WebView 控件示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 `WebView` 控件显示 URL、加载 HTML、在 `WebView` 内与脚本交互以及使用 `WebViewBrush`。 |
| [罗盘传感器示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 `Windows.Devices.Sensors.Compass` API。 此示例允许用户将指南针读数视为磁北读数，并根据已安装的传感器将其视为真北值。 |
| [显示方向示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 `DisplayProperties` 类在应用中设置显示方向。 |
| [Direct2D 内插模式示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例显示 Direct2D 使用的各种内插模式。 |
| [全球化首选项示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 `Windows.System.UserProfile.GlobalizationPreferences` 类获取用户的全球化首选项。 它还演示如何使用 `GeographicRegion` 和 `Language` 类。 |
| [Direct2D 几何实现示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示多核几何镶嵌如何帮助缩短几何渲染的时间。 传统几何渲染的替代方法是使用不透明蒙版和网格，但在某些情况下几何渲染可能会更好。 |
| [语言字体映射示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 `Windows.Globalization.Fonts` 命名空间中的 `LanguageFontGroup` 类获取特定于语言的字体建议。 |
| [测斜仪传感器示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 `Windows.Devices.Sensors.Inclinometer` API。 此示例允许用户查看 3 轴测试仪的 X 轴、Y 轴和 Z 轴的倾斜角度。 |
| [XAML 高对比度样式示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了在应用中实现高对比度模式支持的各种技术。 让你的应用支持高对比度模式，这一点至关重要，可以帮助有视力障碍的用户快速访问你的应用。 |
| [输入设备功能示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何查询连接到用户设备的输入设备。 以及如何支持 Windows 应用商店应用的指针、触摸、笔/触笔、鼠标和键盘输入模式。 |
| [邮件客户端的 EAS 策略示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示邮件客户端如何检索设备信息并处理提供的 Exchange Active Sync (EAS) 策略。 Windows 应用商店应用可以配置其邮件客户端以符合给定的 EAS 策略。 |
| [DatagramSocket 示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示使用 Windows 运行时提供的网络功能的 `DatagramSocket` 类的基础知识。 示例的客户端组件创建 UDP 套接字，使用套接字发送和接收数据，并关闭套接字。 |
| [DirectWrite Hello World 示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 DirectWrite 和 Direct2D 将文本“Hello World”呈现到 `CoreWindow`。 |
| [压缩示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何从文件中读取结构化数据并将压缩数据写入新文件，以及如何读取压缩数据并将解压缩数据写入新文件。 许多应用程序都需要压缩和解压缩数据。 |
| [网络状态后台示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何通过使用 Internet 存在条件为网络状态更改事件注册后台任务处理程序来确定 Internet 连接配置文件中的更改。 |
| [应用包信息示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Windows 运行时打包 API 获取包信息。 用户以应用程序包的形式获取 Windows 应用商店应用。 Windows 使用应用包中的信息按用户安装应用。 |
| [LightSensor 示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 `Windows.Devices.Sensors.LightSensor` API。 此示例允许用户以 LUX 值的形式查看环境光线读数。 可选择以下两个方案之一：LightSensor 数据事件、当前光线传感器读数等。 |
| [移动宽带帐户预配示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Windows 8 移动宽带预配代理 API (`Windows.Networking.NetworkOperators.ProvisioningAgent`) 通过所需的连接信息和访问预配来配置 Windows 8。 |
| [媒体远程播放示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示远程播放 API。 该示例演示如何扩展媒体应用程序，将视频、音频和图像流式传输到本地网络上的其他设备。 |
| [Input Touch 键盘示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在自定义控件（非派生自平台控件）中自动启动触控键盘。 该示例实现需要键盘输入且非派生自标准 XAML 控件的自定义控件。 |
| [XAML 动画库示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何为元素设置动画，以及如何对动画应用缓动函数以实现各种效果。 |
| [对齐示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 已对齐的状态为四种可能的应用程序视图状态之一。 通过对齐应用将应用大小调整到 320 像素宽，使其可与其他应用共享屏幕。 通过对齐功能，可以同时看到两个应用。 |
| [转码媒体示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 `Windows.Media.Transcoding` API 在 Windows 应用商店应用中转码视频文件。 转码是数字媒体文件（如视频或音频文件）从一种格式转换为另一种格式。 |
| [XAML 二维转换示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用二维转换来修改元素在应用中的显示方式。 转换定义如何将点从一个坐标空间映射或转换到另一个坐标空间。 |
| [IXmlReader 和 IXmlWriter XML 数据读取写入示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此实例演示如何在 C++ 编写的 Windows 应用商店应用中使用 `IXmlReader` 和 `IXmlWriter`。 它们用于从平面 XML 格式的文本文件中读取和写入 XML 数据。 这些接口是 Windows Win32 和 COM API 的一部分，但受 Windows 运行时的支持。 |
| [使用捕获设备的媒体捕获示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 `MediaCapture` API 从捕获设备（如网络摄像机）捕获视频、音频和图片。 |
| [XAML 弹出窗口示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在项目中创建和使用 XAML 弹出窗口元素。 |
| [CameraCaptureUI 示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 `Windows.Media.Capture.CameraCaptureUI` API 显示用于捕获照片或视频的全屏 UI。 相机捕获 UI 提供从照片切换到视频的控件、用于拍摄延迟时间照片的计时器等。 |
| [XAudio2 音频文件播放示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示应用中的 XAudio2 用法。 |
| [Hilo C++ 示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 C++ 和 XAML 构建完整的 Windows 应用商店应用。 Hilo 照片示例为希望使用新式 C++、XAML 和 Windows 运行时创建 Windows 8 应用的 C++开发人员提供了有用指导。 |
| [DirectWrite 自定义文本呈现器示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何实现 DirectWrite 的自定义文本呈现器。 |
| [DirectWrite 字体枚举示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 DirectWrite 在用户设备上列出系统字体集合中的字体。 |
| [Direct2D 透视变换示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 `DrawBitmap` API 来显示应用透视变换的图像。 |
| [CameraOptionsUI 示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在设备应用中使用相机选项。 `CameraOptionsUI` API 显示用于调整照相机设置的 UI。 此示例需要一个网络摄像头。 |
| [XInput 音频控制器播放示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在应用中通过 XAudio2 回放到 XInput 设备，如耳机。 |
| [Direct2D 3D 转换效果示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了在 3D 空间中转换图像的不同方法。 |
| [Windows 帐户授权示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 `Windows.Security.Authentication.OnlineId` 命名空间的成员在委派模式下使用其 Microsoft 帐户对用户进行身份验证。 以及如何使用 REST 协议将获取的令牌发送到 Live Connect API。 |
| [数字格式设置和分析示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何 `Windows.Globalization.NumberFormatting` 命名空间中的 `DecimalFormatter`、`CurrencyFormatter`、`PercentFormatter` 和 `PermilleFormatter` 类。 它们用于显示和分析数字、货币和百分比值。 |
| [DXGI 提供和回收资源示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何通过 DirectX 在 C++ 应用中使用 DXGI `IDXGIDevice2::OfferResources` 和 `IDXGIDevice2::ReclaimResources` API。 |
| [Web 身份验证代理示例（Windows 8）](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示 Web 身份验证代理 WinRT API。 它允许你启用与 OAuth 提供商（如 Facebook、Google、微软和 Twitter）的单一登录 (SSO) 连接。 |
| [XAudio2 音频流效果示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例使用 XAudio2 和媒体基础 API 演示 C++ 应用程序中的音频流。 |
| [初始屏幕示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在 Windows 关闭其显示的初始屏幕时正确定位类似图像，从而模仿 Windows 为应用显示的初始屏幕。 |
| [SMS 后台任务示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何结合使用 Windows 8 移动宽带 SMS API (`Windows.Devices.Sms`) 与后台任务 API (`Windows.ApplicationModel.Background`) 以发送和接收短信。 |
| [短信发送、接收和 SIM 管理示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Windows 8 移动宽带 SMS API (`Windows.Devices.Sms`)。 |
| [试用应用和应用内购买示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Windows 应用商店提供的许可 API 来确定应用的许可证状态，或应用内购买中启用的功能。 |
| [Input Touch 键盘文本输入示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何启用触控键盘上的优化视图。 它的工作原理是借助 `WinJS.UI` 命名空间中的控件，以及借助 `TextBox` 和 `RichEdit` XAML 控件，使用输入范围和输入类型。 |
| [XAML 文本编辑示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在应用中使用文本输入控件。 |
| [线程池示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Windows 运行时线程池 API 异步运行工作项。 |
| [UI 自动化核心窗口提供程序示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何创建 Microsoft UI 自动提供程序。 它使有关 Windows 应用商店应用的编程信息可供可访问的技术（如屏幕阅读器）使用。 该示例是一个 Direct2D 应用程序。 |
| [XAML 辅助功能示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何向应用添加基本辅助功能支持。 |
| [播放列表示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何创建、保存、显示和编辑音频文件的播放列表。 此示例使用 `Windows.Media.Playlists` 命名空间中的类。 |
| [媒体服务器客户端示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用媒体服务器 API 创建媒体服务器客户端。 媒体服务器示例演示如何在本地网络上以编程方式浏览数字媒体服务器，并显示其所有视频文件。 |
| [Direct2D 杂志应用示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Direct2D、DirectWrite、Windows 映像组件 (WIC) 和 XAML 构建具有杂志类型演示文稿的应用。 |
| [移动宽带帐户和设备管理示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用移动网络运营商 (MNO) 使用的 Windows 8 移动宽带 API (`Windows.Networking.NetworkOperators`)。 它演示如何使用 MobileBroadbandAccount API 来检索和显示可用的移动宽带帐户。 |
| [邻近感应示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 `PeerFinder` 和 `ProximityDevice` 类与附近的计算机进行通信。 你可以使用 `Proximity` API 在点击手势期间交换小消息，或在对等应用之间设置套接字连接。 |
| [创建 Windows 运行时进程内组件示例 (C++CX) (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在 C++/CX 中创建用于 C++/CX、JavaScript 和 C# 客户端代码的组件。 OvenServer 项目包含名为 `Oven` 的运行时类，该类实现了 `IOven` 接口和 `IAppliance` 接口。 |
| [设备自动旋转首选项示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 `DisplayProperties` 类来处理和验证设备旋转事件。 |
| [实时通信示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用低延迟功能启用实时通信应用程序。 |
| [共享内容资源应用示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示一个应用如何与其他应用共享内容。 此示例使用来自 `Windows.ApplicationModel.DataTransfer` 命名空间的类。 |
| [“搜索”合约示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何允许用户在选择“搜索”超级按钮并打开“搜索”窗格时搜索你的应用。 还演示如何使用“搜索”窗格显示用户查询的建议。 |
| [原始通知示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用原始通知，这种通知也是推送通知，没有执行应用后台任务的关联 UI。 |
| [Direct2D 基础图像效果示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何加载图像、对图像应用高斯模糊效果，然后在 `Windows::UI::Core::CoreWindow` 中显示图像。 |
| [关于基元的 Direct2D 效果示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何将图像效果应用于 Direct2D 基元。 此示例使用 Direct2D 绘制圆角矩形，然后在矩形中间绘制 DirectWrite 文本。 然后，将效果图应用于 Direct2D。 |
| [ControlChannelTrigger StreamSocket 示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 该示例演示如何在 Windows 应用商店应用中使用 `ControlChannelTrigger` 类。 它使用 TCP `StreamSocket`，因此应用程序始终处于连接状态，并且始终可到达。 此示例演示如何使用后台网络通知。 |
| [ControlChannelTrigger StreamWebSocket 示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 该示例演示如何使用 `ControlChannelTrigger` 类使使用 StreamWebSocket 的 Windows 应用商店应用始终连接且始终可访问。 此示例演示如何使用后台网络通知。 |
| [关联启动示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何为文件类型或协议启动用户的默认应用。 你还可以了解如何使你的应用成为文件类型或协议的默认应用。 |
| [AtomPub 示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何从 Web 访问、创建、更新和删除联合内容源。 它使用 Atom 发布标准的 Windows 运行时实现。 |
| [证书注册示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在证书层次结构中创建和注册证书。 若要获取 Windows 8 的评估副本，请转到 Windows 8。 若要获取 Microsoft Visual Studio 2012 的评估副本，请转到 Visual Studio 2012。 |
| [剪贴板应用示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何应用使用剪贴板命令，包括复制、粘贴、剪切和移动。 此示例使用来自 `Windows.ApplicationModel.DataTransfer` 命名空间的类。 |
| [Direct2D 复合效果模式示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例显示了可从 Direct2D 获取的各种复合模式和混合模式。 |
| [Direct3D 平滑示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示使用法线贴图和像素级光照效果的凹凸处理。 |
| [日历详细信息和数学示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在 `Windows.Globalization` 命名空间中使用 `Calendar` 类，根据日历系统和用户的全球化首选项操作和处理日期。 |
| [设备枚举示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用设备枚举 API 查找可用设备和查找设备信息。 此示例提供了两种方案：在第一个方案中，设备枚举 API 用于查找特定的设备接口。 |
| [DirectWrite 段落文本示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 DirectWrite 和 Direct2D 将段落文本呈现给 `CoreWindow`。 以及如何对布局应用对齐和字符间距。 |
| [响应屏幕键盘的外观示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | [本文档是初步文档，可能会更改。] 此示例演示如何侦听和响应屏幕软键盘的外观。 在无键盘的设备上，将焦点提供给需要文本输入的元素时。 |
| [XAML 数据绑定示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了使用绑定类和绑定标记扩展的基本数据绑定技术。 |
| [Direct3D 教程示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 本示例教程包含五个课时。 它介绍了 Direct3D API 以及许多其他 DirectX 示例中使用的概念和代码。 |
| [Direct2D 效果照片调整应用示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例介绍了使用 Direct2D 效果的各种常见照片操作技术。 此示例分为多个部分。 第 1 课：演示使用 Direct2D 效果加载和绘制图像的基本知识。 |
| [Windows 音频会话 (WASAPI) 示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 演示如何使用 Windows 音频会话 API (WASAPI) 执行各种音频相关任务。 |
| [用户域名示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示与域相关的功能，这些功能由 `Windows.System.UserProfile` 命名空间的 `UserInformation` 类提供。 UserInformation 类使应用可以获取和设置有关用户的信息。 |
| [USSD 消息管理示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示使用 USSD 协议与支持 GSM 的移动宽带设备的网络帐户管理。 USSD 通常用于移动网络运营商 (MNO) 对移动宽带配置文件的帐户管理。 |
| [Bing 地图行程优化器示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 该示例演示如何使用 JavaScript 和 Visual C++，以及如何为名为 Bing 地图行程优化器的 Windows 8 创建应用。 Bing 地图行程优化器使用 JavaScript 来定义 UI，并使用 C++ 定义并行计算代价高昂的算法。 |
| [路径中的 Direct2D 和 DirectWrite 动画文本示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Direct2D 和 DirectWrite 沿动画非线性几何路径呈现文本字符串。 应用呈现“Hello, World!” 通过贝塞尔曲线以不同的语言重复多次。 |
| [Wi-Fi 热点身份验证示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Windows 8 移动宽带 API (`Windows.Networking.NetworkOperators`) 进行 Wi-Fi 热点身份验证。 使用此机制作为一种替代方法来为 Wi-Fi 热点配置静态凭据。 |
| [XAML 图像示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了使用图像控件和 BitmapImage 类在应用中显示和操作图像的各种技术。 |
| [HomeGroup 应用示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 `HomeGroup` 打开、搜索和共享文件。 此示例使用 `Windows.Storage.Pickers` 和 `Windows.Storage.KnownFolders`中的某些 `HomeGroup` 选项。 |
| [UI 对比度和设置示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在基本 C# 或 JavaScript 应用中使用 UI 设置 API。 |
| [文件夹枚举示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何列出某个位置内的顶级文件和文件夹。 （例如文件夹、设备或网络位置。）以及如何使用查询，通过将所有文件分成文件组，在一个位置列出全部列出。 |
| [文件选取器示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何通过允许用户通过文件选取器选择文件和文件夹来访问它们。 以及如何保存文件，以便用户可以指定要保存的文件的名称、文件类型和位置。 |
| [文件选取器合约示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何通过文件选取器向其他应用提供文件、保存位置和实时文件更新。 它通过参与文件开启选取器合约、文件保存选取器合约和缓存文件更新程序合约来完成。 |
| [编程文件搜索示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在文件夹、库、设备或网络位置等位置查询文件。 它使用 `Windows.Storage.Search` API。 本示例的重要 API 包括：`QueryOptions` 类、`StorageFileQueryResult` 类等。 |
| [文件和文件夹缩略图示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何检索文件和文件夹的缩略图。 它使用 `Windows.Storage.FileProperties` API。 |
| [输入操作和手势 (C++) 示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何通过 C++ 和 DirectX 在 Windows 应用商店应用中使用 `GestureRecognizer` API 处理指针输入、操作和手势。 |
| [Direct3D HLSL 分形生成器示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Direct3D HLSL 和 DirectCompute 计算着色器创建分形图像。 |
| [XAML Direct2D 照明效果示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示 Direct2D 效果中可用的照明效果。 照明效果属性由 XAML 接口控件控制，然后通过 XAML SwapChainBackgroundPanel 使用 Direct2D 显示。 |
| [Direct2Dapp 打印示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何将 Direct2D 打印支持添加到 Windows 应用商店应用。 此示例演示如何使用 Direct2D 功能呈现用于打印的 Windows 应用商店应用的内容。 还演示如何将呈现的内容发送到打印机。 |
| [Direct2D 打印图像和效果示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在 Windows 应用商店应用中打印 Direct2D 图像和 Direct2D 效果。 |
| [Direct2D 动画文本示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Direct2D `FillOpacityMask` 方法快速呈现文本。 该示例还对触控进行响应。 可以使用手指缩放来放大和缩小文本。 |
| [Direct3D 后处理效果示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了使用缩小的中间缓冲区在简单旋转立方体场景中进行 Direct3D 11.1 后处理。 |
| [扩展语言服务 (ELS) 示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在 Windows 应用商店应用中使用扩展语言服务 (ELS)。 该示例实现演示使用三个可用 ELS 服务的方案。 此方案演示如何请求特定服务。 |
| [DirectWrite 命中测试示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 DirectWrite 的命中测试功能。 它们用于确定所显示的文本中被单击或触控的部分。 |
| [DirectWrite 内联对象示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何将内联对象插入到文本布局（如图像）中。 |
| [XAML 基于矢量的绘图示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在应用中绘制基于矢量的图形。 |
| [蓝牙呼叫控制示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 蓝牙 CallControl 示例演示如何配置默认蓝牙通信设备以处理呼叫。 此示例有 JavaScript、C#、C++、和 VB.Net 版本。 此示例需要了解 Windows 事件和事件处理的知识。 |
| [Direct2D 命令列表示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示命令列表的用法。 它用于记录一组矢量命令，从命令列表中创建图像画笔，然后填充矩形几何体。 命令列表保留矢量的分辨率独立性。 |
| [ControlChannelTrigger XMLHTTPRequest 示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 该示例演示如何使用 `ControlChannelTrigger` 类使使用 `IXMLHTTPRequest2` 的 Windows 应用商店应用始终连接且始终可访问。 此示例演示如何在 Windows 应用商店应用中使用后台网络通知。 |
| [XInput 和 JavaScript 控制器草图示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在 Windows 运行时组件中包装 XInput C++ API。 然后，它将使用 JavaScript 从 Windows 应用商店应用调用它。 此示例实现一个草图应用，让你可使用 Xbox 游戏控制器来选择线的粗细等。 |
| [Direct2D 卷积矩阵效果示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示 Direct2D 效果卷积矩阵效果。 此示例包含一些示例卷积内核矩阵：直通（无操作），方框模糊（宽度为 5），简单边缘检测，简单锐化，浮雕，垂直拖尾（高度为 10）等。 |
| [DirectX 交换链实现示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何接收本机应用程序中的 `CoreWindow` 事件，以及如何将 DirectX 交换链连接到应用程序视图。 |
| [凭据选取器示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 `Windows.Security.Credentials.UI.CredentialPicker` 类检索凭据。 这些凭据可能会传递给需要它们的 API，例如 `HttpClient`。 |
| [Direct2D 动画示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Direct2D 沿螺旋路径呈现 Direct2D 基元并为其设置动画。 |
| [共享内容目标应用示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何从另一个应用接收共享的内容。 此示例使用来自 `Windows.ApplicationModel.DataTransfer` 和 `Windows.ApplicationModel.DataTransfer.Share` 命名空间的类。 |
| [Direct2D 保存到图像文件示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Direct2D 和 DirectWrite 呈现到屏幕。 还演示如何使用 WIC API 将呈现的图像保存到磁盘。 |
| [根据 DPI 缩放示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例说明如何构建可根据屏幕像素密度进行缩放的应用。 它加载适当缩放的图像或覆盖默认缩放。 此示例使用 `Windows.Graphics.Display` API。 |
| [创建 Windows 运行时进程内组件示例 (C#) (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在 C# 中创建用于 C++/CX、JavaScript 和 C# 客户端代码的组件。 OvenServer 项目包含名为 `Oven` 的运行时类，该类实现了 `IOven` 接口和 `IAppliance` 接口。 |
| [推送并定期通知客户端示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示客户端应用如何注册和侦听从 Web 服务器发送的推送通知。 推送通知可用于更新徽章或磁贴、引发 Toast 通知或启动后台任务。 |
| [便携设备 API 示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何访问 C++ 应用中的 `IPortableDevice` COM API。 若要了解如何从桌面 C++ 应用访问 `IPortableDevice` COM API，请参阅便携式设备 COM API 示例。 |
| [PlayToReceiver 示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何创建 Play To Receiver 软件。 若要播发 Play To Receiver软件，请单击“启动接收程序”按钮。 若要停止接收程序，请单击“停止接收程序”按钮。 |
| [锁屏界面个性化示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 `LockScreen` API 设置当前用户的锁屏界面图像。 此示例使用来自 `Windows.System.UserProfile` 命名空间的类。 |
| [凭据保险箱示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 WinRT `PasswordVault` API，以及如何使用凭据保险箱存储 Web 凭据。 特定方案包括具有单个资源的单个用户和具有单个资源的多个用户。 |
| [媒体引擎本机 C++ 视频播放示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示使用本机 C++ 应用中的 `MediaEngine` API 进行视频播放。 |
| [媒体扩展示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用媒体扩展。 可以使用方案处理程序将效果应用于视频、解码视频并创建媒体流。 |
| [锁屏界面应用示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例显示如何在锁屏界面（锁定计算机时显示的屏幕）上显示应用，并有提供基本状态信息的锁屏提醒或提供更详细状态的磁贴。 |
| [XAML 文本显示示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何控制应用中文本的外观。 |
| [SimpleOrientationSensor 示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 `Windows.Devices.Sensors.SimpleOrientationSensor` API。 |
| [Direct3D 子画面示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例提供了子画面批处理行为的 Direct3D 实现，类似于 XNA `SpriteBatch` API。 子画面是 2-D 位图，可在 3D 场景中独立转换和管理，通常用于 2D 游戏。 |
| [Direct3D 3D 示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Direct3D 向 C++ 应用添加立体 3D 效果。 它还演示了如何在 Direct3D 中响应系统立体声更改。 3D 效果需要支持立体声 3D 的显示器。 |
| [使用 C++ 创建 Windows 运行时 DLL 组件示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在 Microsoft Visual C++ 中创建进程内 DLL 组件。 它在 C++/CX、JavaScript 和 C# 客户端代码中使用。 OvenServer 项目包含名为 `Oven` 的运行时类，该类实现了 `IOven` 接口。 |
| [使用 C++ 创建 Windows 运行时 EXE 组件示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在 Microsoft Visual C++ 中创建进程外 EXE 组件。 它在 C++/CX、JavaScript 和 C# 客户端代码中使用。 OvenServer 项目包含名为 `Oven` 的运行时类，该类实现了 `IOven` 接口。 |
