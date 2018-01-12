---
title: "编译器警告 （等级 1） C4537 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4537
dev_langs: C++
helpviewer_keywords: C4537
ms.assetid: 9454493c-d419-475e-8f35-9c00233c9329
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8cdc3cc00b1b6ea52657f441423e61c3003652ce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4537"></a>编译器警告（等级 1）C4537
object: operator 应用于非 UDT 类型  
  
 已传递的引用，需要的对象 （用户定义类型） 的位置。 引用不是一个对象，但内联汇编程序代码不能使这种差异。 编译器将生成代码，如同***对象***已实例。  
  
 下面的示例生成 C4537:  
  
```  
// C4537.cpp  
// compile with: /W1 /c  
// processor: x86  
struct S {  
   int member;  
};  
  
void f1(S &s) {  
   __asm mov eax, s.member;   // C4537  
   // try the following code instead  
   // or, make the declaration "void f1(S s)"  
   /*  
   mov eax, s  
   mov eax, [eax]s.member  
   */  
}  
```