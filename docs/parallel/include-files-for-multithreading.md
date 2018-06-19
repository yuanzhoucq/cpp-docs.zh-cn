---
title: 包含文件中的多线程处理 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- threading [C++], include files
- include files, multithreading
- multithreading [C++], include files
ms.assetid: 98d764f9-71f4-4da5-8f3a-8d2d26e96799
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 62b94f4a7a394b78cb7c6f23275709e4aeacc774
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33685796"
---
# <a name="include-files-for-multithreading"></a>多线程编程的包含文件
标准包含文件实现在库中的声明 C 运行时库函数。 如果你使用[完全优化](../build/reference/ox-full-optimization.md)(/ Ox) 或[fastcall 调用约定](../build/reference/gd-gr-gv-gz-calling-convention.md)(/ Gr) 选项，则编译器将认为应该使用的寄存器调用约定来调用所有函数。 使用 C 调用约定，编译运行时库函数和标准包含文件中的声明告知编译器生成正确的外部引用，对这些函数。  
  
## <a name="see-also"></a>请参阅  
 [使用 C 和 Win32 进行多线程编程](../parallel/multithreading-with-c-and-win32.md)