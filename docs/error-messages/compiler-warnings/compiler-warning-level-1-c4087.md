---
title: 编译器警告 （等级 1） C4087 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4087
dev_langs:
- C++
helpviewer_keywords:
- C4087
ms.assetid: 546e4d57-5c8e-422c-8ef1-92657336dad5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5b9962abc29b94425f96c978f3dd7e8d3f7c251
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33278439"
---
# <a name="compiler-warning-level-1-c4087"></a>编译器警告（等级 1）C4087
“function”：用“void”参数列表声明  
  
 函数声明没有形参，而函数调用具有实参。 根据该函数的调用约定传递了额外的参数。  
  
 此警告针对 C 编译器。  
  
## <a name="example"></a>示例  
  
```  
// C4087.c  
// compile with: /W1  
int f1( void ) {  
}  
  
int main() {  
   f1( 10 );   // C4087  
}  
```