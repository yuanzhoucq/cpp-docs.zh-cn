---
title: "编译器警告 （等级 1） C4028 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4028
dev_langs:
- C++
helpviewer_keywords:
- C4028
ms.assetid: c3e8b70b-e870-416c-a285-bba5f71dbfc6
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 0041d795ed5afce50592f21f41986d3f32c71fe3
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-warning-level-1-c4028"></a>编译器警告 （等级 1） C4028
形参数字不同于声明  
  
 在声明中的相应参数不一致的形参的类型。 使用原始声明中的类型。  
  
 此警告才有效的 C 源代码。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4028。  
  
```  
// C4028.c  
// compile with: /W1 /Za  
void f(int , ...);  
void f(int i, int j) {}   // C4028  
  
void g(int , int);  
void g(int i, int j) {}   // OK  
  
int main() {}  
```
