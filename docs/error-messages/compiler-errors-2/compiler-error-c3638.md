---
title: 编译器错误 C3638 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3638
dev_langs:
- C++
helpviewer_keywords:
- C3638
ms.assetid: 8d8bc5ca-75aa-480e-b6b6-3178fab51b1d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3edb1a05323187b4a5dfcc2356da4a1ff8b874de
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267085"
---
# <a name="compiler-error-c3638"></a>编译器错误 C3638
operator： 不能重新定义的标准装箱和取消装箱转换运算符  
  
 编译器定义的转换运算符为每个托管类以支持隐式装箱。 此运算符不能重新定义。  
  
 有关详细信息，请参阅[隐式装箱](../../windows/boxing-cpp-component-extensions.md)。  
  
 下面的示例生成 C3638:  
  
```  
// C3638.cpp  
// compile with: /clr  
value struct V {  
   V(){}  
   static operator V^(V);   // C3638  
};  
  
int main() {  
   V myV;  
   V ^ pmyV = myV;   // operator supports implicit boxing  
}  
```