---
title: 承载 ActiveX 控件使用 ATL AXHost |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CAxWindow2T class
- Calendar control (ActiveX), hosting with ATL AXHost
- Calendar control (ActiveX)
- ActiveX controls [C++], hosting
- hosting ActiveX controls
- AXHost method
ms.assetid: 2c1200ec-effb-4814-820a-509519699468
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e26fd9e80b96c2b0196e3fd0e11b9c97f0f3bff3
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2018
ms.locfileid: "39027201"
---
# <a name="hosting-activex-controls-using-atl-axhost"></a>使用 ATL AXHost 承载 ActiveX 控件
本主题中的示例演示如何创建 AXHost 以及如何托管 ActiveX 控件使用各种 ATL 函数。 它还演示如何访问控制和接收器事件 (使用[IDispEventImpl](../atl/reference/idispeventimpl-class.md)) 从承载的控件。 此示例承载日历控件在主窗口中或在子窗口。  
  
 请注意 USE_METHOD 符号的定义。 可以更改此符号来改变介于 1 和 8 之间的值。 符号的值确定将如何创建控件：  
  
-   USE_METHOD，调用创建主机子类的窗口的偶数值，并将它转换为控件宿主。 对于奇数的值，该代码创建充当一个主机的子窗口。  
  
-   对控件的访问的 USE_METHOD 介于 1 和 4 之间的值和事件的事件接收完成的调用中，还会创建主机。 介于 5 到 8 之间的值查询接口的主机，并挂接接收器。  
  
摘要如下：  
  
|USE_METHOD|Host|控制访问和事件接收|说明的函数|  
|-----------------|----------|--------------------------------------|---------------------------|  
|1|子窗口|一个步骤|CreateControlLicEx|  
|2|主窗口|一个步骤|AtlAxCreateControlLicEx|  
|3|子窗口|一个步骤|CreateControlEx|  
|4|主窗口|一个步骤|AtlAxCreateControlEx|  
|5|子窗口|多个步骤|CreateControlLic|  
|6|主窗口|多个步骤|AtlAxCreateControlLic|  
|7|子窗口|多个步骤|CreateControl|  
|8|主窗口|多个步骤|AtlAxCreateControl|  
  
 [!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [控件包含常见问题](../atl/atl-control-containment-faq.md)   
 [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)   
 [AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)   
 [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)   
 [AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)   
 [CAxWindow2T 类](../atl/reference/caxwindow2t-class.md)   
 [IAxWinHostWindowLic 接口](../atl/reference/iaxwinhostwindowlic-interface.md)

