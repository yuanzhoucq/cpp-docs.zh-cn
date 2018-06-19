---
title: 编译器错误 C2467 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2467
dev_langs:
- C++
helpviewer_keywords:
- C2467
ms.assetid: f9ead270-5d0b-41cc-bdcd-586a647c67a7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ed9b1b50c63852ed830c2072d7cd8fce668a671
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225638"
---
# <a name="compiler-error-c2467"></a>编译器错误 C2467
匿名用户定义的类型的非法声明  
  
 未声明的用户定义的嵌套的类型。 编译 C 源代码，与 ANSI 兼容性选项时，这是一个错误 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 启用。  
  
 下面的示例生成 C2467:  
  
```  
//C2467.c  
// compile with: /Za   
int main() {  
   struct X {  
      union { int i; };   // C2467, nested declaration  
   };  
}  
```