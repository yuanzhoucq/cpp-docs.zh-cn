---
title: "编译器错误 C2603 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2603
dev_langs:
- C++
helpviewer_keywords:
- C2603
ms.assetid: 9ca520d0-f082-4b65-933d-17c3bcf8b02c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c06c5747a3d785242e8b926fe6e1eaa251a2d8b4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2603"></a>编译器错误 C2603  
  
> *函数*： 太多块静态对象的范围与函数中的构造函数/析构函数  
  
在 Visual Studio 2015 之前, 的 Visual c + + 编译器的版本时，或者当[/Zc:threadSafeInit-](../../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md)指定编译器选项，没有为 31 个你可以在外部可见的内联函数中的静态对象数限制.  
  
若要解决此问题，我们建议你采用较新版本的 Visual c + + 编译器工具集，或如果可能，请删除 /Zc:threadSafeInit-编译器选项。 如果这是不可能，请考虑将静态对象。 如果同一类型的对象，请考虑使用该类型的单个静态数组，并且引用所需的各个成员。
  
## <a name="example"></a>示例  
  
下面的代码生成 C2603，并演示修复此错误的一种方法：  
  
```cpp  
// C2603.cpp  
// Compile by using: cl /W4 /c /Zc:threadSafeInit- C2603.cpp
struct C { C() {} };  
extern inline void f1() {  
    static C C01, C02, C03, C04, C05, C06, C07, C08, C09, C10;
    static C C11, C12, C13, C14, C15, C16, C17, C18, C19, C20;
    static C C21, C22, C23, C24, C25, C26, C27, C28, C29, C30, C31;  
    static C C32;   // C2603 Comment this line out to avoid error  
}  
```
