---
title: 编译器错误 C3857 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3857
dev_langs:
- C++
helpviewer_keywords:
- C3857
ms.assetid: 9f746d1e-9708-4945-bc29-3150d5371d3c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4a9277ccd6a4e1e71faaf634498ccf32378fc961
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3857"></a>编译器错误 C3857
type： 不允许多个类型参数列表  
  
 为同一类型，这不允许指定多个模板或泛型。  
  
 下面的示例生成 C3857:  
  
```  
// C3857.cpp  
template <class T, class TT>  
template <class T2>    // C3857  
struct B {};  
```  
  
 可能的解决方法：  
  
```  
// C3857b.cpp  
// compile with: /c  
template <class T, class TT, class T2>   
struct B {};  
```  
  
 使用泛型时，也可能发生 C3857:  
  
```  
// C3857c.cpp  
// compile with: /clr  
generic <typename T>  
generic <typename U>  
ref class GC;   // C3857  
```  
  
 可能的解决方法：  
  
```  
// C3857d.cpp  
// compile with: /clr /c  
generic <typename U>  
ref class GC;  
```