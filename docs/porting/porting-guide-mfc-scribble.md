---
title: "迁移指南：MFC Scribble | Microsoft Docs"
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
ms.assetid: 8ddb517d-89ba-41a1-ab0d-4d2c6d9047e8
caps.latest.revision: 5
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 迁移指南：MFC Scribble
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题是向你介绍 Visual C\+\+ 项目升级过程的几个主题的第一个，该项目是在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 的较旧版本的 Visual Studio 中创建的。  这些主题通过示例介绍升级过程，从非常简单的项目开始，过渡到稍微更复杂的项目。  在本主题中，我们将完成特定项目 \(MFC Scribble\) 的升级过程。  它很适合作为对 C\+\+ 项目升级过程的基本介绍。  
  
 每个版本的 Visual Studio 都可能引入不兼容问题，使从较早版本的 Visual Studio 移动代码到较新的版本变得复杂。  有时需要对你的代码进行必要的更改，因此你必须重新编译并更新代码，有时需要对项目文件进行必要的更改。  当你打开使用早期版本的 Visual Studio 创建的项目时，Visual Studio 会自动询问你是否要将项目或解决方案更新到最新版本。  这些工具通常仅升级项目文件；它们不修改你的源代码。  
  
## MFC Scribble  
 MFC Scribble 是一个众所周知的示例，已包括在许多不同版本的 Visual C\+\+ 中。  它是一个简单的绘图应用程序，展示了 MFC 的一些基本功能。  它有各种可用的版本，包括托管版本和本机代码版本。  针对此示例，我们发现了来自 Visual Studio 2005 的本机代码中的旧版 Scribble 并将其在 [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 中打开。  
  
 在尝试升级前，我们备份整个解决方案及其所有内容。  接下来，我们需要决定特定的升级方法。  对于更复杂的解决方案和长期未进行升级的项目，则应考虑一次升级一个 Visual Studio 版本。  这样一来，你可以对哪个 Visual Studio 版本引入了问题进行范围缩小。  对于简单的项目，值得在最新版的 Visual Studio 中尝试打开它，并允许向导将项目转换。  如果这不起作用，你可以尝试一次升级一个版本（如果你有权访问相应版本的 Visual Studio）。  
  
 请注意，使用 `/Upgrade` 选项（而不是使用向导来升级项目），你还可以在命令行运行 devenv。  请参阅 [\/Upgrade](../Topic/-Upgrade%20\(devenv.exe\).md)。  这在为大量项目自动执行升级过程中很有帮助。  
  
### 步骤 1。转换项目文件  
 在 Visual Studio 2015 中打开旧的项目文件时，Visual Studio 主动将项目文件转换为我们接受的最新版本。  出现了下面的对话框：  
  
 ![复查项目和解决方案更改](../porting/media/scribbleprojectupgrade.png "ScribbleProjectUpgrade")  
  
 出现了错误，通知我们 Itanium 目标不可用且不被转换。  
  
  **在此项目中找不到平台“Itanium”。  所有配置及其特定于此平台的文件配置设置都将被忽略。  如果你想要转换此平台，请确保在“%vctargetpath%\\platforms\\Itanium”下安装了相应的平台。  是否在无此平台的条件下继续转换该项目?**  创建之前的 Scribble 项目时，Itanium 是重要的目标平台。  Windows 平台不再支持 Itanium，因此我们选择在不支持 Itanium 平台的情况下继续。  
  
 Visual Studio 随后将显示一个迁移报告，该报告列出旧项目文件中的所有问题。  
  
 ![升级报告](../Image/ScribbleMigrationReport.PNG "ScribbleMigrationReport")  
  
 在本例中，问题都是警告，并且 Visual Studio 在项目文件中进行了相应的更改。  项目关注的最大差别就在于生成工具从 vcbuild 更改为 msbuild。  在 Visual Studio 2010 中首先引入了此更改。  其他更改包括项目文件本身中元素序列的重新排列。  针对此简单项目，无需对这些问题进行深入关注。  
  
### 步骤 2。开始生成  
 在生成之前，我们检查平台工具集以便了解项目系统使用的是何种编译器版本。  在**“配置属性”**之下的项目属性对话框中，请在**“常规”**类别中查看**“平台工具集”**属性。  它包含 Visual Studio 的版本和平台工具版本号，在本例中，[!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 版本的工具版本号为 v140。  转换使用 Visual C\+\+ 2010、2012 或 2013 进行初始编译的项目时，工具集将不会自动更新为 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 工具集。  对于 Scribble，已为 Visual Studio 2005 创建我们转换的版本，因此它将转换为使用最新的工具集。  
  
 生成时，出现第一个问题是关于 MBCS 代码的。  
  
  **error MSB8031:**  点击错误消息中的链接，我们将转到有关不推荐在 Visual Studio 2013 中使用 MBCS 的主题。  默认情况下，Visual C\+\+ 2013 中的 MFC 安装不包括 MBCS 版本的 MFC。  在当前窗体中生成此项目时需要 MBCS 版本的 MFC。  我们可以将代码迁移以使用 Unicode，也可以下载并安装 MBCS 版本的 MFC。  如果我们选择下载 MBCS 版本的 MFC，则可以为宏 NO\_WARN\_MBCS\_MFC\_DEPRECATION 添加定义以禁止显示此警告。  
  
 若要下载 MBCS 版的 MFC，请先阅读文章 [MFC MBCS DLL 加载项](../mfc/mfc-mbcs-dll-add-on.md)中有关弃用 MBCS 版的 MFC 的内容，然后登录 VC 博客，在[此处](http://www.microsoft.com/download/details.aspx?id=44930)下载 MBCS 版的 MFC。  在**“预处理器”**下的**“C\/C\+\+”**类别的“项目属性”对话框中，将 NO\_WARN\_MBCS\_MFC\_DEPRECATION 添加到预定义的宏的列表。  
  
 若要切换到 Unicode，请打开**“配置属性”**之下的项目属性，选择**“常规”**部分，然后找到**“字符集”**属性。  将此项从**“使用多字节字符集”**更改为**“使用 Unicode 字符集”**。  此更改的效果：现在定义了 \_UNICODE 和 UNICODE 宏，而未定义 \_MBCS，这一点你可以在**“命令行”**属性处的**“C\/C\+\+”**类别之下的“属性”对话框中进行验证。  
  
  **\/GS \/analyze\- \/W4 \/Gy \/Zc:wchar\_t \/Zi \/Gm\- \/O2 \/Ob1 \/Fd"。  \\Release\\vc140.pdb" \/Zc:inline \/fp:precise \/D "\_AFXDLL" \/D "WIN32" \/D "NDEBUG" \/D "\_WINDOWS" \/D "\_UNICODE" \/D "UNICODE" \/errorReport:prompt \/GF \/WX \/Zc:forScope \/Gd \/Oy \/MD \/Fa"。  \\Release\\" \/EHsc \/nologo \/Fo"。  \\Release\\" \/Fp"。  \\Release\\Scribble.pch"**  尽管未将 Scribble 项目设置为使用 Unicode 字符进行编译，但它已使用 TCHAR（而非 char）进行编写，因此实际上无需做任何更改。  使用 Unicode 字符集成功生成项目。  
  
 但是，还存在另一个问题。  编译器告诉我们 \_WINNT32\_WINNT 未进行定义：  
  
  **\_WIN32\_WINNT 未定义。  默认为 \_WIN32\_WINNT\_MAXVER（请参阅 WinSDKVer.h）**  这是一个警告而不是错误，在升级 Visual C\+\+ 项目时很常见。  这是定义我们的应用程序将在其上运行的最低版本的 Windows 的宏。  如果我们忽略该警告，则接受表示当前 Windows 版本的默认值（\_WIN32\_WINNT\_MAXVER）。  有关可能的值的表，请参阅[使用 Windows 标头](https://msdn.microsoft.com/en-us/library/aa383745.aspx)。  例如，我们可以将其设置为自 Vista 起的任何版本上运行。  
  
```  
#define _WIN32_WINNT _WIN32_WINNT_VISTA  
```  
  
 如果代码使用你用此宏该指定的 Windows 版本上不可用的部分 Windows API，则你应该将其视为编译器错误。  对于 Scribble 代码，不存在任何错误。  
  
### 步骤 3。测试和调试  
 由于没有任何测试套件，因此我们只是启动应用，通过用户界面手动测试其功能。  观察不到任何问题。  
  
### 步骤 4。改进代码  
 既然你已经迁移到 Visual Studio 2015，你可能想要执行一些更改来利用新的 C\+\+ 功能。  当前版本的 Visual C\+\+ 编译器相比早期版本更符合 C\+\+ 标准，因此如果想做一些代码更改以使代码更加安全，并更易于移植到其他编译器和操作系统上，则应考虑做些改进。  
  
## 后续步骤  
 Scribble 是一款小巧而简单 Windows 桌面应用程序，且不难转换。  许多小型简单的应用程序都可轻松转换为新版本。  对于具有很多行代码以及可能不符合现代设计标准的较早的旧版代码、多个项目和库、自定义生成步骤的更复杂的应用程序，或对于复杂脚本的自动生成，则需要较长时间进行升级。  继续[下一个示例](../porting/porting-guide-com-spy.md)，称为 COM Spy 的 ATL\/COM 应用程序。  
  
## 请参阅  
 [迁移和升级：示例和案例研究](../porting/porting-and-upgrading-examples-and-case-studies.md)   
 [下一个示例：COM Spy](../porting/porting-guide-com-spy.md)