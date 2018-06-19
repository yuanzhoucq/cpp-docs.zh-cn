---
title: 编译器错误 C2756 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2756
dev_langs:
- C++
helpviewer_keywords:
- C2756
ms.assetid: 42eb988d-4043-4dee-8fd4-596949f69a55
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3eb61cd111166867be0439709a8b73dd4056099
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33231772"
---
# <a name="compiler-error-c2756"></a>编译器错误 C2756
“模板类型”: 部分专用化中不允许有默认模板自变量  
  
 部分专用化的模板不能包含默认自变量。  
  
 下面的示例生成 C2756，并演示如何修复此错误：  
  
```  
// C2756.cpp  
template <class T>  
struct S {};  
  
template <class T=int>  
// try the following line instead  
// template <class T>  
struct S<T*> {};   // C2756  
```