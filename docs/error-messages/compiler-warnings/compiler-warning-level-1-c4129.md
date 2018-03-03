---
title: "编译器警告 （等级 1） C4129 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4129
dev_langs:
- C++
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6405c7c156f34b49ab892304ee51a6b996ac2595
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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