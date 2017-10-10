---
title: "编译器错误 C2467 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2467
dev_langs:
- C++
helpviewer_keywords:
- C2467
ms.assetid: f9ead270-5d0b-41cc-bdcd-586a647c67a7
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: a51321e6597bffe0dded58ffa481f054e770f9b7
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2467"></a>编译器错误 C2467
匿名用户定义的类型的非法声明  
  
 未声明的用户定义的嵌套的类型。 编译 C 源代码，与 ANSI 兼容性选项时，这是一个错误 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 启用。  
  
 下面的示例生成 C2467:  
  
```  
//C2467.c  
// compile with: /Za   
int main() {  
   struct X {  
      union { int i; };   // C2467, nested declaration  
   };  
}  
```
