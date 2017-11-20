---
title: "编译器错误 C2650 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2650
dev_langs: C++
helpviewer_keywords: C2650
ms.assetid: 49a8ac6e-aa6d-4616-917c-a3cfcdbad5a4
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c3352820434c8d794d4980a606cb945bd8ecc4a8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2650"></a>编译器错误 C2650
operator： 不能为虚函数  
  
 A`new`或`delete`运算符被声明为`virtual`。 这些运算符是`static`成员函数，不能为`virtual`。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2650:  
  
```  
// C2650.cpp  
// compile with: /c  
class A {  
   virtual void* operator new( unsigned int );   // C2650  
   // try the following line instead  
   // void* operator new( unsigned int );  
};  
```