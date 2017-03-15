---
title: "Can I Host More Than One Control in a Single Window? | Microsoft Docs"
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
  - "控件 [ATL], hosting multiple"
  - "windows [C++], hosting multiple controls"
ms.assetid: 3a967a1a-7e7e-42e3-8eed-f7bde912363f
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Can I Host More Than One Control in a Single Window?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

承载超过单个ATL宿主窗口的控件是不可能的。  每个主窗口中设计一次正确存放一个控件\(这允许处理的消息反射和每个控件环境属性简单的机制）。  但是，因此，如果需要用户看到在单个窗口中的多个控件，该控件是一个简单的内容创建多个宿主窗口为该窗口的子窗口。  
  
## 请参阅  
 [控件包含常见问题](../atl/atl-control-containment-faq.md)