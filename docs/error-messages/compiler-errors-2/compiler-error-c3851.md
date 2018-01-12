---
title: "编译器错误 C3851 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3851
dev_langs: C++
helpviewer_keywords: C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6c5f0cca8f3c1dfc4b3b35d494ebf73459a74d03
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3851"></a>编译器错误 C3851
“char”：通用字符名称不能指定基本字符集中的字符  
  
 在编译为 C++ 的代码中，无法使用在字符串或字符文本之外表示基本源字符集中的字符的通用字符名称。 有关详细信息，请参阅 [Character Sets](../../cpp/character-sets2.md)。 在编译为 C 的代码中，无法使用范围 0x20 至 0x7f（包含 0x20 和 0x7f）以内的字符的通用字符名称，0x24 ('$')、0x40 ('@') 或 0x60 ('`') 除外。  
  
 下面的示例生成 C3851，并显示如何修复此问题：  
  
```cpp  
// C3851.cpp  
int main()  
{  
   int test1_\u0041 = 0;   // C3851, \u0041 = 'A' in basic character set  
   int test2_A = 0;        // OK  
}  
```