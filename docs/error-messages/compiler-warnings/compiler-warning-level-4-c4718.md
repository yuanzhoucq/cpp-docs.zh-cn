---
title: 编译器警告 （等级 4） C4718 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4718
dev_langs:
- C++
helpviewer_keywords:
- C4718
ms.assetid: 29507f8a-b024-42c1-a3b8-f35d1f2641f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a92ab7a32babd181f282c799568e3a9dea436c49
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294029"
---
# <a name="compiler-warning-level-4-c4718"></a>编译器警告（等级 4）C4718
“function call”：递归调用无副作用，正在删除  
  
 函数包含递归调用，但却没有副作用。 正在删除对此函数的调用。 不影响程序的正确性，而是影响其行为。 但保留该调用会导致运行时堆栈溢出异常，请删除该调用，从而排除这种可能性。