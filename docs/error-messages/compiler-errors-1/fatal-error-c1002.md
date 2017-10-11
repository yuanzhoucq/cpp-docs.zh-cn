---
title: "错误 C1002 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1002
dev_langs:
- C++
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: cab0e1db2d84fb5ba84d773f28e70341faf10ac6
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1002"></a>错误 C1002
在第 2 遍中编译器的堆空间不足  
  
 在第二个阶段，可能由于具有过多符号或复杂表达式的程序发生过程，编译器用尽了动态内存空间。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复  
  
1.  将源文件划分为若干较小的文件。  
  
2.  将表达式分解为较小的子表达式。  
  
3.  删除其他程序或驱动程序占用的内存。
