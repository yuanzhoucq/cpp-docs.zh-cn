---
title: "编译器错误 C3638 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3638
dev_langs:
- C++
helpviewer_keywords:
- C3638
ms.assetid: 8d8bc5ca-75aa-480e-b6b6-3178fab51b1d
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 51048bb46dde49f432699e620b94d62fb8f6c131
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

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
