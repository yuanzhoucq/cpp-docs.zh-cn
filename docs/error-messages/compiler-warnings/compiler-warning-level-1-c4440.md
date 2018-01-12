---
title: "编译器警告 （等级 1） C4440 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4440
dev_langs: C++
helpviewer_keywords: C4440
ms.assetid: 78b9642a-a93e-401e-9d92-372f6451bc5d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 418c49aa988c5cbf37b2307ca7f488dd9c4243d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4440"></a>编译器警告（等级 1）C4440
重新从 calling_convention1 到 calling_convention2 忽略的调用约定定义  
  
 已忽略尝试更改的调用约定。  
  
 下面的示例生成 C4440:  
  
```  
// C4440.cpp  
// compile with: /W1 /LD /clr  
typedef void __clrcall F();  
typedef F __cdecl *PFV;   // C4440  
```