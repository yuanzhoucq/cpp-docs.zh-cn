---
title: 错误 C1383 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1383
dev_langs:
- C++
helpviewer_keywords:
- C1383
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae5e16959597e16f25320778be4d4b45ca5950e0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1383"></a>错误 C1383
编译器选项 /GL 与安装的公共语言运行时版本不兼容  
  
 将以前版本的公共语言运行时与较新编译器结合使用时，以及使用 **/clr** 和 **/GL.** 进行编译时，会发生 C1383。  
  
 要进行解决，请勿将 **/GL** 与 **/clr** 结合使用，或是安装随你的编译器附带的公共语言运行时版本。  
  
 有关详细信息，请参阅 [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) 和 [/GL (Whole Program Optimization)](../../build/reference/gl-whole-program-optimization.md)。