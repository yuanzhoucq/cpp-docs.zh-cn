---
title: "初始化字符串 | Microsoft Docs"
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
- character arrays, initializing
- strings [C++], initializing
- initializing arrays, strings
ms.assetid: 0ab8079d-d0d3-48f9-afd1-36a7bb439b29
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
ms.openlocfilehash: c1bf614544f008910a86e8281cb775c1d7734b0d
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="initializing-strings"></a>初始化字符串
您可以使用字符串文本（或宽字符串文本）初始化字符（或宽字符）的数组。 例如：  
  
```  
char code[ ] = "abc";  
```  
  
 将 `code` 初始化为一个四元素字符数组。 第四个元素为 null 字符，用于终止所有字符串文本。  
  
 标识符列表的长度值只能与要初始化的标识符的数量相同。 如果指定短于字符串的数组大小，则会忽略多余字符。 例如，以下声明将 `code` 初始化为一个三元素字符数组：  
  
```  
char code[3] = "abcd";  
```  
  
 只有初始值设定项的前三个字符将分配给 `code`。 字符 `d` 和字符串终止 null 字符将被丢弃。 请注意，这将创建一个非终止字符串（即，没有 0 值标记其结束的字符串）并生成指示这种情况的诊断消息。  
  
 声明  
  
```  
char s[] = "abc", t[3] = "abc";  
```  
  
 等同于  
  
```  
char s[]  = {'a', 'b', 'c', '\0'},   
     t[3] = {'a', 'b', 'c' };  
```  
  
 如果字符串短于指定的数组大小，数组中的剩余元素将初始化为 0。  
  
 **Microsoft 专用**  
  
 在 Microsoft C 中，字符串文本的长度最大为 2048 个字节。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [初始化](../c-language/initialization.md)
