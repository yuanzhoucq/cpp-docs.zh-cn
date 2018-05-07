---
title: 编译器警告 （等级 1） C4558 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4558
dev_langs:
- C++
helpviewer_keywords:
- C4558
ms.assetid: 52bb0324-7bec-468c-b35b-13a08d38e578
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 852e3d3e8bb1c8186232cbed2636ac890b0cd057
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4558"></a>编译器警告（等级 1）C4558
操作数 value 的值超出了范围下限的上限  
  
 传递给程序集语言指令的值超出了范围的参数指定。 值将被截断。  
  
 下面的示例生成 C4558:  
  
```  
// C4558.cpp  
// compile with: /W1  
// processor: x86  
void asm_test() {  
   __asm pinsrw   mm1, eax, 8;   // C4558  
}  
  
int main() {  
}  
```