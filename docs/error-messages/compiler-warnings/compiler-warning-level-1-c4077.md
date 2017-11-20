---
title: "编译器警告 （等级 1） C4077 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4077
dev_langs: C++
helpviewer_keywords: C4077
ms.assetid: c2d28805-b33f-41ad-afba-33b3f788c649
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4d177d9d9bc5ce24e31b918b5651f2db1208b2c1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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