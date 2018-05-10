---
title: 外部定义 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- external definitions
- external linkage, variable declarations
ms.assetid: 41e37bfc-b360-43b1-9972-28af2d365b20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bd1ce5a214e33fed66aa5f54a57c1cc1d15473e6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
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