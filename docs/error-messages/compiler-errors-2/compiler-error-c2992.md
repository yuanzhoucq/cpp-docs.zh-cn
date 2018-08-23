---
title: 编译器错误 C2992 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2992
dev_langs:
- C++
helpviewer_keywords:
- C2992
ms.assetid: 01b16447-43fe-4e91-9a5a-af884a166a31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc21e5db2770c915c1c64f1e48c89e8e5401835d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33245030"
---
# <a name="compiler-error-c2992"></a>编译器错误 C2992
“类”: 参数列表无效或缺失  
  
 此类前加 `template` 或 **generic** 关键字，存在缺失或无效的参数。  
  
## <a name="example"></a>示例  
 以下示例生成 C2992:  
  
```  
// C2992.cpp  
// compile with: /c  
template <class T>   
struct TC1 {  
   template <class U>  
   struct TC2;  
};  
  
template <class T>   struct TC1<T>::TC2 {};   // C2992  
  
// OK  
template <class T>  
template <class U>  
struct TC1<T>::TC2 {};  
 // C2992 can also occur when using generics:  
// C2992c.cpp  
// compile with: /clr /c  
generic <class T>  
ref struct GC1 {  
   generic <class U>  
   ref struct GC2;  
};  
  
generic <class T> ref struct GC1<T>::GC2 {};   // C2992  
  
// OK  
generic <class T>  
generic <class U>  
ref struct GC1<T>::GC2 {};  
```