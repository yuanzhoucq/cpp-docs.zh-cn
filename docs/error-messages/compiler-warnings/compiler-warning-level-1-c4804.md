---
title: 编译器警告 （等级 1） C4804 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4804
dev_langs:
- C++
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 677899230b2475c80f9bdd461a0c79740c4d3bec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33286976"
---
# <a name="compiler-warning-level-1-c4804"></a>编译器警告（等级 1）C4804
operation： 类型为 bool 操作中的不安全地使用  
  
 在使用时，此警告为`bool`变量或以意外方式的值。 例如，如果你使用运算符，例如负一元运算符生成 C4804 (**-**) 或补数运算符 (`~`)。 编译器计算的表达式。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4804:  
  
```  
// C4804.cpp  
// compile with: /W1  
  
int main()  
{  
   bool i = true;  
   if (-i)   // C4804, remove the '-' to resolve  
   {  
      i = false;  
   }  
}  
```