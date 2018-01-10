---
title: "标记摘要 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 2978cbf6-e66e-46fc-9938-caa052f2ccf7
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1b187b1e7df39acce57691b0e8fd502b88eb3e46
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="summary-of-tokens"></a>标记摘要
*token*：  
 keyword  
  
 *identifier*  
  
 *constant*  
  
 *string-literal*  
  
 *operator*  
  
 `punctuator`  
  
 preprocessing-token:  
 header-name  
  
 *identifier*  
  
 pp-number  
  
 *character-constant*  
  
 *string-literal*  
  
 operator punctuator  
  
 不能成为上述项目之一的每个非空白字符  
  
 header-name:  
 \<  path-spec  > "  path spec  "  
  
 path-spec:  
 合法文件路径  
  
 pp-number:  
 *digit*  
  
 **.** *digit*  
  
 pp-number digit  
  
 pp-number nondigit  
  
 pp-number  e  sign  
  
 pp-number  E  sign  
  
 pp-number  .  
  
## <a name="see-also"></a>请参阅  
 [词法语法](../c-language/lexical-grammar.md)