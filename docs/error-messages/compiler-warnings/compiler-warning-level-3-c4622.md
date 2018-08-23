---
title: 编译器警告 （等级 3） C4622 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4622
dev_langs:
- C++
helpviewer_keywords:
- C4622
ms.assetid: d3c879f0-4492-4f4b-b26d-230993f3a933
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b82e87f37b50b8df727d043889cb35ca02d3f78
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291536"
---
# <a name="compiler-warning-level-3-c4622"></a>编译器警告（等级 3）C4622
覆盖创建对象文件的预编译头期间生成的调试信息：“file”  
  
 当使用 [/Yu](../../build/reference/yu-use-precompiled-header-file.md) （使用预编译头）选项编译时，指定文件中的 CodeView 信息丢失。  
  
 当创建或使用预编译头文件时（使用 [/Fo](../../build/reference/fo-object-file-name.md)）重命名对象文件，并使用新对象文件进行链接。