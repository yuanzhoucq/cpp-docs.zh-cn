---
title: ATL Module 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CComModule class, what's changed
- ATL, module classes
- module classes
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b254edfe75cfcdaee7ab15351f7c05c3d163e301
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="atl-module-classes"></a>ATL Module 类
本主题讨论了在 ATL 7.0 中新的模块类。  
  
## <a name="ccommodule-replacement-classes"></a>CComModule 替换类  
 使用 ATL 的早期版本`CComModule`。 ATL 7.0 中`CComModule`功能取代由几个类：  
  
-   [CAtlBaseModule](../atl/reference/catlbasemodule-class.md)包含所需的大多数应用程序使用 atl。 信息 包含 HINSTANCE 的模块和资源实例。  
  
-   [CAtlComModule](../atl/reference/catlcommodule-class.md)包含所需的 atl。 中的 COM 类信息  
  
-   [CAtlWinModule](../atl/reference/catlwinmodule-class.md)包含所需的 atl。 中的窗口类信息  
  
-   [CAtlDebugInterfacesModule](../atl/reference/catldebuginterfacesmodule-class.md)包含接口调试的支持。  
  
-   [CAtlModule](../atl/reference/catlmodule-class.md)以下`CAtlModule`-自定义派生的类以包含在特定应用程序类型所需信息。 可以重写这些类中的大多数成员：  
  
    -   [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) DLL 的应用中使用。 为标准的导出提供代码。  
  
    -   [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md) EXE 应用程序中使用。 提供在 EXE 所需代码。  
  
    -   [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md)提供创建 Windows NT 和 Windows 2000 服务支持。  
  
 `CComModule`是仍可用于向后兼容性。  
  
## <a name="reasons-for-distributing-ccommodule-functionality"></a>分发 CComModule 功能的原因  
 功能`CComModule`已分发到多个新类，原因如下：  
  
-   进行中的功能`CComModule`粒度。  
  
     对 COM、 窗口、 接口调试和应用程序特定 （DLL 或 EXE） 功能的支持现已在单独的类。  
  
-   自动声明每个这些模块的全局的实例。  
  
     所需的模块类的全局实例链接到项目中。  
  
-   删除不必通过调用 Init 和术语方法。  
  
     Init 和术语方法为模块的类; 已移到构造函数和析构函数不再需要调用 Init 和术语。  
  
## <a name="see-also"></a>请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [类概述](../atl/atl-class-overview.md)

