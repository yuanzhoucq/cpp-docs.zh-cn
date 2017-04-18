---
title: "编译器错误 C3554 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3554
dev_langs:
- C++
helpviewer_keywords:
- C3554
ms.assetid: aede18d5-fefc-4da9-9b69-adfe90bfa742
caps.latest.revision: 4
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
ms.openlocfilehash: 29fdf7dacbc24f136d24b283c787d40891969678
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3554"></a>编译器错误 C3554
“decltype”不能与任何其他类型说明符组合  
  
 不可用任何类型说明符来限定 `decltype()` 关键字。 例如，下述代码片段产生错误 C3554。  
  
```  
int x;  
unsigned decltype(x); // C3554  
```
