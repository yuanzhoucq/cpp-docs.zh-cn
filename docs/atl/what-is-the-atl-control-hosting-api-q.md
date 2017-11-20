---
title: "什么是 ATL 控件承载 API？ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- APIs [C++], hosting
- control-hosting API
- controls [ATL], hosting APIs
ms.assetid: 75b27e45-cfba-4950-aa35-96cc7d8da753
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4f04f5caa30ab860634f0f96ae18e9da03577ba2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="what-is-the-atl-control-hosting-api"></a>什么是 ATL 控件承载 API？
ATL 的控件承载 API 是一套函数，它允许任何窗口使其作为 ActiveX 控件容器。 这些函数可以是静态或动态链接到你的项目，因为它们可用作源代码并由 ATL90.dll 公开。 下表中列出的控件承载的函数。  
  
|函数|描述|  
|--------------|-----------------|  
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|创建主机对象，将它连接到提供的窗口，然后将现有控件附加。|  
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|创建主机对象，将它连接到提供的窗口，然后加载控件。|  
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|创建授权的 ActiveX 控件，初始化它，并在指定窗口，类似于中承载它[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)。|  
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|创建主机对象，将它连接到提供的窗口，然后加载控件 （也允许事件接收器设置）。|  
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|创建授权的 ActiveX 控件，初始化它，并在指定窗口，类似于中承载它[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)。|  
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|从对话框资源创建无模式对话框并返回的窗口句柄。|  
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|从对话框资源创建模式对话框。|  
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|返回**IUnknown**承载在窗口中的控件的接口指针。|  
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|返回**IUnknown**该主机对象的接口指针连接到一个窗口。|  
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|初始化的控件承载代码。|  
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|取消初始化的控件承载代码。|  
  
 `HWND`中的前三个函数的参数必须是 （几乎） 任何类型的现有的窗口。 如果显式调用了任何这三个函数 （通常情况下，您不必），不要将句柄传递给已充当主机窗口 （如果这样做，现有的宿主对象不会被释放）。  
  
 前七个函数调用[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)隐式。  
  
> [!NOTE]
>  控件承载 API 窗体 ActiveX 控件包含 ATL 的支持的基础。 但是，通常没有几乎无需直接调用这些函数，如果你充分利用或充分利用 ATL 的包装类。 有关详细信息，请参阅[的 ATL 类促进 ActiveX 控件包含](which-atl-classes-facilitate-activex-control-containment-q.md)。  
  
## <a name="see-also"></a>另请参阅  
 [控件包含常见问题](which-atl-classes-facilitate-activex-control-containment-q.md)
