---
title: "编译器警告 （等级 1 和 4） C4112 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4112
dev_langs:
- C++
helpviewer_keywords:
- C4112
ms.assetid: aff64897-bb79-4a67-9b6f-902c6d44f3dc
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 8a2c08b6c4bc8e1f2cf20e0236f76b5cd3020de4
ms.contentlocale: zh-cn
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-levels-1-and-4-c4112"></a>编译器警告（等级 1 和等级 4）C4112
\#行需要介于 1 到 number 之间的整数  
  
 [#Line](../../preprocessor/hash-line-directive-c-cpp.md)指令指定超出了允许的范围的整数参数。  
  
 若指定的参数小于 1，则行计数器将重置为 1。 如果指定的参数大于 *number*，即编译器定义的限制，则行计数器保持不变。 这是在 ANSI 兼容性级别 1 警告 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 和等级 4 警告具有 Microsoft 扩展 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))。  
  
 下面的示例生成 C4112：  
  
```  
// C4112.cpp  
// compile with: /W4  
#line 0   // C4112, value must be between 1 and number  
  
int main() {  
}  
```
