---
title: 编译器错误 C2555 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2555
dev_langs:
- C++
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d2d1a710177e2c8c72b0afeff662dddf1c22ef5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
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