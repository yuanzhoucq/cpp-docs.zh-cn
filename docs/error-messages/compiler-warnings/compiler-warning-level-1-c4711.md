---
title: 编译器警告 （等级 1） C4711 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4711
dev_langs:
- C++
helpviewer_keywords:
- C4711
ms.assetid: 270506ab-fead-4328-b714-2978113be238
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1faa8051ea2d167ae1386ef30ac54166c942aaf2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4711"></a>编译器警告（等级 1）C4711
为内联展开选定了函数“function”  
  
 编译器在上执行给定的函数，尽管它未标记为内联。  
  
 如果启用 C4711 [/Ob2](../../build/reference/ob-inline-function-expansion.md)指定。  
  
 在由编译器自行执行内联。 此警告为信息性。  
  
 默认情况下，此警告处于关闭状态。 若要启用警告，请使用[#pragma 警告](../../preprocessor/warning.md)。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。