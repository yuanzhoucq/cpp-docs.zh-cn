---
title: "编译器警告 （等级 1） C4124 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4124
dev_langs:
- C++
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 38588fb242b5b4167984e15d101594d1b015ec86
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4124"></a>编译器警告 （等级 1） C4124
与堆栈检查 __fastcall 做效率很低  
  
 `__fastcall`关键字与堆栈检查启用一起使用。  
  
 `__fastcall`约定生成更快的代码，但堆栈检查会导致代码较慢。 使用时`__fastcall`，关闭堆栈检查与**check_stack**杂注或 /Gs。  
  
 仅为第一个函数声明在这些情况下发出此警告。