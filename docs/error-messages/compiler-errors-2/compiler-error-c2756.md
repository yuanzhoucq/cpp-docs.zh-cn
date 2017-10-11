---
title: "编译器错误 C2756 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2756
dev_langs:
- C++
helpviewer_keywords:
- C2756
ms.assetid: 42eb988d-4043-4dee-8fd4-596949f69a55
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 4ca6e01d1c4b2f7dda2a941eeef4599d62241fe3
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2756"></a>编译器错误 C2756
“模板类型”: 部分专用化中不允许有默认模板自变量  
  
 部分专用化的模板不能包含默认自变量。  
  
 下面的示例生成 C2756，并演示如何修复此错误：  
  
```  
// C2756.cpp  
template <class T>  
struct S {};  
  
template <class T=int>  
// try the following line instead  
// template <class T>  
struct S<T*> {};   // C2756  
```
