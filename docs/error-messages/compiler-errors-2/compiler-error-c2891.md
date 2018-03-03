---
title: "编译器错误 C2891 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2891
dev_langs:
- C++
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 979d77ad5b5bd0b68dd539695d6cb1b60b099c55
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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