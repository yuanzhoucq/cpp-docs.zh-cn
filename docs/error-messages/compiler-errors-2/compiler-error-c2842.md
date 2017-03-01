---
title: "编译器错误 C2842 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2842
dev_langs:
- C++
helpviewer_keywords:
- C2842
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: e4b3067b3293892d25dace565538a022e49a6f6f
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2842"></a>编译器错误 C2842
“类”：托管或 WinRT 类型不能定义自己的“operator new”或“operator delete”  
  
 您可以定义自己**new 运算符或**运算符 delete * * 来管理在本机堆上的内存分配。 但是，引用类不能定义这些运算符，因为它们仅分配在托管堆上。  

  
 有关详细信息，请参阅[用户定义运算符 (C + + /cli CLI)](../../dotnet/user-defined-operators-cpp-cli.md)。  
  
## <a name="example"></a>示例  
 以下示例生成 C2842。  
  
```  
// C2842.cpp  
// compile with: /clr /c  
ref class G {  
   void* operator new( size_t nSize );   // C2842  
};  
```  

