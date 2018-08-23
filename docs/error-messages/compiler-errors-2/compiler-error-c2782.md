---
title: 编译器错误 C2782 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2782
dev_langs:
- C++
helpviewer_keywords:
- C2782
ms.assetid: 8b685422-294d-4f64-9f3d-c14eaf03a93d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ffbe6cd7a2880b1be07a89420d17bf68cc337d3d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234037"
---
# <a name="compiler-error-c2782"></a>编译器错误 C2782
declaration： 模板参数 identifier 不明确  
  
 编译器无法确定模板自变量的类型。  
  
 下面的示例生成 C2782:  
  
```  
// C2782.cpp  
template<typename T>  
void f(T, T) {}  
  
int main() {  
   f(1, 'c');   // C2782  
   // try the following line instead  
   // f<int>(1, 'c');  
}  
```  
  
 使用泛型时也可能发生 C2782:  
  
```  
// C2782b.cpp  
// compile with: /clr  
generic<typename T> void gf(T, T) { }  
  
int main() {  
   gf(1, 'c'); // C2782  
   // try the following line instead  
   // gf<int>(1, 'c');  
}  
```