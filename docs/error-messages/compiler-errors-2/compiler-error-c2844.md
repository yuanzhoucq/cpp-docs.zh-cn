---
title: "编译器错误 C2844 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2844
dev_langs:
- C++
helpviewer_keywords:
- C2844
ms.assetid: dcaf4cd2-21b0-4280-ae42-0a706c524d83
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 45e0a7eb7a8846d90cc8e0743f5484ba1b58208a
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2844"></a>编译器错误 C2844
member： 不能为接口 interface 的成员  
  
 [接口类](../../windows/interface-class-cpp-component-extensions.md)不能包含的数据成员，除非它也是一个属性。  
  
 在接口中不允许一个属性或成员函数之外的任何内容。 此外，不允许构造函数、 析构函数和运算符。  
  
 下面的示例生成 C2844:  
  
```  
// C2844a.cpp  
// compile with: /clr /c  
public interface class IFace {  
   int i;   // C2844  
   // try the following line instead  
   // property int Size;  
};  
```  

