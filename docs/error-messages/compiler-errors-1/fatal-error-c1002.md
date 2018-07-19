---
title: 错误 C1002 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1002
dev_langs:
- C++
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c63a8d399b3e8c781694d89825e7898fd1db4639
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225046"
---
# <a name="fatal-error-c1002"></a>错误 C1002
在第 2 遍中编译器的堆空间不足  
  
 在第二个阶段，可能由于具有过多符号或复杂表达式的程序发生过程，编译器用尽了动态内存空间。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复  
  
1.  将源文件划分为若干较小的文件。  
  
2.  将表达式分解为较小的子表达式。  
  
3.  删除其他程序或驱动程序占用的内存。