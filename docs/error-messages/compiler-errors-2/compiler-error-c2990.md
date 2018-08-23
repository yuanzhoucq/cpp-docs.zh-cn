---
title: 编译器错误 C2990 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2990
dev_langs:
- C++
helpviewer_keywords:
- C2990
ms.assetid: 674e9f6a-6743-4af0-a7ed-cbe11103a2f8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 669cfcd1e9a715b247c9264856e8877275d6407c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33243024"
---
# <a name="compiler-error-c2990"></a>编译器错误 C2990
class： 非类类型已被声明为类类型  
  
 非泛型或模板类重新定义泛型或模板类。 检查冲突的标头文件。  
  
 下面的示例生成 C2990:  
  
```  
// C2990.cpp  
// compile with: /c  
template <class T>  
class C{};  
class C{};   // C2990  
```  
  
 使用泛型时也可能导致 C2990:  
  
```  
// C2990b.cpp  
// compile with: /clr /c  
generic <class T>  
ref struct GC;  
  
ref struct GC {};   // C2990  
```  
  
 也可能导致 C2990 由于中 Visual c + + 编译器的重大更改为 Visual c + + 2005;编译器现在需要为同一类型的多个声明与模板规范相同。  
  
 下面的示例生成 C2990:  
  
```  
// C2990c.cpp  
// compile with: /c  
template<class T>  
class A;  
  
template<class T>  
struct A2 {  
   friend class A;   // C2990  
};  
  
// OK  
template<class T>  
struct B {  
   template<class T>  
   friend class A;  
};  
```