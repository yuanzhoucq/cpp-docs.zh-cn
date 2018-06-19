---
title: 编译器错误 C2309 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2309
dev_langs:
- C++
helpviewer_keywords:
- C2309
ms.assetid: 6303d5b5-72cf-42b8-92ce-b1eb48e80d48
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52be559b2e5991e647425b99a1795866046d9050
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33174891"
---
# <a name="compiler-error-c2309"></a>编译器错误 C2309
catch 处理程序预期用圆括号括起来异常声明  
  
 Catch 处理程序有任何用圆括号括起来的类型。  
  
 下面的示例生成 C2309:  
  
```  
// C2309.cpp  
// compile with: /EHsc  
#include <eh.h>  
class C {};  
int main() {  
   try {  
      throw "ooops!";  
   }  
   catch C {}   // C2309  
   // try the following line instead  
   // catch( C ) {}  
}  
```