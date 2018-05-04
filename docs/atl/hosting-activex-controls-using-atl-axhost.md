---
title: 承载 ActiveX 控件使用 ATL AXHost |Microsoft 文档
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
ms.openlocfilehash: 5057a077e8e778fa3d943b736d51d19af8f60fc6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="hosting-activex-controls-using-atl-axhost"></a>承载 ActiveX 控件使用 ATL 类
本主题中的示例演示如何创建 AXHost 以及如何承载 ActiveX 控件使用各种 ATL 函数。 它还演示如何访问控制和接收器事件 (使用[IDispEventImpl](../atl/reference/idispeventimpl-class.md)) 从承载的控件。 此示例承载主窗口中或在子窗口中的日历控件。  
  
 请注意的定义`USE_METHOD`符号。 你可以更改此符号用于改变介于 1 和 8 之间的值。 符号的值确定将如何创建该控件的创建：  
  
-   中的偶数值`USE_METHOD`，用于创建窗口的主机子类的调用和将其转换为控件主机。 对于奇数的值，该代码创建作为主机子窗口。  
  
-   值`USE_METHOD`1，4，访问控件和事件的事件接收还会创建主机的调用中完成。 介于 5 和 8 之间的值查询接口的主机，并将挂钩接收器。  
  
 摘要如下：  
  
|USE_METHOD|Host|控制访问权限和接收的事件|演示函数|  
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

