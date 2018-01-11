---
title: "编译器错误 C2781 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2781
dev_langs: C++
helpviewer_keywords: C2781
ms.assetid: f29b9963-f55b-427c-8db6-50f37713df5a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8c9e86968cc53e5a3db8411b5557460511ac4a3b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2781"></a>编译器错误 C2781
declaration： 需要至少 value1 参数-value2 提供  
  
 具有变量参数列表的函数模板具有参数太少。  
  
 下面的示例生成 C2781:  
  
```  
// C2781.cpp  
template<typename T>  
void f(T, T, ...){}  
  
int main() {  
   f(1);   // C2781  
  
   // try the following line instead  
   f(1,1);  
}  
```