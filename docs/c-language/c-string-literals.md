---
title: C 字符串文本 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- string literals, syntax
- strings [C++], string literals
- literal strings, C
ms.assetid: 4b05523e-49a2-4900-b21a-754350af3328
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 303ad83c5e366f32a99a501a58b168ef25adbb42
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="c-string-literals"></a>C 字符串文本
“字符串文本”是封闭在双引号 (" ") 内的源字符集中的字符序列。 字符串用于表示可一起构成以 null 结尾的字符串的字符序列。 必须在宽字符串文本前添加字母 L 作为前缀。  
  
## <a name="syntax"></a>语法  
 string-literal：  
 " s-char-sequence opt"  
  
 L" s-char-sequence opt"  
  
 s-char-sequence：  
 s-char  
  
 s-char-sequence s-char  
  
 s-char：  
 除双引号 (")、反斜杠 (\\) 或者换行符以外的任何源字符集成员  
  
 escape-sequence  
  
 以下示例是一个简单的字符串：  
  
```  
char *amessage = "This is a string literal.";  
```  
  
 在[转义序列](../c-language/escape-sequences.md)表中列出的所有转义码在字符串文本中均有效。 若要表示字符串文本中的双引号，请使用转义序列 \\"。 可在不使用转义序列的情况下表示单引号 (')。 反斜杠 (\\) 在字符串中出现时必须后跟另一个反斜杠 (\\\\)。 当反斜杠出现在行的末尾时，始终解释为行继续符。  
  
## <a name="see-also"></a>请参阅  
 [C 的元素](../c-language/elements-of-c.md)