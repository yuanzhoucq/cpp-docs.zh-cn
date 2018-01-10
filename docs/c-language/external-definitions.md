---
title: "外部定义 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- external definitions
- external linkage, variable declarations
ms.assetid: 41e37bfc-b360-43b1-9972-28af2d365b20
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2242eca9bf39aef4dc26a4450377f32e2e554b89
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="external-definitions"></a>外部定义
translation-unit：  
 external-declaration  
  
 translation-unit external-declaration  
  
 external-declaration:       /\* 只允许在外部（文件）范围内 \*/  
 function-definition  
  
 `declaration`  
  
 function-definition:         /\* 此处的声明符是函数声明符 \*/  
 declaration-specifiers optdeclarator declaration-list optcompound-statement  
  
## <a name="see-also"></a>请参阅  
 [短语结构语法](../c-language/phrase-structure-grammar.md)