---
title: "编译器错误 C3075 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3075
dev_langs:
- C++
helpviewer_keywords:
- C3075
ms.assetid: f431daa9-e0fa-48f0-a5c3-f99be96b55e3
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 8197297ffd2f75afede3876577f249d3e07c6abb
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3075"></a>编译器错误 C3075
“instance”：无法将引用类型“type”的实例嵌入到值类型中  
  
 值类型不能包含引用类型的实例。  
  
 有关详细信息，请参阅[对于引用类型的 c + + 堆栈语义](../../dotnet/cpp-stack-semantics-for-reference-types.md)。  
  
## <a name="example"></a>示例  
 以下示例生成 C3075。  
  
```  
// C3075.cpp  
// compile with: /clr /c  
ref struct U {};  
value struct X {  
   U y;   // C3075  
};  
  
ref struct Y {  
   U y;   // OK  
};  
```
