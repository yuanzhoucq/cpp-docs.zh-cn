---
title: "编译器错误 C2477 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2477
dev_langs: C++
helpviewer_keywords: C2477
ms.assetid: 60bc324b-6605-4833-8099-a291efc712e7
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 72b83b09ec97a2e7e68b2ee28429eeb31567178c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2477"></a>编译器错误 C2477
member： 不能通过派生类中初始化静态数据成员  
  
 一种模板类的静态数据成员未正确初始化。 若要符合 ISO c + + 标准，这是一项重大更改与在 Visual Studio.NET 2003 中之前, 的 Visual c + + 编译器的版本。  
  
 下面的示例生成 C2477:  
  
```  
// C2477.cpp  
// compile with: /Za /c  
template <class T>  
struct S {  
   static int n;  
};  
  
struct X {};  
struct A: S<X> {};  
  
int A::n = 0;   // C2477  
  
template<>  
int S<X>::n = 0;  
```