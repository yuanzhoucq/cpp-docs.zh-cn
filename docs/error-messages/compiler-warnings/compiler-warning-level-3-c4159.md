---
title: 编译器警告 （等级 3） C4159 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4159
dev_langs:
- C++
helpviewer_keywords:
- C4159
ms.assetid: e2cf964e-f4b8-4b2c-9569-1abb94307232
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 139a21f5fbb7ce279d96f9df8be6008c2f092287
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291666"
---
# <a name="compiler-warning-level-3-c4159"></a>编译器警告 （等级 3） C4159
\#杂注 pragma(pop,...)： 具有弹出先前入栈的标识符 identifier  
  
 你的源代码包含**推送**带有杂注标识符与指令跟**pop**指令不含标识符。 因此，***标识符***的弹出，和后续用于***标识符***可能导致意外的行为。  
  
 若要避免此警告，请提供一个标识符**pop**指令。 例如：  
  
```  
// C4159.cpp  
// compile with: /W3  
#pragma pack(push, f)  
#pragma pack(pop)   // C4159  
  
// using the identifier resolves the warning  
// #pragma pack(pop, f)  
  
int main()  
{  
}  
```