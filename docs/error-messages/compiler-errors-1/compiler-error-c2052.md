---
title: "编译器错误 C2052 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2052
dev_langs:
- C++
helpviewer_keywords:
- C2052
ms.assetid: 922ca43b-b64b-4ef7-9611-c7313be3fd79
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: e4c90a50dbd6a7d59d195d6b92ae0a10d79285fc
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2052"></a>编译器错误 C2052
type： 非法的 case 表达式类型  
  
 Case 表达式必须是整数常量。  
  
 下面的示例生成 C2052:  
  
```  
// C2052.cpp  
int main() {  
   int index = 0;  
   switch (index) {  
      case 1:  
         return 24;  
      case 1.0:   // C2052  
      // try the following line instead  
      // case 2:  
         return 23;  
   }  
}  
```
