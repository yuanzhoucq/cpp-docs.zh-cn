---
title: ATL 类促进 ActiveX 控件包含？ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- hosting controls using ATL
- ActiveX control containers [C++], ATL control hosting
ms.assetid: 803a4605-7f4c-4139-8638-49d8783d31b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f024e9929e916e15b110bfc32bc704c4aef755a9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="which-atl-classes-facilitate-activex-control-containment"></a>ATL 类促进 ActiveX 控件包含？
ATL 的控件承载代码不要求你使用任何 ATL 类;你可以只需创建 **"AtlAxWin80"** 窗口和使用控件承载 API，如有必要 (有关详细信息，请参阅**什么是 ATL 控件承载 API**。 但是，以下类使包含功能使用起来更为简便。  
  
|类|描述|  
|-----------|-----------------|  
|[CAxWindow](../atl/reference/caxwindow-class.md)|包装 **"AtlAxWin80"** 窗口中，提供用于创建窗口，创建控件和/或将控件附加到窗口中，并检索该主机对象上的接口指针的方法。|  
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|包装 **"AtlAxWinLic80"** 窗口中，提供用于创建窗口，创建控件和/或将授权的控件附加到窗口中，并检索该主机对象上的接口指针的方法。|  
|[CComCompositeControl](../atl/reference/ccomcompositecontrol-class.md)|充当基于对话框资源的 ActiveX 控件类的基类。 此类控件可以包含其他 ActiveX 控件。|  
|[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)|充当基于对话框资源的对话框类的基类。 此类对话框可以包含 ActiveX 控件。|  
|[CWindow](../atl/reference/cwindow-class.md)|提供一种方法， [GetDlgControl](../atl/reference/cwindow-class.md#getdlgcontrol)，这将返回的接口指针上的控件，给定及其主机窗口的 ID。 此外，Windows API 包装公开`CWindow`通常使窗口管理更加轻松。|  
  
## <a name="see-also"></a>请参阅  
 [控件包含常见问题](../atl/atl-control-containment-faq.md)

