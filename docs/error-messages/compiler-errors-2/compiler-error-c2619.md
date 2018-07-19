---
title: 编译器错误 C2619 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2619
dev_langs:
- C++
helpviewer_keywords:
- C2619
ms.assetid: c826f8ab-d66a-4b79-a0b2-93b0af8c41ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 05f02026dac06647a8fda1eeb7e67cc3eaa586b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33231313"
---
# <a name="compiler-error-c2619"></a>编译器错误 C2619
“标识符”：匿名结构或联合中不允许使用静态数据成员  
  
 匿名结构或联合的成员声明为 `static`。  
  
 下面的示例生成 C2619，并演示如何通过删除 static 关键字修复此错误。  
  
```  
// C2619.cpp  
int main() {  
   union { static int j; };  // C2619  
   union { int j; };  // OK  
}  
```