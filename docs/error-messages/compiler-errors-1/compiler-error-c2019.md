---
title: 编译器错误 C2019 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2019
dev_langs:
- C++
helpviewer_keywords:
- C2019
ms.assetid: 4f37b1e1-9eca-418f-a4c3-141e8512d7b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8f9f36bef278edc4c40c732b86c012180535f74
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164235"
---
# <a name="compiler-error-c2019"></a>编译器错误 C2019
应为预处理器指令，却找到“character”  
  
 字符跟`#`登录，但这不是预处理器指令的第一个字母。  
  
 下面的示例生成 C2019:  
  
```  
// C2019.cpp  
#!define TRUE 1   // C2019  
```  
  
 可能的解决方法：  
  
```  
// C2019b.cpp  
// compile with: /c  
#define TRUE 1  
```