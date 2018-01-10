---
title: "编译器错误 C3354 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3354
dev_langs: C++
helpviewer_keywords: C3354
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bd5552afb4981a3ff5303f0f992dbea78cb3a36e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3354"></a>编译器错误 C3354
“%$I”：该函数用于创建不能有返回类型“type”的委托  
  
 以下类型作为 `delegate`的返回类型无效：  
  
-   指向函数的指针  
  
-   指向成员的指针  
  
-   指向成员函数的指针  
  
-   对函数的引用  
  
-   对成员函数的引用  
  
 以下示例生成 C3354：  
  
```  
// C3354_2.cpp  
// compile with: /clr /c  
using namespace System;  
typedef void ( *VoidPfn )();  
  
delegate VoidPfn func(); // C3354  
// try the following line instead  
// delegate  void func();  
```  
