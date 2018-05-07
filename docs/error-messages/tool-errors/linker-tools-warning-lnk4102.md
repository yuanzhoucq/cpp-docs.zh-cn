---
title: 链接器工具警告 LNK4102 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4102
dev_langs:
- C++
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16d13dcbc6d15efd7cf3a7ea0a310de4ab7b0c93
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4102"></a>链接器工具警告 LNK4102
导出删除的析构函数 name;图像可能无法正确运行  
  
 程序已尝试导出删除析构函数。 产生的删除可能会跨 DLL 边界，以便进程可以释放不拥有的内存。 请确保在.def 文件中，未列出给定的符号和符号未列出作为自变量的 **/导入**或 **/导出**链接器命令行中的选项。  
  
 如果你正在重新生成的 C 运行时库，你可以忽略此消息。