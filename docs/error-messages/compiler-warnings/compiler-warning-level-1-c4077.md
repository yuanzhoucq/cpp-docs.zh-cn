---
title: "编译器警告 （等级 1） C4077 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4077
dev_langs:
- C++
helpviewer_keywords:
- C4077
ms.assetid: c2d28805-b33f-41ad-afba-33b3f788c649
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
ms.openlocfilehash: 000301a51098faff00210f323f522e35280418b8
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4077"></a>编译器警告（等级 1）C4077
未知的 check_stack 选项  
  
 旧式 **check_stack** 杂注与未知的参数一起使用。 参数必须为 `+`、 `-`、 `(on)`、 `(off)`或为空。  
  
 编译器将忽略杂注，保持堆栈检查不变。  
  
## <a name="example"></a>示例  
  
```  
// C4077.cpp  
// compile with: /W1 /LD  
#pragma check_stack yes // C4077  
#pragma check_stack +    // Correct old form  
#pragma check_stack (on) // Correct new form  
```
