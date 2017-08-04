---
title: "外部定义 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- external definitions
- external linkage, variable declarations
ms.assetid: 41e37bfc-b360-43b1-9972-28af2d365b20
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 918775a68b7497bb931694c99e9f1b20bc304639
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="external-definitions"></a>外部定义
translation-unit：  
external-declaration **  
  
 translation-unit external-declaration  
  
 external-declaration:       /\* 只允许在外部（文件）范围内 \*/  
function-definition **  
  
 `declaration`  
  
 function-definition:         /\* 此处的声明符是函数声明符 \*/  
declaration-specifiers ** optdeclarator declaration-list optcompound-statement  
  
## <a name="see-also"></a>另请参阅  
 [短语结构语法](../c-language/phrase-structure-grammar.md)
