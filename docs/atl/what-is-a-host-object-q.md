---
title: "What Is a Host Object? | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "host objects"
ms.assetid: 4f8da992-b27e-45e8-b5e0-c8b1dcae4fac
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# What Is a Host Object?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

宿主对象是表示特定窗口的ATL提供的ActiveX控件容器的COM对象。  宿主对象子类容器窗口，以便能够反映消息到控件，它提供控件将使用所必需的容器接口，因此，它显示 [IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md) 和 [IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md) 接口允许配置控件的环境。  
  
 您可以使用宿主对象将容器的单个属性。  
  
## 请参阅  
 [控件包含常见问题](../atl/atl-control-containment-faq.md)