---
title: "编译器警告 （等级 1） C4144 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4144
dev_langs: C++
helpviewer_keywords: C4144
ms.assetid: a37b445d-dbc6-43b4-8d95-ffd0e4225464
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d34c260d04549bf6ab40863e262c79b53a2480ec
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4144"></a>编译器警告 （等级 1） C4144
expression： 关系表达式用作 switch 表达式  
  
 指定的关系表达式用作的控制表达式[切换](../../cpp/switch-statement-cpp.md)语句。 关联的 case 语句将提供布尔值。 下面的示例生成 C4144:  
  
```  
// C4144.cpp  
// compile with: /W1  
int main()  
{  
   int i = 0;  
   switch(!i) {   // C4144, remove the ! to resolve  
      case 1:  
         break;  
      default:  
         break;  
   }  
}  
```