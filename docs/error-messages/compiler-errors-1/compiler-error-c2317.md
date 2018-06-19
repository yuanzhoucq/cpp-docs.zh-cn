---
title: 编译器错误 C2317 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2317
dev_langs:
- C++
helpviewer_keywords:
- C2317
ms.assetid: e44d129b-8d3e-4ce9-9d79-6791ee77f25e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82ff1155db69833cad45d9e5df4ccdf016e661e4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33196135"
---
# <a name="compiler-error-c2317"></a>编译器错误 C2317
在行“number”上开始的“try”块没有 catch 处理程序  
  
 `try` 块至少须具有一个 catch 处理程序。  
  
 以下示例生成 C2317：  
  
```  
// C2317.cpp  
// compile with: /EHsc  
#include <eh.h>  
int main() {  
   try {  
      throw "throw an exception";  
   }  
   // C2317, no catch handler  
}  
```  
  
 可能的解决方法：  
  
```  
// C2317b.cpp  
// compile with: /EHsc  
#include <eh.h>  
int main() {  
   try {  
      throw "throw an exception";  
   }  
   catch(char*) {}  
}  
```