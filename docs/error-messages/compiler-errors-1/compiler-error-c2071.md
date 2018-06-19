---
title: 编译器错误 C2071 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2071
dev_langs:
- C++
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: faee56023d14e9b010d1c691af654ffcbc31dc78
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169200"
---
# <a name="compiler-error-c2071"></a>编译器错误 C2071
identifier： 非法存储类  
  
 `identifier` 已使用无效声明[存储类](../../c-language/c-storage-classes.md)。 为标识符指定多个存储类时或定义与存储类声明不兼容时，会导致此错误。  
  
 若要解决此问题，请了解标识符的预期的存储类 — 例如，`static`或`extern`-并更正要匹配的声明。  
  
## <a name="example"></a>示例  
 以下示例生成 C2071。  
  
```  
// C2071.cpp  
// compile with: /c  
struct C {  
   extern int i;   // C2071  
};  
struct D {  
   int i;   // OK, no extern on an automatic  
};  
```  
  
## <a name="example"></a>示例  
 以下示例生成 C2071。  
  
```  
// C2071_b.cpp  
// compile with: /c  
typedef int x(int i) { return i; }   // C2071  
typedef int (x)(int);   // OK, no local definition in typedef  
```