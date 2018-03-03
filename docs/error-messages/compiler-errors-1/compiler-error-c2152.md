---
title: "编译器错误 C2152 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2152
dev_langs:
- C++
helpviewer_keywords:
- C2152
ms.assetid: a9ea2b0c-d55d-41c7-ba9f-dd75592ffc8a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 705c5b96ce904a3851c57300cf395f8667aac3d2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2152"></a>编译器错误 C2152
identifier： 指向具有不同的属性的函数的指针  
  
 使用一个调用约定函数指针 (`__cdecl`， `__stdcall`，或`__fastcall`) 分配给使用另一个调用约定函数指针。