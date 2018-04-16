---
title: "错误 C1076 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1076
dev_langs:
- C++
helpviewer_keywords:
- C1076
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 617db809cfaeb4d0e0003a3dfc2e9568726b0c58
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1076"></a>错误 C1076
编译器限制 : 达到内部堆限制；使用 /Zm 指定更高的限制  
  
 此错误可能是由过多符号或过多模板实例化引起的。  
  
 解决此问题的方法是：  
  
1.  使用[/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)选项将编译器内存限制设置中指定的值为[C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md)错误消息。 有关详细信息，包括如何在中设置此值[!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]，请参阅备注部分中的[/Zm （指定预编译头内存分配限制）](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)。  
  
2.  如果正在 64 位操作系统中使用 32 位托管编译器，请改用 64 位托管编译器。 有关详细信息，请参阅[如何： 启用 64 位 Visual c + + 工具集在命令行上的](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)。  
  
3.  消除不需要的包含文件。  
  
4.  消除不需要的全局变量，例如，动态分配内存而不是声明一个大数组。  
  
5.  消除未使用的声明。  
  
6.  将大函数拆分为更小的函数。  
  
7.  将大类拆分为更小的类。  
  
8.  将当前文件拆分成更小的文件。  
  
 如果指定的值在生成开始后，立即，则会发生 C1076 **/Zm**而言可能太高为您的程序。 减少**/Zm**值。