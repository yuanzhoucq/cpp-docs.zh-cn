---
title: "语句摘要 | Microsoft Docs"
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
  - "C"
ms.assetid: ce45d2fe-ec0e-459f-afb1-80ab6a7f0239
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 语句摘要
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*statement*:  
 *labeled\-statement*  
  
 *compound\-statement*  
  
 *expression\-statement*  
  
 *selection\-statement*  
  
 *iteration\-statement*  
  
 *jump\-statement*  
  
 *try\-except\-statement* \/\* Microsoft 专用 \*\/  
  
 *try\-finally\-statement* \/\* Microsoft 专用 \*\/  
  
 *jump\-statement*：  
 **goto**  *identifier*  **;**  
  
 **continue ;**  
  
 **break ;**  
  
 **return**  *expression* opt **;**  
  
 *compound\-statement*:  
 **{**  *declaration\-list* opt *statement\-list* opt **}**  
  
 *declaration\-list*:  
 *declaration*  
  
 *declaration\-list declaration*  
  
 *statement\-list*:  
 *statement*  
  
 *statement\-list statement*  
  
 *expression\-statement*:  
 *expression* opt **;**  
  
 *iteration\-statement*:  
 **while \(**  *expression*  **\)**  *statement*  
  
 **do**  *statement*  **while \(**  *expression*  **\) ;**  
  
 **for \(**  *expression* opt **;** *expression* opt **;** *expression* opt **\)** *statement*  
  
 *selection\-statement*:  
 **if \(**  *expression*  **\)**  *statement*  
  
 **if \(**  *expression*  **\)**  *statement*  **else**  *statement*  
  
 **switch \(**  *expression*  **\)**  *statement*  
  
 *labeled\-statement*:  
 *identifier*  **:**  *statement*  
  
 **case**  *constant\-expression*  **:**  *statement*  
  
 **default :**  *statement*  
  
 *try\-except\-statement*:   \/\* Microsoft 专用 \*\/  
 **\_\_try**  *compound\-statement*  
  
 **\_\_except \(**  *expression*  **\)**  *compound\-statement*  
  
 *try\-finally\-statement*:   \/\* Microsoft 专用 \*\/  
 **\_\_try**  *compound\-statement*  
  
 **\_\_finally**  *compound\-statement*  
  
## 请参阅  
 [短语结构语法](../c-language/phrase-structure-grammar.md)