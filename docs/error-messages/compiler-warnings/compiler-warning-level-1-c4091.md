---
title: 编译器警告 （等级 1） C4091 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4091
dev_langs:
- C++
helpviewer_keywords:
- C4091
ms.assetid: 3a404967-ab42-49b0-b324-fd7ba1859d78
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 79a0a74ad2cf6471679fd776f296d465ee8dd29c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276511"
---
# <a name="compiler-warning-level-1-c4091"></a>编译器警告 （等级 1） C4091
keyword： 未不声明任何变量时忽略左侧的 type  
  
 编译器检测到的情况： 用户可能想要声明的变量，但编译器无法将该变量声明。  
  
## <a name="example"></a>示例  
 A`__declspec`开头的用户定义的类型声明的特性应用于该类型的变量。 C4091 指示未声明任何变量。 下面的示例生成 C4091。  
  
```  
// C4091.cpp  
// compile with: /W1 /c  
__declspec(dllimport) class X {}; // C4091  
  
// __declspec attribute applies to varX  
__declspec(dllimport) class X2 {} varX;  
  
// __declspec attribute after the class or struct keyword   
// applies to user defined type  
class __declspec(dllimport) X3 {};  
```  
  
## <a name="example"></a>示例  
 如果标识符是的 typedef，它还不能为变量的名称。 下面的示例生成 C4091。  
  
```  
// C4091_b.cpp  
// compile with: /c /W1 /WX  
#define LIST 4  
typedef struct _LIST {} LIST;   // C4091  
```