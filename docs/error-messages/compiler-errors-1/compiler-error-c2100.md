---
title: "编译器错误 C2100 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2100
dev_langs:
- C++
helpviewer_keywords:
- C2100
ms.assetid: 9ed5ea11-9d55-4ddf-8b1a-162c74f3c390
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 799dba08ffb14126a26234b85c7ac4dd60b63633
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2100"></a>编译器错误 C2100
非法的间接寻址  
  
 间接寻址运算符 ( `*` ) 应用于非指针值。  
  
 下面的示例生成 C2100:  
  
```  
// C2100.cpp  
int main() {  
   int r = 0, *s = 0;  
   s = &r;  
   *r = 200;   // C2100  
   *s = 200;   // OK  
}  
```
