---
title: 资源文件 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- resource files
- resources [C++]
- file types [C++], resource files
ms.assetid: 338a4a0f-0c62-4ef1-a34f-5d86262d93a4
ms.openlocfilehash: b3e15c024b84bdf04c7c5611584dc1b14d82816f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319429"
---
# <a name="resource-files-c"></a>资源文件 (C++)

资源是向用户提供信息的接口元素。 位图、图标、工具栏和光标都是资源。 可操纵某些资源来执行操作，例如从菜单中进行选择或在对话框中输入数据。

有关详细信息，请参阅[使用资源](../../windows/working-with-resource-files.md)。

|文件名|目录位置|解决方案资源管理器位置|描述|
|---------------|------------------------|--------------------------------|-----------------|
|Projname.rc|Projname|源文件|项目的资源脚本文件。 资源脚本文件包含以下内容，具体取决于项目类型以及为项目选择的支持（例如工具栏、对话框或 HTML）：<br /><br />- 默认菜单定义。<br />- 快捷键和字符串表。<br />- 默认“关于”对话框。<br />- 其他对话框。<br />- 图标文件 (res\\Projname.ico)。<br />- 版本信息。<br />- 位图。<br />- 工具栏。<br />- HTML 文件。<br /><br /> 资源文件包含标准 Microsoft 基础类资源的文件 Afxres.rc。|
|Resource.h|Projname|头文件|资源头文件，其中包括项目使用的资源的定义。|
|Projname.rc2|Projname\res|源文件|其中包含项目使用的其他资源的脚本文件。 可在项目的 .rc 文件下包含 .rc2 文件。<br /><br /> .rc2 文件可用于包括多个不同项目使用的资源。 不必为不同的项目多次创建相同资源，而是将它们放在 .rc2 文件中，并将 .rc2 文件包含到主 .rc 文件中。|
|Projname.def|Projname|源文件|DLL 项目的模块定义文件。 对于控件，它提供了控件的名称和说明，以及运行时堆的大小。|
|Projname.ico|Projname\res|资源文件|项目或控件的图标文件。 应用程序最小化时，会显示此图标。 它也用于应用程序的“关于”框中。 默认情况下，MFC 提供 MFC 图标，而 ATL 提供 ATL 图标。|
|ProjnameDoc.ico|Projname\res|资源文件|MFC 项目的图标文件，其中包含对文档/视图体系结构的支持。|
|Toolbar.bmp|Projname\res|资源文件|位图文件，代表工具栏或调色板中应用程序或控件。 该位图包含在项目的资源文件中。 在 CMainFrame 类中构造初始工具栏和状态栏。|
|ribbon.mfcribbon-ms|Projname\res|资源文件|资源文件，包含用于定义功能区中的按钮、控件和属性的 XML 代码。 有关详细信息，请参阅 [Ribbon Designer (MFC)](../../mfc/ribbon-designer-mfc.md)。|

## <a name="see-also"></a>请参阅

[为 Visual C++ 项目创建的文件类型](file-types-created-for-visual-cpp-projects.md)
