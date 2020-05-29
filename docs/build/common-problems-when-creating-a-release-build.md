---
title: 创建发行版本时遇到的常见问题
ms.date: 11/04/2016
helpviewer_keywords:
- unexpected code generation
- debugging [MFC], release builds
- release builds, troubleshooting
- stray pointers
- debug builds, difference from release builds
- MFC [C++], release builds
- heap layout problems
- pointers, stray
- release builds, building applications
- debug memory allocator
- optimization [C++], compiler
- projects [C++], debug configuration
- troubleshooting release builds
- memory [C++], overwrites
ms.assetid: 73cbc1f9-3e33-472d-9880-39a8e9977b95
ms.openlocfilehash: 9bd1cafe40417872d42f2e9e1427e5f2eccad7a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328865"
---
# <a name="common-problems-when-creating-a-release-build"></a>创建发行版本时遇到的常见问题

在开发过程中，通常使用项目的调试版本来生成和测试。 如果随后为发布版本生成应用程序，则可能会遇到访问冲突。

下面的列表显示了调试和发布（非调试）版本之间的主要区别。 还有其他差异，但以下是导致应用程序在调试版本中可运行但在发布版本中不运行的主要区别。

- [堆布局](#_core_heap_layout)

- [编译](#_core_compilation)

- [指针支持](#_core_pointer_support)

- [优化](#_core_optimizations)

有关如何捕获调试版本中的发布版本错误的信息，请参阅 [/GZ（捕获调试版本中的发布版本错误）](reference/gz-enable-stack-frame-run-time-error-checking.md)编译器选项。

## <a name="heap-layout"></a><a name="_core_heap_layout"></a> 堆布局

关于导致应用程序在调试版本中可运行，但在发布版本中不运行的问题，约有百分之九十都是由堆布局引起的。

生成用于调试的项目时，使用的是调试内存分配器。 这意味着所有内存分配的周围都有保护字节。 这些保护字节检测内存覆盖。 由于堆布局在发布版本和调试版本之间不同，因此内存覆盖在调试版本中可能不会引起任何问题，但在发布版本中可能导致灾难性的后果。

有关详细信息，请参阅[查看内存覆盖](checking-for-memory-overwrites.md)和[使用调试版本检查内存覆盖](using-the-debug-build-to-check-for-memory-overwrite.md)。

## <a name="compilation"></a><a name="_core_compilation"></a> 编译

许多 MFC 宏和大部分 MFC 实现在生成以用于发布时都会发生更改。 特别是，ASSERT 宏在发布版本中不计算任何内容，因此不会执行 ASSERT 中找到的任何代码。 有关详细信息，请参阅[检查 ASSERT 语句](using-verify-instead-of-assert.md)。

为提高运行速度，发布版本中内联了某些函数。 发行版本中通常会启用优化。 还会使用不同的内存分配器。

## <a name="pointer-support"></a><a name="_core_pointer_support"></a> 指针支持

缺少调试信息会从应用程序中删除填充。 在发布版本中，迷途指针更有可能指向未初始化的内存，而不是指向调试信息。

## <a name="optimizations"></a><a name="_core_optimizations"></a> 优化

根据代码片段的特性，优化编译器可能会生成意外代码。 这导致发布版本问题的可能性最低，但有时确实会发生。 有关解决方案，请参阅[优化代码](optimizing-your-code.md)。

## <a name="see-also"></a>请参阅

[发行版本](release-builds.md)<br/>
[修复发行版本问题](fixing-release-build-problems.md)
