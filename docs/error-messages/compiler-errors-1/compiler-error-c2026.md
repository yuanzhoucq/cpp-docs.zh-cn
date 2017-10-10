---
title: "编译器错误 C2026 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2026
dev_langs:
- C++
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 97937579c12730fecfa89c69d9e7cf51229b5c6c
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2026"></a>编译器错误 C2026
字符串太大，已截断尾部字符  
  
 字符串的长度超出 16380 单字节字符的限制。  
  
 之前在连接的相邻字符串，字符串不能超过 16380 单字节字符。  
  
 此长度约 50%的 Unicode 字符串还会生成此错误。  
  
 如果你有定义，如下所示的字符串，则会生成 C2026:  
  
```  
char sz[] =  
"\  
imagine a really, really \  
long string here\  
";  
```  
  
 你无法将其分解，如下所示：  
  
```  
char sz[] =  
"\  
imagine a really, really "  
"long string here\  
";  
```  
  
 你可能想要存储特别大的字符串 （32k 或更大） 自定义资源或外部文件中。 请参阅[创建新的自定义资源或数据资源](../../windows/creating-a-new-custom-or-data-resource.md)有关详细信息。
