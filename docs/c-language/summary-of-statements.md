---
title: "语句摘要 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: ce45d2fe-ec0e-459f-afb1-80ab6a7f0239
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ba646cbd4443d75eaf8414dbb6ce23797411ade6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="summary-of-statements"></a>语句摘要
statement：  
 *labeled-statement*  
  
 *compound-statement*  
  
 *expression-statement*  
  
 *selection-statement*  
  
 iteration-statement  
  
 jump-statement  
  
 try-except-statement /* Microsoft 专用\*/  
  
 try-finally-statement /* Microsoft 专用\*/  
  
 *jump-statement*:  
 goto  identifier  ;  
  
 continue ;  
  
 break ;  
  
 return  expressionopt;  
  
 compound-statement：  
 {  declaration-listoptstatement-listopt}  
  
 declaration-list：  
 declaration  
  
 declaration-list declaration  
  
 statement-list：  
 statement  
  
 statement-list statement  
  
 expression-statement：  
 expressionopt;  
  
 *iteration-statement*:  
 while (  expression  )  statement  
  
 do  statement  while (  expression  ) ;  
  
 for (  expressionopt; expressionopt; expressionopt) statement  
  
 *selection-statement*:  
 if (  expression  )  statement  
  
 if (  expression  )  statement  else  statement  
  
 switch (  expression  )  statement  
  
 *labeled-statement*:  
 identifier  :  statement  
  
 **case**  *constant-expression*  **:**  *statement*  
  
 **default :**  *statement*  
  
 try-except-statement:   /\* Microsoft 专用\*/  
 **__try**  *compound-statement*  
  
 **__except (**  *expression*  **)**  *compound-statement*  
  
 try-finally-statement:   /\* Microsoft 专用\*/  
 **__try**  *compound-statement*  
  
 __finally compound-statement  
  
## <a name="see-also"></a>请参阅  
 [短语结构语法](../c-language/phrase-structure-grammar.md)