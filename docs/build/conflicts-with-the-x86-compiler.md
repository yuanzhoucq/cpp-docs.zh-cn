---
title: "冲突与 x86 编译器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 8e47f0d3-afe0-42d9-9efa-de239ddd3a05
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2b2b9c4cf871e8436a8da34a862d205541e7dc5c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="conflicts-with-the-x86-compiler"></a>与 x86 编译器冲突
数据类型都大于 4 个字节不自动对齐在堆栈上时使用 x86 编译器进行编译应用程序。 因为编译器为 4 字节对齐的堆栈，任何大于 4 个字节，例如，64 位整数，不能自动对齐到 8 字节地址 x86 的体系结构。  
  
 处理未对齐的数据有两个含义。  
  
-   可能需要更长时间才能访问未对齐的位置不是所需对齐的位置。  
  
-   未对齐的位置不能在互锁操作。  
  
 如果需要更为严格的对齐，则使用`__declspec(align(N)) on your variable declarations`。 这将导致编译器动态对齐堆栈，以满足您的规范。 但是，在运行时动态调整堆栈，这种情况可能会导致你的应用程序的执行速度变慢。  
  
## <a name="see-also"></a>请参阅  
 [类型和存储](../build/types-and-storage.md)   
 [align](../cpp/align-cpp.md)