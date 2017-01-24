---
title: "ATL Connection Point Example | Microsoft Docs"
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
  - "连接点 [C++], 示例"
  - "examples [ATL]"
ms.assetid: a49721b7-f308-43de-8868-f662a94bc81a
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL Connection Point Example
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此示例演示支持 [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) 为输出接口的对象:  
  
 [!code-cpp[NVC_ATL_Windowing#84](../atl/codesnippet/CPP/atl-connection-point-example_1.h)]  
  
 当指定 `IPropertyNotifySink` 为输出接口时，可以使用选件类 [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) 而不是 `IConnectionPointImpl`。  例如：  
  
 [!code-cpp[NVC_ATL_Windowing#85](../atl/codesnippet/CPP/atl-connection-point-example_2.h)]  
  
## 请参阅  
 [连接点](../atl/atl-connection-points.md)