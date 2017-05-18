---
title: "移植指南：MFC Scribble | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 8ddb517d-89ba-41a1-ab0d-4d2c6d9047e8
caps.latest.revision: 5
author: mikeblome
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 220ecd24c6056737d0338cc584663e4664ac81b1
ms.openlocfilehash: 053769ee274abf6e29f8d6f2938dc595ad8bd9f3
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="porting-guide-mfc-scribble"></a>迁移指南：MFC Scribble
本主题是向你介绍 Visual C++ 项目升级过程的几个主题中的第一个主题，具体升级过程为将在较旧版本的 Visual Studio 中创建的 Visual C++ 项目升级到 Visual Studio 2017。 这些主题通过示例介绍升级过程，从非常简单的项目开始，过渡到稍微更复杂的项目。 在本主题中，我们将完成特定项目 (MFC Scribble) 的升级过程。 它很适合作为对 C++ 项目升级过程的基本介绍。  
  
 每个版本的 Visual Studio 都可能引入不兼容问题，使从较早版本的 Visual Studio 移动代码到较新的版本变得复杂。 有时需要对你的代码进行必要的更改，因此你必须重新编译并更新代码，有时需要对项目文件进行必要的更改。 当你打开使用早期版本的 Visual Studio 创建的项目时，Visual Studio 会自动询问你是否要将项目或解决方案更新到最新版本。 这些工具通常仅升级项目文件；它们不修改你的源代码。  
  
## <a name="mfc-scribble"></a>MFC Scribble  
 MFC Scribble 是一个众所周知的示例，已包括在许多不同版本的 Visual C++ 中。 它是一个简单的绘图应用程序，展示了 MFC 的一些基本功能。 它有各种可用的版本，包括托管版本和本机代码版本。 针对此示例，我们发现本机代码中的旧版 Scribble 来自 Visual Studio 2005 并在 Visual Studio 2017 中打开。  
  
 在尝试升级之前，请确保已安装 Windows Desktop 工作负载。 打开 Visual Studio 安装程序 (vs_installer.exe)。 打开安装程序的方法之一是，选择“文件”>“新建项目”，向下滚动已安装模板列表，直到看到“打开 Visual Studio 安装程序”。 打开安装程序后，将看到所有可用的工作负载。 如果未选择“Windows Desktop 工作负载”框，请选择它，然后单击窗口底部的“修改”按钮。 


 接下来，备份整个解决方案及其所有内容。 
 
 最后，我们需要确定具体的升级方法。 对于更复杂的解决方案和长期未进行升级的项目，则应考虑一次升级一个 Visual Studio 版本。 这样一来，你可以对哪个 Visual Studio 版本引入了问题进行范围缩小。 对于简单的项目，值得在最新版的 Visual Studio 中尝试打开它，并允许向导将项目转换。 如果这不起作用，你可以尝试一次升级一个版本（如果你有权访问相应版本的 Visual Studio）。  
  
 请注意，使用 `/Upgrade` 选项（而不是使用向导来升级项目），你还可以在命令行运行 devenv。 请参阅 [/Upgrade (devenv.exe)](/visualstudio/ide/reference/upgrade-devenv-exe)。 这在为大量项目自动执行升级过程中很有帮助。  
  
### <a name="step-1-converting-the-project-file"></a>步骤 1。 转换项目文件  
 在 Visual Studio 2017 中打开旧的项目文件时，Visual Studio 主动将项目文件转换为我们接受的最新版本。 出现了下面的对话框：  
  
 ![复查项目和解决方案更改](../porting/media/scribbleprojectupgrade.PNG "ScribbleProjectUpgrade")  
  
 出现了错误，通知我们 Itanium 目标不可用且不被转换。  
  
```Output  
Platform 'Itanium' is missing from this project. All the configurations and their file configuration settings specific to this platform will be ignored. If you want this platform converted, please make sure you have the corresponding platform installed under '%vctargetpath%\platforms\Itanium'.Continue to convert this project without this platform?  
```  
  
 创建之前的 Scribble 项目时，Itanium 是重要的目标平台。 Windows 平台不再支持 Itanium，因此我们选择在不支持 Itanium 平台的情况下继续。  
  
 Visual Studio 随后将显示一个迁移报告，该报告列出旧项目文件中的所有问题。  
  
 ![升级报告](../porting/media/scribblemigrationreport.PNG "ScribbleMigrationReport")  
  
 在本例中，问题都是警告，并且 Visual Studio 在项目文件中进行了相应的更改。 项目关注的最大差别就在于生成工具从 vcbuild 更改为 msbuild。 在 Visual Studio 2010 中首先引入了此更改。 其他更改包括项目文件本身中元素序列的重新排列。 针对此简单项目，无需对这些问题进行深入关注。  
  
