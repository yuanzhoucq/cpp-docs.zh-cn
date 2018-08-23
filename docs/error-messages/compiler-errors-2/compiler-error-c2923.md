---
title: 编译器错误 C2923 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2923
dev_langs:
- C++
helpviewer_keywords:
- C2923
ms.assetid: 6b92933b-13ef-4124-99d9-b89f9fdae030
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b71470ed288abe0a0868c788917dfcecdeeb914a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33241495"
---
# <a name="compiler-error-c2923"></a>编译器错误 C2923
“type”: 对于参数“param”，“identifier”不是有效的模板类型参数  
  
 参数列表缺少实例化模板或泛型所需的类型。 检查模板或泛型声明。  
  
 下面的示例生成 C2923：  
  
```  
// C2923.cpp  
template <class T> struct TC {};  
int x;  
int main() {  
   TC<x>* tc2;   // C2923  
   TC<int>* tc2;   // OK  
}  
```  
  
 使用泛型时，也可能会发生 C2923：  
  
```  
// C2923b.cpp  
// compile with: /clr /c  
generic <class T> ref struct GC {};  
  
int x;  
  
int main() {  
   GC<x>^ gc2;   // C2923  
   GC<int>^ gc2;   // OK  
}  
```