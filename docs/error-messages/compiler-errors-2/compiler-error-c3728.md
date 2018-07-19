---
title: 编译器错误 C3728 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3728
dev_langs:
- C++
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bae204db616db9e7d7e04cfd62d53374b0793aa9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273219"
---
# <a name="compiler-error-c3728"></a>编译器错误 C3728
event： 事件不具有引发方法  
  
 使用一种语言，创建的元数据，如 C# 中，不允许在定义它在类外部从引发事件，不包括[#using](../../preprocessor/hash-using-directive-cpp.md)指令，而是使用尝试的 CLR 编程的 Visual c + + 程序引发事件。  
  
 若要引发事件如 C# 语言开发的程序中，包含事件的类需要还定义引发事件的公共方法。