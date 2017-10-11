---
title: "编译器错误 C3672 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3672
dev_langs:
- C++
helpviewer_keywords:
- C3672
ms.assetid: da971041-1766-467a-aecf-1d8655c6cb7a
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: f01237ca5ac90ea3def4a6d2733ef8dd700bf738
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3672"></a>编译器错误 C3672
伪析构函数表达式仅用作函数调用的一部分  
  
 未正确调用析构函数。  有关详细信息，请参阅[析构函数](../../cpp/destructors-cpp.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3672。  
  
```  
// C3672.cpp  
template<typename T>  
void f(T* pT) {  
   &pT->T::~T;   // C3672  
   pT->T::~T();   // OK  
};  
  
int main() {  
   int i;  
   f(&i);  
}  
```
