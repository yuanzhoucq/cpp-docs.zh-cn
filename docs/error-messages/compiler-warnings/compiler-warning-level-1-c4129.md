---
title: 编译器警告 （等级 1） C4129 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4129
dev_langs:
- C++
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc095a32e5cb0d5a0bf240282e11c3fa3382ffe5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276638"
---
# <a name="compiler-warning-level-1-c4129"></a>编译器警告 （等级 1） C4129
character： 无法识别的字符转义序列  
  
 `character`以下反斜杠 (\\) 中的字符或字符串常量不识别为有效的转义序列。 反斜杠是忽略，并且不打印。 对反斜杠后面的字符都将打印。  
  
 若要打印单个反斜杠，指定使用双反斜杠 (\\\\)。  
  
 C + + 标准，2.13.2 节中的讨论了转义序列。  
  
 下面的示例生成 C4129:  
  
```  
// C4129.cpp  
// compile with: /W1  
int main() {  
   char array1[] = "\/709";   // C4129  
   char array2[] = "\n709";   // OK  
}  
```