---
title: "编译器警告 （等级 1） C4010 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4010
dev_langs:
- C++
helpviewer_keywords:
- C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: b6a0c84d5138cf2ae8a7a6279d9dc0fde9fe9512
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-warning-level-1-c4010"></a>编译器警告 （等级 1） C4010
单行注释包含续行符  
  
 单行注释，由此引入 / /、 包含一个反斜杠 (\\) 用作作为行继续符。 编译器会考虑为延续的下一行，并会将其视为注释。  
  
 某些语法导向型编辑器并不表示为一个注释延续字符后面的行。 忽略语法突出显示的任何行的会导致此警告。  
  
 下面的示例生成 C4010:  
  
```  
// C4010.cpp  
// compile with: /WX  
int main() {  
   // the next line is also a comment because of the backslash \  
   int a = 3; // C4010  
   a++;  
}  
```