### <a name="step-2-getting-it-to-build"></a>步骤 2。 开始生成  
 在生成之前，我们检查平台工具集以便了解项目系统使用的是何种编译器版本。 在“配置属性”之下的“项目属性”对话框中，请在“常规”类别中查看“平台工具集”属性。 它包含 Visual Studio 的版本和平台工具版本号，在本例中，Visual Studio 2017 版本的工具版本号为 v141。 转换使用 Visual C++ 2010、2012、2013 或 2015 进行初始编译的项目时，工具集将不会自动更新为 Visual Studio 2017 工具集。   
  
  若要切换到 Unicode，请打开“配置属性”之下的项目属性，选择“常规”部分，然后找到“字符集”属性。 将此项从“使用多字节字符集”更改为“使用 Unicode 字符集”。 此更改的效果：现在定义了 _UNICODE 和 UNICODE 宏，而未定义 _MBCS，这一点你可以在“命令行”属性处的“C/C++”类别之下的“属性”对话框中进行验证。  
  
```Output  
/GS /analyze- /W4 /Zc:wchar_t /Zi /Gm- /Od /Fd".\Debug\vc141.pdb" /Zc:inline /fp:precise /D "_AFXDLL" /D "WIN32" /D "_DEBUG" /D "_WINDOWS" /D "_UNICODE" /D "UNICODE" /errorReport:prompt /WX /Zc:forScope /Gd /Oy- /MDd /Fa".\Debug\" /EHsc /nologo /Fo".\Debug\" /Fp".\Debug\Scribble.pch" /diagnostics:classic 
```  
  
 尽管未将 Scribble 项目设置为使用 Unicode 字符进行编译，但它已使用 TCHAR（而非 char）进行编写，因此实际上无需做任何更改。 使用 Unicode 字符集成功生成项目。  
  
 至此解决方案构建完毕。 在输出窗口中，编译器告诉我们 _WINNT32_WINNT 未进行定义：  
  
```Output  
_WIN32_WINNT not defined. Defaulting to _WIN32_WINNT_MAXVER (see WinSDKVer.h)  
```  
  
 这是一个警告而不是错误，在升级 Visual C++ 项目时很常见。 这是定义我们的应用程序将在其上运行的最低版本的 Windows 的宏。 如果我们忽略该警告，则接受表示当前 Windows 版本的默认值（_WIN32_WINNT_MAXVER）。 有关可能的值的表，请参阅 [Using the Windows Headers](https://msdn.microsoft.com/en-us/library/aa383745.aspx)（使用 Windows 标头）。 例如，我们可以将其设置为自 Vista 起的任何版本上运行。  
  
```  
#define _WIN32_WINNT _WIN32_WINNT_VISTA  
```  
  
 如果代码使用你用此宏该指定的 Windows 版本上不可用的部分 Windows API，则你应该将其视为编译器错误。 对于 Scribble 代码，不存在任何错误。  
  
### <a name="step-3-testing-and-debugging"></a>步骤 3。 测试和调试  
 由于没有任何测试套件，因此我们只是启动应用，通过用户界面手动测试其功能。 观察不到任何问题。  
  
### <a name="step-4-improve-the-code"></a>步骤 4。 改进代码  
 现在你已经迁移到 Visual Studio 2017，建议执行一些更改来利用新的 C++ 功能。 当前版本的 Visual C++ 编译器相比早期版本更符合 C++ 标准，因此如果想做一些代码更改以使代码更加安全，并更易于移植到其他编译器和操作系统上，则应考虑做些改进。  
  
## <a name="next-steps"></a>后续步骤  
 Scribble 是一款小巧而简单 Windows 桌面应用程序，且不难转换。 许多小型简单的应用程序都可轻松转换为新版本。  对于具有很多行代码以及可能不符合现代设计标准的较早的旧版代码、多个项目和库、自定义生成步骤的更复杂的应用程序，或对于复杂脚本的自动生成，则需要较长时间进行升级。 继续[下一个示例](../porting/porting-guide-com-spy.md)，即称为 COM Spy 的 ATL/COM 应用程序。  
  
## <a name="see-also"></a>另请参阅  
 [移植和升级：示例和案例研究](../porting/porting-and-upgrading-examples-and-case-studies.md)   
 [下一个示例：COM Spy](../porting/porting-guide-com-spy.md)

