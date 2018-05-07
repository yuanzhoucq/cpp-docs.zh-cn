---
title: 错误 C1001 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1001
dev_langs:
- C++
helpviewer_keywords:
- C1001
ms.assetid: 5736cdb3-22c8-4fad-aa85-d5e0d2b232f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f605dd7e4892c4a8b57e544ed857257be72f020d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1001"></a>错误 C1001

> 内部编译器 ERROR(compiler file *file*, line *number*)  
  
编译器无法在分析中生成的构造，通常是由于特定表达式以及优化选项，或问题的组合的正确代码。 如果列出的编译器文件具有 utc 或 C2 路径段，则可能会优化出错。 如果文件具有 cxxfe 或 c1xx 路径段，或者是 msc1.cpp，它可能是分析器错误。 如果名为的文件，cl.exe 没有其他信息可用。  

通常可以通过删除一个或多个优化选项来修复优化问题。 若要确定哪个选项有故障，请移除一个选项一个时间并重新编译之前的错误消息将消失。 最常负责选项[/Og （全局优化）](../../build/reference/og-global-optimizations.md)和[/Oi （生成内部函数）](../../build/reference/oi-generate-intrinsic-functions.md)。 一旦你确定哪个优化选项负责，也可以禁用它通过使用出现错误的函数[优化](../../preprocessor/optimize.md)杂注，并继续使用该模块中的其余的选项。 有关优化选项的详细信息，请参阅[优化最佳做法](../../build/reference/optimization-best-practices.md)。

如果优化不负责该错误，请尝试重写其中报告错误，一行或几行的代码周围的行。 若要查看的代码的方法，编译器可以看到该预处理后，可以使用[/P （预处理到文件）](../../build/reference/p-preprocess-to-a-file.md)选项。

有关如何隔离错误根源以及如何向 Microsoft 报告内部编译器错误的详细信息，请参阅[如何报告使用 Visual c + + 工具集的问题](../../how-to-report-a-problem-with-the-visual-cpp-toolset.md)。