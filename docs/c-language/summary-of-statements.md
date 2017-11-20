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
ms.openlocfilehash: a8fbebed0608ba21973fdc93d2812b497ca3dc83
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="summary-of-statements"></a>语句摘要
statement：  
 labeled-statement  
  
 compound-statement  
  
 expression-statement  
  
 selection-statement  
  
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
  
## <a name="see-also"></a>另请参阅  
 [短语结构语法](../c-language/phrase-structure-grammar.md)