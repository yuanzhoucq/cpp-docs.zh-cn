---
title: "包含文件中的多线程处理 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- threading [C++], include files
- include files, multithreading
- multithreading [C++], include files
ms.assetid: 98d764f9-71f4-4da5-8f3a-8d2d26e96799
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0f71b52bca5f636d80f2d55cc5e9ffc3e217d90a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="include-files-for-multithreading"></a>多线程编程的包含文件
标准包含文件实现在库中的声明 C 运行时库函数。 如果你使用[完全优化](../build/reference/ox-full-optimization.md)(/ Ox) 或[fastcall 调用约定](../build/reference/gd-gr-gv-gz-calling-convention.md)(/ Gr) 选项，则编译器将认为应该使用的寄存器调用约定来调用所有函数。 使用 C 调用约定，编译运行时库函数和标准包含文件中的声明告知编译器生成正确的外部引用，对这些函数。  
  
## <a name="see-also"></a>请参阅  
 [使用 C 和 Win32 进行多线程编程](../parallel/multithreading-with-c-and-win32.md)