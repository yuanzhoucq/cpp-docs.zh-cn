---
title: "容器中的 RDO 数据控件承载模型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RDO RemoteData 控件, 承载模型"
  - "RemoteData 控件, 承载模型"
ms.assetid: ca598bac-9fef-40e6-b6cd-03d817e16b2e
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 容器中的 RDO 数据控件承载模型
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

容器承载 RDO 数据控件的方法为：  
  
-   容器从数据控件获得 IVBDSC 接口。  如果它无法找到 IVBDSC，则该控件不是数据控件。  
  
-   容器从数据控件获得 **ICursor** 接口。  这些接口提供可由客户端操作的 Cursor 对象。  
  
-   容器挂钩到数据控件的 **INotifyDBEvents** 接口。  该接口允许容器接收来自数据控件的通知。  容器应支持 **INotifyDBEventsSink** 接口以实现此操作。  
  
 容器承载 RDO 数据绑定控件的方法为：  
  
-   控件支持 **IBoundObject** 接口并且容器支持 **IBoundObjectSite** 接口。  控件获得容器的 **IBoundObjectSite** 接口，而容器从控件获得 **IBoundObject** 接口。  
  
-   控件支持 **IPropNotifySink** 接口，并与容器挂钩。  这允许容器接收来自控件的通知。  
  
-   如果控件支持 **INotifyDBEventsSink**，则它在与数据控件的 **INotifyDBEvents** 接口连接后，可接收来自 RDO 数据控件的通知。  
  
-   然后，控件可以（直接或通过容器）从数据控件接收 Cursor 对象。  然后可以操作并滚动游标。  到这里，RDO 数据绑定控件已成功绑定。  
  
## 请参阅  
 [RDO 数据绑定](../../data/ado-rdo/rdo-databinding.md)   
 [在 Visual C\+\+ 中使用 RDO 数据绑定](../../data/ado-rdo/using-rdo-databinding-in-visual-cpp.md)