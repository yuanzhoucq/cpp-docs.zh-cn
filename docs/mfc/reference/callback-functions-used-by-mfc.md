---
title: "MFC 使用的回调函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.functions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "回调函数"
  - "回调函数, MFC"
  - "函数 [C++], 回调"
  - "MFC, 回调函数"
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# MFC 使用的回调函数
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

三回调函数出现在 Microsoft 基础类库。  传递给回调函数，并按照 [CDC::EnumObjects](../Topic/CDC::EnumObjects.md)[CDC::GrayString](../Topic/CDC::GrayString.md)[CDC::SetAbortProc](../Topic/CDC::SetAbortProc.md) 的说明本主题。  有关回调函数的基本用法，请参见这些成员函数的"备注"节。  注意任何回调函数必须在返回之前捕获 MFC 异常到窗口，因为异常回调不能跨边界引发。  有关异常的更多信息，请参见知识库文章 [异常](../../mfc/exception-handling-in-mfc.md)。  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)