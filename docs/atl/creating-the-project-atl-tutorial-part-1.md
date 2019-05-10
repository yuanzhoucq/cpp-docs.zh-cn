---
title: 创建项目（ATL 教程，第 1 部分）
ms.custom: get-started-article
ms.date: 05/06/2019
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
ms.openlocfilehash: 292faf1769baa2e1c3fc6e52ba6df065cf08766e
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221401"
---
# <a name="creating-the-project-atl-tutorial-part-1"></a>创建项目（ATL 教程，第 1 部分）

本教程将指导你逐步完成创建显示多边形的 ActiveX 对象的非属性化 ATL 项目。 该对象包含用于允许用户的选项，若要更改组成 polygon 和代码以刷新显示的边数。

> [!NOTE]
> ATL 和 MFC 不通常支持在 Visual Studio 速成版中。

> [!NOTE]
> 本教程将创建与多边形的示例相同的源代码。 如果你想要避免手动输入的源代码，您可以从中进行下载[多边形示例抽象](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/Polygon)。 然后可以指多边形源代码在你完成本教程中，或使用它来检查自己的项目中的错误。
> 若要编译，请打开 stdafx.h 并替换为：
> ```
> #ifndef WINVER
> #define WINVER 0x0400
> #endif
> ```
> 替换为
> ```
> #ifndef WINVER
> #define WINVER 0x0500
> #define _WIN32_WINNT 0x0500
> #endif
> ```
> 编译器仍抱怨`regsvr32`未退出正确，但你仍应生成并可供使用的控件的 DLL。

### <a name="to-create-the-initial-atl-project-using-the-atl-project-wizard"></a>若要创建使用 ATL 项目向导的初始 ATL 项目

1. 在 Visual Studio 2017 及更早版本：**文件** > **新** > **项目**。 打开**可视化C++** 选项卡并选择**MFC/ATL**。 选择**ATL 项目**。

   在 Visual Studio 2019:选择**文件** > **新建** > **项目**中，在搜索框中，键入"atl"并选择**ATL 项目**。

1. 类型*多边形*作为项目名称。

    源代码的位置将通常默认为 \Users\\\<用户名 > 将自动创建 \source\repos 和一个新的文件夹。

1. 单击**确定**并**ATL 项目**向导随即打开。

1. 单击**应用程序设置**若要查看可用的选项。

1. 如要创建一个控件，并且必须是进程内服务器，将保留**应用程序类型**作为 DLL。

1. 将其他选项保留其默认值，然后单击**确定**。

**ATL 项目向导**将通过生成多个文件来创建项目。 您可以查看这些文件置于**解决方案资源管理器**展开`Polygon`对象。 下面列出的文件。

|文件|描述|
|----------|-----------------|
|Polygon.cpp|包含实现`DllMain`， `DllCanUnloadNow`， `DllGetClassObject`， `DllRegisterServer`，和`DllUnregisterServer`。 此外包含对象代码图，它是你的项目中的 ATL 对象的列表。 这是最初为空。|
|Polygon.def|此模块定义文件提供了有关所需的 DLL 导出的信息链接器。|
|Polygon.idl 使其|接口定义语言文件，其中描述了特定于您的对象的接口。|
|Polygon.rgs|此注册表脚本包含用于注册应用程序的 DLL 的信息。|
|Polygon.rc|最初包含版本信息和包含项目名称的字符串资源文件。|
|Resource.h|资源文件的头文件。|
|Polygonps.def|此模块定义文件提供了有关支持跨单元调用导出所需的代理和存根代码的信息链接器。|
|stdafx.cpp|将该文件`#include`ATL 实现文件。|
|stdafx.h|将该文件`#include`ATL 标头文件。|

1. 在中**解决方案资源管理器**，右键单击`Polygon`项目。

1. 在快捷菜单上，单击**属性**。

1. 单击**链接器**。 更改**每个 UserRedirection**选项设为**是**。

1. 单击 **“确定”**。

在下一步中，将将控件添加到你的项目。

[步骤 2 到](../atl/adding-a-control-atl-tutorial-part-2.md)

## <a name="see-also"></a>请参阅

[教程](../atl/active-template-library-atl-tutorial.md)
