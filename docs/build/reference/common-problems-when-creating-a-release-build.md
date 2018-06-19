---
title: 创建发布版本时的常见问题 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8860783a2cf9fb88b28e24e0bc16eb16c0dd5d77
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373161"
---
# <a name="common-problems-when-creating-a-release-build"></a>创建发行版本时遇到的常见问题
在开发期间，你通常将生成，并使用你的项目的调试版本进行测试。 如果你然后生成你的应用程序的发布版本，则可能获得访问冲突。  
  
 下面的列表显示调试版本和版本 （非调试） 生成之间的主要差异。 其他差异，但以下是在调试版本一起使用时将导致在发布版本中的应用程序失败的主要差异。  
  
-   [堆布局](#_core_heap_layout)  
  
-   [编译](#_core_compilation)  
  
-   [指针支持](#_core_pointer_support)  
  
-   [优化](#_core_optimizations)  
  
 请参阅[/GZ （调试版本中捕捉版本生成错误）](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md)有关如何捕获版本的编译器选项生成调试版本中的错误。  
  
##  <a name="_core_heap_layout"></a> 堆布局  
 堆布局将大约 90%的明显的问题的原因，在调试，但不是发布应用程序运行时。  
  
 生成用于调试的项目时，您正在使用调试内存分配器。 这意味着所有内存分配都有保护字节放置在其周围。 这些保护字节检测内存改写。 因为堆布局不同之间发行版本和调试版本中，内存覆盖不可能会在调试版本，创建的任何问题，但可能会产生灾难性的效果在发布版本中。  
  
 有关详细信息，请参阅[检查内存覆盖](../../build/reference/checking-for-memory-overwrites.md)和[用于调试版本来检查内存改写](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)。  
  
##  <a name="_core_compilation"></a> 编译  
 许多 MFC 宏和很多 MFC 实现更改时生成发布版本。 具体而言，断言宏计算出任何结果中的发布版本中，以便将执行任何在 assert 语句中找到的代码。 有关详细信息，请参阅[检查断言语句](../../build/reference/using-verify-instead-of-assert.md)。  
  
 一些函数是内联以发布版本中提高速度。 优化通常是在发布版本中打开的。 也会使用不同的内存分配器。  
  
##  <a name="_core_pointer_support"></a> 指针支持  
 缺少调试信息从你的应用程序中移除填充。 在发布版本，杂散指针具有更好的指向未初始化的内存，而不是指向的调试信息。  
  
##  <a name="_core_optimizations"></a> 优化  
 根据某些代码段的性质，优化编译器可能生成意外的代码。 这是最可能的原因的发行版本问题，但有时确实会发生。 一种解决方案，请参阅[优化您的代码](../../build/reference/optimizing-your-code.md)。  
  
## <a name="see-also"></a>请参阅  
 [发行版本](../../build/reference/release-builds.md)   
 [修复发行版本问题](../../build/reference/fixing-release-build-problems.md)