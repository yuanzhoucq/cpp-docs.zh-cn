---
title: "编译器警告 （等级 3） C4316 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4316
dev_langs: C++
helpviewer_keywords: C4316
ms.assetid: 10371f01-aeb8-40ac-a290-59e63efa5ad4
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0a36f436090ef7ca3790f4bd5dd15443c0ed52f9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4316"></a>编译器警告 （等级 3） C4316
没有可能对此类型对齐在堆上分配的对象。  
  
 通过使用分配的过度对齐的对象`operator new`可能没有指定的对齐方式。 重写[运算符 new](../../c-runtime-library/operator-new-crt.md)和[运算符 delete](../../c-runtime-library/operator-delete-crt.md)的过度对齐类型，以便他们使用对齐的分配例程 — 例如， [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md)和[_aligned_free](../../c-runtime-library/reference/aligned-free.md)。 下面的示例生成 C4316:  
  
```cpp  
// C4316.cpp  
// Test: cl /W3 /c C4316.cpp  
  
__declspec(align(32)) struct S {}; // C4324  
  
int main() {  
    new S; // C4316  
}  
```