---
title: 什么是 ATL 控件承载 API？ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- APIs [C++], hosting
- control-hosting API
- controls [ATL], hosting APIs
ms.assetid: 75b27e45-cfba-4950-aa35-96cc7d8da753
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2cc85c7ca47d5d1226ffc3089e01c0755ef6c6ac
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850548"
---
# <a name="what-is-the-atl-control-hosting-api"></a>什么是 ATL 控件承载 API？
ATL 的控件承载 API 是允许任何窗口，使其作为 ActiveX 控件容器的函数集。 这些函数可以是静态或动态链接到你的项目，因为它们可为源代码和由 ATL90.dll 公开。 下表中列出的控件承载的函数。  
  
|函数|描述|  
|--------------|-----------------|  
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|创建主机对象，将其连接到提供的窗口，然后将附加现有的控件。|  
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|创建主机对象，将其连接到提供的窗口，然后加载控件。|  
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|创建授权的 ActiveX 控件，初始化它，并在指定窗口中，类似于承载[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)。|  
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|创建主机对象，将其连接到提供的窗口，然后加载控件 （也允许事件接收器设置）。|  
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|创建授权的 ActiveX 控件，初始化它，并在指定窗口中，类似于承载[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)。|  
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|通过对话框资源创建无模式对话框并返回窗口句柄。|  
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|从对话框资源创建模式对话框。|  
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|返回`IUnknown`承载在窗口中的控件的接口指针。|  
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|返回`IUnknown`接口指针的宿主对象连接到一个窗口。|  
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|初始化控件承载代码。|  
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|取消初始化的控件承载代码。|  
  
 `HWND`中前三个函数的参数必须是现有 （几乎） 任何类型的窗口。 如果显式调用这三个函数的任何 （通常情况下，不需要），请不要将句柄传递到已充当主机窗口 （如果这样做，现有的宿主对象将不会释放）。  
  
 前七个函数调用[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)隐式。  
  
> [!NOTE]
>  控件承载 API 窗体的 ActiveX 控件包含的 ATL 的支持的基础。 但是，通常会有很少需要直接调用这些函数，如果您充分利用或充分利用 ATL 的包装类。 有关详细信息，请参阅[的 ATL 类促进 ActiveX 控件包含](which-atl-classes-facilitate-activex-control-containment-q.md)。  
  
## <a name="see-also"></a>请参阅  
 [控件包含常见问题](which-atl-classes-facilitate-activex-control-containment-q.md)
