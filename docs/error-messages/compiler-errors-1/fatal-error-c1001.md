---
title: 错误 C1001
ms.date: 11/04/2016
f1_keywords:
- C1001
helpviewer_keywords:
- C1001
ms.assetid: 5736cdb3-22c8-4fad-aa85-d5e0d2b232f4
ms.openlocfilehash: e1255578883c8d2bc278184a02575a0a51ed9b6c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204953"
---
# <a name="fatal-error-c1001"></a>错误 C1001

> 内部编译器错误（编译器文件*文件*、行*号*）

编译器无法为构造生成正确的代码（通常是由于特定表达式和优化选项的组合），也不是分析时遇到的问题。 如果列出的编译器文件具有 utc 或 C2 路径段，则可能是优化错误。 如果文件具有 cxxfe 或 c1xx 路径段，或为 msc1，则可能是分析器错误。 如果名为 cl .exe 文件，则没有其他可用的信息。

通常可以通过删除一个或多个优化选项来解决优化问题。 若要确定哪个选项是错误的，请一次删除一个选项并重新编译，直到错误消息消失。 最常见的选项是[/og （全局优化）](../../build/reference/og-global-optimizations.md)和[/Oi （生成内部函数）](../../build/reference/oi-generate-intrinsic-functions.md)。 确定要负责的优化选项后，可以通过使用[optimize](../../preprocessor/optimize.md)杂注在出现错误的函数周围禁用该选项，并继续将选项用于模块的其余部分。 有关优化选项的详细信息，请参阅[优化最佳实践](../../build/optimization-best-practices.md)。

如果优化不负责错误，请尝试重新编写报告错误的行或围绕该行的几行代码。 若要查看编译器在预处理后看到的代码，可以使用[/p （预处理到文件）](../../build/reference/p-preprocess-to-a-file.md)选项。

有关如何隔离错误源以及如何向 Microsoft 报告内部编译器错误的详细信息，请参阅[如何使用视觉C++工具集报告问题](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md)。
