---
title: 编译器警告 （等级 1） C4142 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4142
dev_langs:
- C++
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c87b7689cf11ab28c1a6377ff85e1594fd1b5fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284428"
---
# <a name="compiler-warning-level-1-c4142"></a>编译器警告 （等级 1） C4142
良性重定义的类型  
  
 一种类型中不起作用对已生成代码的方式重新定义。  
  
 通过检查以下可能的原因进行修复：  
  
-   派生类的成员函数具有不同的返回类型从相应的成员函数的基类。  
  
-   与定义的类型`typedef`命令重新定义使用不同的语法。  
  
 下面的示例生成 C4142:  
  
```  
// C4142.c  
// compile with: /W1  
float X2;  
X2 = 2.0 + 1.0;   // C4142  
  
int main() {  
   float X2;  
   X2 = 2.0 + 1.0;   // OK  
}  
```