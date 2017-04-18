---
title: "编译器警告 （等级 1） C4068 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4068
dev_langs:
- C++
helpviewer_keywords:
- C4068
ms.assetid: 96a7397a-4eab-44ab-b3bb-36747503f7e5
caps.latest.revision: 7
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
ms.openlocfilehash: 6583ed19889de77ee6edd784662cad9bf60f9643
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4068"></a>编译器警告（等级 1）C4068
未知的杂注  
  
 编译器忽略了无法识别[杂注](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)。 请确保所使用的的编译器允许使用该 **杂注** 。 下面的示例生成 C4068：  
  
```  
// C4068.cpp  
// compile with: /W1  
#pragma NotAValidPragmaName   // C4068, use valid name to resolve  
int main()  
{  
}  
```
