---
title: 编译器错误 C2720 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2720
dev_langs:
- C++
helpviewer_keywords:
- C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c6215cd2e83f1fa3a48c3cbd4970cd2d3466fc0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233521"
---
# <a name="compiler-error-c2720"></a>编译器错误 C2720  
  
> *标识符*:*说明符*非法成员上的存储类说明符  
  
存储类无法用于声明外部的类成员。 若要解决此错误，删除不需要[存储类](../../cpp/storage-classes-cpp.md)从类声明外部的成员定义的说明符。  
  
## <a name="example"></a>示例  
  
下例生成了 C2720，并介绍了如何修复此错误：  
  
```cpp  
// C2720.cpp  
struct S {  
   static int i;  
};  
static S::i;   // C2720 - remove the unneeded 'static' to fix it  
```