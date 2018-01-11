---
title: "编译器错误 C2309 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2309
dev_langs: C++
helpviewer_keywords: C2309
ms.assetid: 6303d5b5-72cf-42b8-92ce-b1eb48e80d48
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3db8ca4d3a5c3687bf1f99d73579976e221df936
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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