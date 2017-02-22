---
title: "组合框处理程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ON_CBN_KILLFOCUS"
  - "ON_CBN_ERRSPACE"
  - "ON_CBN_EDITCHANGE"
  - "ON_CBN_CLOSEUP"
  - "ON_CBN_DBLCLK"
  - "ON_CBN_EDITUPDATE"
  - "ON_CBN_DROPDOWN"
  - "ON_CBN_SELENDOK"
  - "ON_CBN_SELCHANGE"
  - "ON_CBN_SETFOCUS"
  - "ON_CBN_SELENDCANCEL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "组合框, 处理程序"
  - "ON_CBN_CLOSEUP"
  - "ON_CBN_DBLCLK"
  - "ON_CBN_DROPDOWN"
  - "ON_CBN_EDITCHANGE"
  - "ON_CBN_EDITUPDATE"
  - "ON_CBN_ERRSPACE"
  - "ON_CBN_KILLFOCUS"
  - "ON_CBN_SELCHANGE"
  - "ON_CBN_SELENDCANCEL"
  - "ON_CBN_SELENDOK"
  - "ON_CBN_SETFOCUS"
ms.assetid: 7f092412-01b7-4242-95ec-41ba506b9d71
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 组合框处理程序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列映射实体对应于函数原型。  
  
|映射项|函数原型|  
|---------|----------|  
|ON\_CBN\_CLOSEUP \( \<ID\>，\<memberFxn\> \)|afx\_msg void memberFxn\( \);|  
|ON\_CBN\_DBLCLK \( \<ID\>，\<memberFxn\> \)|afx\_msg void memberFxn\( \);|  
|ON\_CBN\_DROPDOWN \( \<ID\>，\<memberFxn\> \)|afx\_msg void memberFxn\( \);|  
|ON\_CBN\_EDITCHANGE \( \<ID\>，\<memberFxn\> \)|afx\_msg void memberFxn\( \);|  
|ON\_CBN\_EDITUPDATE \( \<ID\>，\<memberFxn\> \)|afx\_msg void memberFxn\( \);|  
|ON\_CBN\_ERRSPACE\( \<id\>, \<memberFxn\> \)|afx\_msg void memberFxn\( \);|  
|ON\_CBN\_KILLFOCUS\( \<id\>, \<memberFxn\> \)|afx\_msg void memberFxn\( \);|  
|ON\_CBN\_SELCHANGE \( \<ID\>，\<memberFxn\> \)|afx\_msg void memberFxn\( \);|  
|ON\_CBN\_SELENDCANCEL \( \<ID\>，\<memberFxn\> \)|afx\_msg void memberFxn\( \);|  
|ON\_CBN\_SELENDOK \( \<ID\>，\<memberFxn\> \)|afx\_msg void memberFxn\( \);|  
|ON\_CBN\_SETFOCUS\( \<id\>, \<memberFxn\> \)|afx\_msg void memberFxn\( \);|  
  
## 请参阅  
 [消息映射](../../mfc/reference/message-maps-mfc.md)