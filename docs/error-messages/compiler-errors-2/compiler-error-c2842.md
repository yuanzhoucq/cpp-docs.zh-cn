---
title: 编译器错误 C2842 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2842
dev_langs:
- C++
helpviewer_keywords:
- C2842
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fe0a95edfa484eb8606b914424e52483c4c1c52d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2842"></a>编译器错误 C2842
“类”：托管或 WinRT 类型不能定义自己的“operator new”或“operator delete”  
  
 你可以定义自己 * * 运算符 new 或**运算符 delete**来管理本机堆上的内存分配。 但是，引用类不能定义这些运算符，因为它们仅分配在托管堆上。  

  
 有关详细信息，请参阅[用户定义的运算符 (C + + /cli CLI)](../../dotnet/user-defined-operators-cpp-cli.md)。  
  
## <a name="example"></a>示例  
 以下示例生成 C2842。  
  
```  
// C2842.cpp  
// compile with: /clr /c  
ref class G {  
   void* operator new( size_t nSize );   // C2842  
};  
```  
