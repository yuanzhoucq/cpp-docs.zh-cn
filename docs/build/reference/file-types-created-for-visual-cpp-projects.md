---
title: 为 Visual C++ 项目创建的文件类型
ms.date: 04/08/2019
helpviewer_keywords:
- header files [C++], Visual Studio projects
- ActiveX controls [C++], Help files
- def files
- project items [C++], files
- Visual Studio C++ projects, files and directories
- resource files, created by wizard
- files [C++], extensions
- Help files, for ActiveX controls
- Web projects [C++], adding items
- .def files
- licensing ActiveX controls
ms.assetid: 2b0ee2e0-ae81-4185-9bb9-11da3c99a283
ms.openlocfilehash: eee53acbb8b0b8432a7d5819fb773b616f0e8897
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271161"
---
# <a name="file-types-created-for-visual-studio-c-projects"></a>文件类型为 Visual Studio 创建C++项目

许多类型的文件是与 Visual Studio 项目类型提供的经典桌面应用程序相关联。 项目中包含的实际文件取决于项目类型以及在使用向导时选择的选项。

- [项目和解决方案文件](project-and-solution-files.md)

- [CLR 项目](files-created-for-clr-projects.md)

- [ATL 程序或控件的源文件和头文件](atl-program-or-control-source-and-header-files.md)

- [MFC 程序或控件的源文件和头文件](mfc-program-or-control-source-and-header-files.md)

- [预编译的头文件](../creating-precompiled-header-files.md)

- [资源文件](resource-files-cpp.md)

- [帮助文件 (WinHelp)](help-files-winhelp.md)

- [提示文件](hint-files.md)

创建 Visual Studio 项目时，可能会在新解决方案中，创建或可能将项目添加到现有解决方案。 不常用的应用程序通常是使用一个解决方案中的多个项目开发的。

项目通常会生成 EXE 或 DLL。 项目可能依赖于每个其他;在生成过程中，在 Visual Studio 环境会检查内部和项目之间的依赖项。 每个项目通常具有核心源代码。 根据项目的种类，它可能具有包含项目的各个方面的许多其他文件。 这些文件的内容通过文件扩展名来指示。 Visual Studio 开发环境使用文件扩展名来确定如何在生成过程中处理文件内容。

下表显示在 Visual Studio 项目中的公共文件，并使用其文件扩展名标识它们。

|文件扩展名|类型|内容|
|--------------------|----------|--------------|
|.asmx|源|部署文件。|
|.asp|Source|Active Server Page 文件。|
|.atp|项目|应用程序模板项目文件。|
|.bmp、.dib、.gif、.jpg、.jpe、.png|资源|常规图像文件。|
|.bsc|编译|浏览器代码文件。|
|.cpp、.c|Source|应用程序的主源代码文件。|
|.cur|资源|光标位图图形文件。|
|.dbp|项目|数据库项目文件。|
|.disco|Source|动态发现文档文件。 处理 XML Web 服务发现。|
|.exe、.dll|项目|可执行文件或动态链接库文件。|
|.h|Source|头（包含）文件。|
|.htm、.html、.xsp、.asp、.htc、.hta、.xml|资源|公共 Web 文件。|
|.HxC|项目|帮助项目文件。|
|.ico|资源|图标位图图形文件。|
|.idb|编译|包含源代码文件和类定义之间的依赖关系信息的状态文件。 它可由编译器在增量编译过程。 使用 [/Fd](fd-program-database-file-name.md) 编译器选项指定 .idb 文件的名称。|
|.idl|编译|接口定义语言文件。 有关详细信息，请参阅 Windows SDK 中的[接口定义 (IDL) 文件](/windows/desktop/Rpc/the-interface-definition-language-idl-file)。|
|.ilk|链接|增量链接文件。 有关详细信息，请参阅[/incremental](incremental-link-incrementally.md)。|
|.map|链接|包含链接器信息的文本文件。 使用 [/Fm](fm-name-mapfile.md) 编译器选项命名映射文件。 有关详细信息，请参阅[/map](map-generate-mapfile.md)。|
|.mfcribbon-ms|资源|包含定义功能区中的 MFC 按钮、 控件和属性的 XML 代码的资源文件。 有关详细信息，请参阅 [Ribbon Designer](../../mfc/ribbon-designer-mfc.md)。|
|.obj、.o||对象文件，已编译但未链接。|
|.pch|调试|预编译头文件。|
|.rc、.rc2|资源|[资源脚本文件](../../windows/working-with-resource-files.md) ，用于生成资源。|
|.sbr|编译|源浏览器中间文件。 [BSCMAKE](bscmake-options.md)的输入文件。|
|.sln|解决方案|[解决方案](/visualstudio/ide/solutions-and-projects-in-visual-studio)文件。|
|.suo|解决方案|解决方案选项文件。|
|.txt|资源|文本文件，通常是“自述”文件。|
|.vap|项目|Visual Studio Analyzer 项目文件。|
|.vbg|解决方案|兼容的项目组文件。|
|.vbp、.vip、.vbproj|Project|Visual Basic 项目文件。|
|.vcxitems|项目|用于在多个 C++ 项目之间共享代码文件的共享项目。 有关详细信息，请参阅[项目和解决方案文件](project-and-solution-files.md)。|
|.vcxproj|项目|Visual Studio 项目文件。 有关详细信息，请参阅[项目和解决方案文件](project-and-solution-files.md)。|
|.vcxproj.filters|项目|使用解决方案资源管理器将文件添加到项目时使用。 筛选器文件定义在解决方案资源管理器树视图中添加基于其文件扩展名的文件的位置。|
|.vdproj|项目|Visual Studio 部署项目文件。|
|.vmx|项目|宏项目文件。|
|.vup|项目|实用工具项目文件。|

有关与 Visual Studio 关联的其他文件的信息，请参见 [Visual Studio .NET 中的文件类型和文件扩展名](/visualstudio/ide/reference/project-and-solution-file-types)。

项目文件会组织到解决方案资源管理器中的文件夹中。 Visual Studio 将创建的源文件、 头文件和资源文件的文件夹，但可以重新组织这些文件夹或创建新的。 可以使用文件夹在项目层次结构中显式组织文件的逻辑群集。 例如，可以创建文件夹以包含所有用户界面源文件。 或者，规范、 文档或测试套件的文件夹。 所有文件文件夹名都应是唯一的。

当将某个项添加到项目中时，你将项添加到该项目的所有配置。 它是否可生成添加项。 例如，如果有一个名为 MyProject 的项目，则添加项会将它同时添加调试和发布项目配置。

## <a name="see-also"></a>请参阅

[创建和管理 Visual StudioC++项目](../creating-and-managing-visual-cpp-projects.md)<br>
[Visual StudioC++项目类型](visual-cpp-project-types.md)<br>