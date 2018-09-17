---
title: malloc 对齐 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a8d1d1b4-5122-456f-9a64-a50e105e55a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa6e2748691eeb8a11834bcf8e6962252be7ab3f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712057"
---
# <a name="malloc-alignment"></a>malloc 对齐

[malloc](../c-runtime-library/reference/malloc.md)保证返回的存储具有基础对齐方式，且任何对象分配的内存量无法容纳，适当对齐的内存。 一个*基本对齐*是小于或等于而无需对齐方式规范实现支持的最大对齐对齐方式。 (在 Visual c + +，这是所需的对齐方式`double`，或 8 个字节。 在针对 64 位平台的代码中，是 16 个字节。）例如，将支持四个字节或更小的任何对象的边界上对齐 4 字节分配。

Visual c + + 允许具有*扩展对齐方式*，也称为*过对齐*类型。 例如，SSE 类型[__m128](../cpp/m128.md)并`__m256`，并通过使用声明的类型`__declspec(align( n ))`其中`n`大于 8、 具有扩展对齐方式。 不保证适用于需要扩展对齐方式的对象的边界上的内存对齐`malloc`。 若要为过对齐类型分配内存，请使用[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md)和相关函数。

## <a name="see-also"></a>请参阅

[堆栈使用](../build/stack-usage.md)<br/>
[align](../cpp/align-cpp.md)<br/>
[__declspec](../cpp/declspec.md)