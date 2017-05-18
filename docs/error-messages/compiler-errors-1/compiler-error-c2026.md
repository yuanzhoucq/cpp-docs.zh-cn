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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4fafe461008e3545243d693e0d9e34acd57163e0
ms.openlocfilehash: c429f81c64b7710b7edc2b8540d98e8c790e4062
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2026"></a>编译器错误 C2026
字符串太大，已截断尾部字符  
  
 该字符串的长度超出 16380 单字节字符的限制。  
  
 之前在连接的相邻字符串，字符串不能长于 16380 单字节字符。  
  
 大约一半这种长度的 Unicode 字符串还将生成此错误。  
  
 如果您有定义，如下所示的字符串，则会生成 C2026:  
  
```  
char sz[] =  
"\  
imagine a really, really \  
long string here\  
";  
```  
  
 您可以将其分解，如下所示︰  
  
```  
char sz[] =  
"\  
imagine a really, really "  
"long string here\  
";  
```  
  
 您可能想要存储极大的字符串文本 （32k 或以上） 自定义资源或外部文件中。 请参阅[创建新的自定义或数据资源](../../windows/creating-a-new-custom-or-data-resource.md)有关详细信息。
