---
title: "编译器警告 （等级 1） C4167 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4167
dev_langs:
- C++
helpviewer_keywords:
- C4167
ms.assetid: 74a420bd-9371-4167-b1ee-74dd8680f97b
caps.latest.revision: 6
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
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 154b0b55bcdfe1b69fc84ca8e11808fa0343265c
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4167"></a>编译器警告（等级 1）C4167
函数：仅可用作内部函数  
  
 **#pragma 函数** 尝试强制编译器对必须以内部形式使用的函数使用常规调用。 将忽略杂注。  
  
 若要避免此警告，请删除 **#pragma 函数**。  
  
## <a name="example"></a>示例  
  
```  
// C4167.cpp  
// compile with: /W1  
#include <malloc.h>  
#pragma function(_alloca )   // C4167: _alloca() is intrinsic only  
int main(){}  
```
