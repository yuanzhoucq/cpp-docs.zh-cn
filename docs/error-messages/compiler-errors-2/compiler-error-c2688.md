---
title: "编译器错误 C2688 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2688
dev_langs: C++
helpviewer_keywords: C2688
ms.assetid: 168c9e9d-8f65-4664-af86-db71d3e6ee46
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5b398ec1102ff5d5c795e6734e65564d11cd0ce3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2688"></a>编译器错误 C2688
C2::fgrv： 具有多个协变返回或 varargs 函数不支持的虚拟继承  
  
 当函数包含变量自变量在 Visual c + + 中不支持协变返回类型。  
  
 若要解决此错误，请定义您的函数，因此它们不会使用变量自变量或使返回的值对所有虚函数相同。  
  
 下面的示例生成 C2688:  
  
```  
// C2688.cpp  
struct G1 {};  
struct G2 {};  
struct G3 : G1, G2 {};  
struct G4 {};  
struct G5 {};  
struct G6 : G4, G5 {};  
struct G7 : G3, G6 {};  
  
struct C1 {  
   virtual G4& fgrv(int,...);  
};  
  
struct C2 : C1 {  
   virtual G7& fgrv(int,...);   // C2688, does not return G4&  
};  
```