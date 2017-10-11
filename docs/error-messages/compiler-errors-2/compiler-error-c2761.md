---
title: "编译器错误 C2761 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2761
dev_langs:
- C++
helpviewer_keywords:
- C2761
ms.assetid: 38c79a05-b56d-485b-820f-95e8c0cb926f
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 7670c3fa67579c218024dfd3f1f585ad57cf37e5
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2761"></a>编译器错误 C2761
function： 不允许的成员函数重新声明  
  
 不能重新声明成员函数。 您可以定义它，但不是能重新声明。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2761。  
  
```  
// C2761.cpp  
class a {  
   int t;  
   void test();  
};  
  
void a::a;     // C2761  
void a::test;  // C2761  
  
```  
  
## <a name="example"></a>示例  
 不能定义类或结构的非静态成员。  下面的示例生成 C2761。  
  
```  
// C2761_b.cpp  
// compile with: /c  
struct C {  
   int s;  
   static int t;  
};  
  
int C::s;   // C2761  
int C::t;   // OK  
```
