---
title: "用户定义的处理程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.handlers"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ON_MESSAGE 宏"
  - "ON_REGISTERED_MESSAGE 宏"
  - "用户定义的处理程序"
ms.assetid: 99478294-bef0-4ba7-a369-25a6abdcdb62
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 用户定义的处理程序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列映射实体对应于函数原型。  
  
|映射项|函数原型|  
|---------|----------|  
|ON\_MESSAGE \( \<消息\>，\<memberFxn\> \)|afx\_msg LRESULT memberFxn \(WPARAM，LPARAM\);|  
|ON\_REGISTERED\_MESSAGE \( \<nMessageVariable\>，\<memberFxn\> \)|afx\_msg LRESULT memberFxn \(WPARAM，LPARAM\);|  
|ON\_THREAD\_MESSAGE \( \<消息\>，\<memberFxn\> \)|afx\_msg 无效 memberFxn \(WPARAM，LPARAM\);|  
|ON\_REGISTERED\_THREAD\_MESSAGE\( \<nMessageVariable\>, \<memberFxn\> \)|afx\_msg 无效 memberFxn \(WPARAM，LPARAM\);|  
  
## 请参阅  
 [消息映射](../../mfc/reference/message-maps-mfc.md)   
 [WM\_ 消息的处理程序](../../mfc/reference/handlers-for-wm-messages.md)