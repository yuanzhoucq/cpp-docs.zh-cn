---
title: "编译器警告 （等级 4） C4239 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4239
dev_langs: C++
helpviewer_keywords: C4239
ms.assetid: a23dc16a-649e-4870-9a24-275de1584fcd
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ac667ac760e9dbee33da7beb2abcaf3a00e0edbc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4239"></a>编译器警告（等级 4）C4239
使用的非标准扩展: token： 从 type 到 type 的转换  
  
 此类型转换不允许通过 c + + 标准，但它允许此处作为扩展。 此警告始终后跟至少一个行的说明，以描述违反语言规则。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4239。  
  
```  
// C4239.cpp  
// compile with: /W4 /c  
struct C {  
   C() {}  
};  
  
void func(void) {  
   C & rC = C();   // C4239  
   const C & rC2 = C();   // OK  
   rC2;  
}  
```  
  
## <a name="example"></a>示例  
 严格不允许从整数类型转换为枚举类型。  
  
 下面的示例生成 C4239。  
  
```  
// C4239b.cpp  
// compile with: /W4 /c  
enum E { value };   
struct S {   
   E e : 2;   
} s = { 5 };   // C4239   
// try the following line instead  
// } s = { (E)5 };  
```