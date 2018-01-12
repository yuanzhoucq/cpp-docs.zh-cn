---
title: "编译器错误 C2109 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2109
dev_langs: C++
helpviewer_keywords: C2109
ms.assetid: 2d1ac79d-a985-4904-a38b-b270578d664d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7e9d0ba989b2befaa473107e109335816a2b61d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2109"></a>编译器错误 C2109
下标需要数组或指针类型  
  
 该下标用了不是数组的变量上。  
  
 下面的示例生成 C2109:  
  
```  
// C2109.cpp  
int main() {  
   int a, b[10] = {0};  
   a[0] = 1;   // C2109  
   b[0] = 1;   // OK  
}  
```