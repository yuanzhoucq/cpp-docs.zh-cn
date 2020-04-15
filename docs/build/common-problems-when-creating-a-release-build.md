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
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328865"
---
# <a name="common-problems-when-creating-a-release-build"></a>创建发行版本时遇到的常见问题

在开发过程中，您通常会使用项目的调试生成生成和测试。 如果随后为发布生成构建应用程序，则可能会收到访问冲突。

下面的列表显示了调试和发布（非调试）生成之间的主要区别。 还有其他差异，但以下是导致应用程序在调试生成中工作时在发布版本中失败的主要区别。

- [堆布局](#_core_heap_layout)

- [编译](#_core_compilation)

- [指针支持](#_core_pointer_support)

- [优化](#_core_optimizations)

有关如何捕获调试生成中的发布生成错误的信息，请参阅[/GZ（调试生成中的捕获发布-生成错误）](reference/gz-enable-stack-frame-run-time-error-checking.md)编译器选项。

## <a name="heap-layout"></a><a name="_core_heap_layout"></a>堆布局

当应用程序在调试中工作时，堆布局将是大约 90% 的明显问题的原因，但不会释放。

生成项目进行调试时，将使用调试内存分配器。 这意味着所有内存分配都位于它们周围。 这些保护字节检测到内存覆盖。 由于堆布局在版本和调试版本之间不同，因此内存覆盖可能不会在调试生成中造成任何问题，但在发布版本中可能具有灾难性影响。

有关详细信息，请参阅[检查内存覆盖](checking-for-memory-overwrites.md)，并使用[调试生成检查内存覆盖](using-the-debug-build-to-check-for-memory-overwrite.md)。

## <a name="compilation"></a><a name="_core_compilation"></a>编译

许多 MFC 宏和大部分 MFC 实现在生成以进行发布时会发生变化。 特别是，ASSERT 宏在发布版本中不计算任何内容，因此不会执行 ASSERT 中找到的代码。 有关详细信息，请参阅检查[ASSERT 语句](using-verify-instead-of-assert.md)。

某些函数内联在版本版本中提高了速度。 优化通常在发布版本中打开。 还使用了不同的内存分配器。

## <a name="pointer-support"></a><a name="_core_pointer_support"></a>指针支持

缺少调试信息会从应用程序中删除填充。 在发布版本中，杂散指针更有可能指向未初始化的内存，而不是指向调试信息。

## <a name="optimizations"></a><a name="_core_optimizations"></a>优化

根据某些代码段的性质，优化编译器可能会生成意外代码。 这是发布生成问题最不可能的原因，但确实偶尔会出现。 有关解决方案，请参阅[优化代码](optimizing-your-code.md)。

## <a name="see-also"></a>另请参阅

[发行版本](release-builds.md)<br/>
[修复发行版本问题](fixing-release-build-problems.md)
