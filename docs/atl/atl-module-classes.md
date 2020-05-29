---
title: ATL Module 类
ms.date: 11/04/2016
helpviewer_keywords:
- CComModule class, what's changed
- ATL, module classes
- module classes
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
ms.openlocfilehash: 2b72cac0da06b70a40e01fcc75da52f1678f3f64
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317371"
---
# <a name="atl-module-classes"></a>ATL Module 类

本主题讨论 ATL 7.0 中新增的模块类。

## <a name="ccommodule-replacement-classes"></a>CCom 模块更换类

使用的`CComModule`ATL 的早期版本。 在 ATL 7.0 中，`CComModule`功能被几个类替换：

- [CAtlBase模块](../atl/reference/catlbasemodule-class.md)包含大多数使用 ATL 的应用程序所需的信息。 包含模块和资源实例的 HINSTANCE。

- [CAtlCom 模块](../atl/reference/catlcommodule-class.md)包含 ATL 中的 COM 类所需的信息。

- [CAtlWin 模块](../atl/reference/catlwinmodule-class.md)包含 ATL 中窗口类所需的信息。

- [CAtlDebug接口模块](../atl/reference/catldebuginterfacesmodule-class.md)包含对接口调试的支持。

- [CAtlModule](../atl/reference/catlmodule-class.md)以下`CAtlModule`派生类被自定义以包含特定应用程序类型中所需的信息。 可以重写这些类中的大多数成员：

  - [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md)用于 DLL 应用程序。 提供标准导出的代码。

  - [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md)用于 EXE 应用程序。 提供 EXE 中所需的代码。

  - [CAtl服务模块T](../atl/reference/catlservicemodulet-class.md)提供创建 Windows NT 和 Windows 2000 服务的支持。

`CComModule`仍然可用于向后兼容性。

## <a name="reasons-for-distributing-ccommodule-functionality"></a>分发 CComModule 功能的原因

由于以下原因`CComModule`，将 的功能分发到几个新类中：

- 使功能以`CComModule`粒度进行。

   现在，对 COM、窗口、接口调试和特定于应用程序的 （DLL 或 EXE） 功能的支持处于单独的类中。

- 自动声明每个模块的全局实例。

   所需模块类的全局实例链接到项目中。

- 删除调用 Init 和术语方法的必要性。

   Init 和术语方法已移入模块类的构造函数和析构函数;不再需要调用 Init 和术语。

## <a name="see-also"></a>另请参阅

[概念](../atl/active-template-library-atl-concepts.md)<br/>
[类概述](../atl/atl-class-overview.md)
