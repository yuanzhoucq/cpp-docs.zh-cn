---
title: "Interfaces (ATL) | Microsoft Docs"
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
  - "COM 接口"
  - "接口, COM"
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Interfaces (ATL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

接口是对象公开其功能。外界的方式。  在COM接口，是指针表\(如vtable的c. \+\+\)对对象实现的功能。  表表示接口，因此，函数该点是该接口方法。  当选择，对象可以显示多个接口。  
  
 每个基于接口的COM接口，[IUnknown](../atl/iunknown.md)。  **IUnknown** 方法允许导航到对象公开的接口。  
  
 此外，为每个接口单个接口ID \(IID）。  此唯一性可以轻松地支持版本控制接口。  接口的新版本是新接口，新的IID。  
  
> [!NOTE]
>  标准COM和OLE接口的IIDs预定义。  
  
## 请参阅  
 [COM 介绍](../atl/introduction-to-com.md)   
 [COM Objects and Interfaces](http://msdn.microsoft.com/library/windows/desktop/ms690343)