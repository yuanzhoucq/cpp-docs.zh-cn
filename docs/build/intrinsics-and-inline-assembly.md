---
title: 内部和内联程序集 |Microsoft Docs
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
ms.openlocfilehash: ff2b99eedcdd81a96dc3091046a4f62ffe002509
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572530"
---
# <a name="intrinsics-and-inline-assembly"></a>内部和内联程序集
一个编译器不是内联汇编程序支持 x64 的约束。 函数，这意味着不能编写 C 或 c + + 将必须编写为子例程或编译器支持的内部函数。 某些功能是敏感的性能，而有些则不然。 性能敏感的函数应作为内部函数实现。  
  
 编译器支持的内部函数中所述[编译器内部函数](../intrinsics/compiler-intrinsics.md)。  
  
## <a name="see-also"></a>请参阅  
 [x64 软件约定](../build/x64-software-conventions.md)