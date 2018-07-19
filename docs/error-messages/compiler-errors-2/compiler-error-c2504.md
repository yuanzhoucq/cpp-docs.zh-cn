---
title: 编译器错误 C2504 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2504
dev_langs:
- C++
helpviewer_keywords:
- C2504
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bac0f8f28955af172590535568289182c3489d6d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229506"
---
# <a name="compiler-error-c2504"></a>编译器错误 C2504
class： 未定义的基类  
  
 声明的基类，但是永远不会定义。  可能的原因：  
  
1.  缺少包含文件。  
  
2.  使用不声明外部的基类[extern](../../cpp/using-extern-to-specify-linkage.md)。  
  
 下面的示例生成 C2504:  
  
```  
// C2504.cpp  
// compile with: /c  
class A;  
class B : public A {};   // C2504  
```  
  
 还行  
  
```  
class C{};  
class D : public C {};  
```