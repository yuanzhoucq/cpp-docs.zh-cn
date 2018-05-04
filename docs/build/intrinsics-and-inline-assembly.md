---
title: 内部和内联程序集 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8affd4bb-279d-46f3-851f-8be0a9c5ed3f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b8651bea0b1ee9f54ec0af704d92feef0722368
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="intrinsics-and-inline-assembly"></a>内部和内联程序集
约束之一[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]编译器是没有内联汇编程序支持。 这意味着，函数无法写入在 C 或 c + + 中将已作为子例程或内部函数编译器支持写入。 某些函数是敏感的性能，而有些则不是。 性能敏感的函数应作为内部函数实现。  
  
 编译器支持的内部函数中所述[编译器内部函数](../intrinsics/compiler-intrinsics.md)。  
  
## <a name="see-also"></a>请参阅  
 [x64 软件约定](../build/x64-software-conventions.md)