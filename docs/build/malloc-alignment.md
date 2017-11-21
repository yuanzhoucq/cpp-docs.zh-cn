---
title: "malloc 对齐 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a8d1d1b4-5122-456f-9a64-a50e105e55a5
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 66ec1e2e86996b8044909961bef9ab4ea3e76312
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="malloc-alignment"></a>malloc 对齐
[malloc](../c-runtime-library/reference/malloc.md)保证以返回有关存储具有基本的对齐方式，且任何对象分配的内存量无法适应适当对齐的内存。 A*基本对齐*是小于或等于而无需一种对齐规范实现支持的最大对齐方式的对齐方式。 (在 Visual c + +，这是所需的对齐方式`double`，或 8 个字节。 在针对 64 位平台的代码中，是 16 个字节。）例如，将支持任何四个字节或更小的对象的边界上对齐 4 字节分配。  
  
 Visual c + + 允许具有类型*扩展对齐*，它们也称为*过度对齐*类型。 例如，SSE 类型[__m128](../cpp/m128.md)和`__m256`，并通过使用声明的类型的`__declspec(align( n ))`其中`n`大于 8、 具有扩展对齐方式。 不保证适用于需要扩展的对齐方式的对象的边界上的内存对齐方式`malloc`。 若要为过度对齐类型分配内存，使用[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md)和相关函数。  
  
## <a name="see-also"></a>另请参阅  
 [堆栈使用](../build/stack-usage.md)   
 [对齐](../cpp/align-cpp.md)   
 [__declspec](../cpp/declspec.md)