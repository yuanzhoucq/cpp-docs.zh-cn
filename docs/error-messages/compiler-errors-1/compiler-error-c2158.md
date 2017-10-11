---
title: "编译器错误 C2158 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2158
dev_langs:
- C++
helpviewer_keywords:
- C2158
ms.assetid: 39028899-e95c-4809-8e65-6111118641ee
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 84241663685ab1d12581b84bc761dcff77420fd2
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2158"></a>编译器错误 C2158
“type”: 目前只有本机非模板类型才支持 #pragma make_public 指令  
  
 [make_public](../../preprocessor/make-public.md) 杂注只能应用于本机非模板类型。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2158。  
  
```  
// C2158.cpp  
// compile with: /clr /c  
ref class A {};  
#pragma make_public(A)   // C2158  
  
template< typename T >  
class B {};  
#pragma make_public(B)   // C2158  
#pragma make_public(B<int>)   // C2158  
  
void C () {}  
#pragma make_public(C)   // C2158  
  
class D {};  
#pragma make_public(D)   // OK  
```
