---
title: "编译器错误 C2555 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2555
dev_langs: C++
helpviewer_keywords: C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c66b464ac38a46716fbed972939feef1273ad03d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2555"></a>编译器错误 C2555
class1::function1： 重写虚函数返回类型不同，且不从 class2::function2 协变  
  
 虚函数和派生的重写函数具有相同的参数列表，但返回类型不同。 在派生类中的重写函数不能从中只是其返回类型的基类的虚函数。  
  
 若要解决此错误，将返回的值转换后调用的虚拟函数。  
  
 如果使用 /clr 进行编译，也可能会看到此错误。   例如，Visual c + + 等效于下面的 C# 声明：  
  
```  
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);  
```  
  
 is  
  
```  
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];  
```  
  
 C2555 的详细信息，请参阅知识库文章 Q240862。  
  
 下面的示例生成 C2555:  
  
```  
// C2555.cpp  
// compile with: /c  
struct X {  
   virtual void func();  
};  
struct Y : X {  
   char func();  // C2555  
   void func2();   // OK  
};  
```