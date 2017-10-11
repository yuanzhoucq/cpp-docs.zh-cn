---
title: "编译器错误 C3865 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3865
dev_langs:
- C++
helpviewer_keywords:
- C3865
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: af0873d70fcb4f947e838afba130279edf705ced
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3865"></a>编译器错误 C3865
calling_convention： 只能在本机成员函数  
  
 在已全局函数的函数或托管的成员函数上使用的调用约定。 只能对本机 （非托管） 的成员函数进行的调用约定。  
  
 有关详细信息，请参阅[调用约定](../../cpp/calling-conventions.md)。  
  
 下面的示例生成 C3865:  
  
```  
// C3865.cpp  
// compile with: /clr  
// processor: x86  
void __thiscall Func(){}   // C3865  
  
// OK  
struct MyType {  
   void __thiscall Func(){}  
};  
```
