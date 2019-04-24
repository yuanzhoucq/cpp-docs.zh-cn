---
title: MFC 和 ATL
ms.date: 01/24/2018
ms.assetid: 31b1a3a8-4154-4c4a-af10-fafc23ecdc5c
ms.openlocfilehash: c2cfb77f0e3885e0b315ddfe38bf942ec157375a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58780244"
---
# <a name="mfc-and-atl"></a>MFC 和 ATL

Microsoft 基础类 (MFC) 通过 Win32 提供面向 C++ 对象的包装，以便实现本机桌面应用程序的快速开发。 活动模板库 (ATL) 是一个包装库，它简化了 COM 开发，广泛用于创建 ActiveX 控件。

可以使用 Visual Studio Community 或更高版本创建 MFC 或 ATL 程序。 Express 版本不支持 MFC 或 ATL。

在 Visual Studio 2015 中，Visual C++ 是一个可选组件，MFC 和 ATL 组件是 Visual C++ 下的可选子组件。 如果首次安装 Visual Studio 时未选择这些组件，则在你第一次尝试创建或打开 MFC 或 ATL 项目时，系统将提示你安装它们。

在 Visual Studio 2017 及更高版本，MFC 和 ATL 是下的可选子组件**使用的桌面开发C++**  Visual Studio 安装程序中的工作负荷。 您可以安装而不使用 MFC、 ATL 支持或结合使用 MFC 和 ATL 支持 （MFC 取决于 ATL）。 有关工作负载和组件的详细信息，请参阅[安装 Visual Studio 2017](/visualstudio/install/install-visual-studio)。

## <a name="related-articles"></a>相关文章

|标题|描述|
|-----------|-----------------|
|[MFC 桌面应用程序](../mfc/mfc-desktop-applications.md)|Microsoft 基础类通过 Win32 提供面向对象的精简包装，以在 C++ 实现 GUI 应用程序的开速开发。|
|[ATL COM 桌面组件](../atl/atl-com-desktop-components.md)|ATL 提供类模板和其他使用构造来简化 C++ 中 COM 对象的创建。|
|[ATL/MFC 共享类](../atl-mfc-shared/atl-mfc-shared-classes.md)|对 MFC 和 ATL 共享的 [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md) 和其他类的引用。|
|[使用资源文件](../windows/working-with-resource-files.md)|通过资源编辑器可以编辑 UI 资源，如字符串、图像和对话框。|
|[Visual C++](../overview/visual-cpp-in-visual-studio.md)|MSDN 库中的所有 C++ 内容的父主题。|