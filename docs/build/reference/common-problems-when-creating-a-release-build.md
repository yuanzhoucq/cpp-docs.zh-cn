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
- troubleshooting Visual C++
- troubleshooting release builds
- memory [C++], overwrites
ms.assetid: 73cbc1f9-3e33-472d-9880-39a8e9977b95
ms.openlocfilehash: bb5098ab4c92a408ae5895b5c59c7ecd36585bdb
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415651"
---
# <a name="common-problems-when-creating-a-release-build"></a>创建发行版本时遇到的常见问题

在开发期间，将通常生成和测试你的项目的调试版本。 如果您然后构建应用程序的发布版本，可能会收到访问冲突。

以下列表显示调试和发布 （非调试） 生成之间的主要差异。 其他差异，但以下是它适用于调试版本时，会导致失败的应用程序在发布版本中的主要区别。

- [堆布局](#_core_heap_layout)

- [编译](#_core_compilation)

- [指针的支持](#_core_pointer_support)

- [优化](#_core_optimizations)

请参阅[/GZ （调试版本中捕捉版本生成错误）](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md)如何捕获版本信息的编译器选项生成调试版本中的错误。

##  <a name="_core_heap_layout"></a> 堆布局

堆布局将大约 90%的明显的问题的原因，当应用程序中调试，但不是发布的工作。

生成用于调试的项目时，将调试内存分配器。 这意味着所有内存分配都有其周围放置保护字节。 这些保护字节检测内存改写。 因为堆布局不同之间发行版和调试版本中，内存改写可能会在调试版本，不创建任何问题，但在发行版本中可能导致灾难性的后果。

有关详细信息，请参阅[检查内存改写](../../build/reference/checking-for-memory-overwrites.md)并[用于调试版本来检查内存改写](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)。

##  <a name="_core_compilation"></a> 编译

许多 MFC 宏和很多时生成发布版本的 MFC 实现更改。 具体而言，ASSERT 宏计算结果为 nothing 在发行版本中，因此将执行任何 assert 语句中的代码。 有关详细信息，请参阅[检查断言语句](../../build/reference/using-verify-instead-of-assert.md)。

一些函数是内联以在发布版本中提高速度。 优化通常是在发布版本中打开的。 此外使用不同的内存分配器。

##  <a name="_core_pointer_support"></a> 指针的支持

缺少调试信息从你的应用程序中删除填充。 在发布版本中，杂散指针具有更好的指向未初始化的内存，而不是指向要调试的信息。

##  <a name="_core_optimizations"></a> 优化

根据某些代码段的性质，优化编译器可能生成意外的代码。 这是最不可能的原因的发行版本问题，但有时确实会发生。 一种解决方案，请参阅[优化您的代码](../../build/reference/optimizing-your-code.md)。

## <a name="see-also"></a>请参阅

[发行版本](../../build/reference/release-builds.md)<br/>
[修复发行版本问题](../../build/reference/fixing-release-build-problems.md)
