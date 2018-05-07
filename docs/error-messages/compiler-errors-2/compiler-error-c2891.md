---
title: 编译器错误 C2891 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2891
dev_langs:
- C++
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01741d1cc67f0045c46ab392212625b9e1a2d8ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2891"></a>编译器错误 C2891
parameter： 不能采用一个模板参数的地址  
  
 不能采用一个模板参数的地址，除非它是左值。 类型参数不是左值，因为它们没有任何地址。 非类型值都不是左值的模板参数列表中还没有一个地址。 这是代码的导致编译器错误 C2891 示例，因为作为模板参数传递的值是代码的编译器生成的复制的模板自变量。  
  
```  
template <int i> int* f() { return &i; }  
```  
  
 都是左值，如引用类型的模板参数可以具有其采用地址。  
  
```  
template <int& r> int* f() { return &r; }  
```  
  
 若要更正此错误，不会模板参数的地址除非它是左值。