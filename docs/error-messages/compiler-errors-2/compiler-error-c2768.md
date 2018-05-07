---
title: 编译器错误 C2768 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2768
dev_langs:
- C++
helpviewer_keywords:
- C2768
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ee0fd3fa213639e70199cfe5653ee2034bc39b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2768"></a>编译器错误 C2768
function： 非法使用显式模板自变量  
  
 编译器无法确定是否应该函数定义的显式专用化函数模板，或者函数定义应该用于新函数。  
  
 此错误的引入了在 Visual Studio.NET 2003 中，编译器一致性增强功能的一部分。  
  
 下面的示例生成 C2768:  
  
```  
// C2768.cpp  
template<typename T>  
void f(T) {}  
  
void f<int>(int) {}   // C2768  
  
// an explicit specialization  
template<>  
void f<int>(int) {}   
  
// global nontemplate function overload  
void f(int) {}  
```