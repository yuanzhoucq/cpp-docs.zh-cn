---
title: 编译器警告 （等级 1） C4964 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4964
dev_langs:
- C++
helpviewer_keywords:
- C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98226b2da465d2301356939273d370d76edcb64e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4964"></a>编译器警告（等级 1）C4964
未不指定任何优化选项;将不会收集配置文件信息  
  
 [/GL](../../build/reference/gl-whole-program-optimization.md)和[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)已指定，但无法使用优化了请求，因此会生成任何对应的.pgc 文件，并且因此，可以不按配置优化。  
  
 如果你想要运行你的应用程序时生成的.pgc 文件，指定其中一个[/O](../../build/reference/o-options-optimize-code.md)编译器选项。  
  
 下面的示例生成 C4964:  
  
```  
// C4964.cpp  
// compile with: /W1 /GL /link /ltcg:pgi  
// C4964 expected  
// Add /O2, for example, to the command line to resolve this warning.  
int main() {  
   int i;  
}  
```