---
title: "内部和内联程序集 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 8affd4bb-279d-46f3-851f-8be0a9c5ed3f
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 80eb16eb7fde49c499227bb3d60000e2ac6e5143
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="intrinsics-and-inline-assembly"></a>内部和内联程序集
约束之一[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]编译器是没有内联汇编程序支持。 这意味着，函数无法写入在 C 或 c + + 中将已作为子例程或内部函数编译器支持写入。 某些函数是敏感的性能，而有些则不是。 性能敏感的函数应作为内部函数实现。  
  
 编译器支持的内部函数中所述[编译器内部函数](../intrinsics/compiler-intrinsics.md)。  
  
## <a name="see-also"></a>请参阅  
 [x64 软件约定](../build/x64-software-conventions.md)