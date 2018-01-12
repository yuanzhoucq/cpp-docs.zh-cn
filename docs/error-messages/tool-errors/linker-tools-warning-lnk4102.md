---
title: "链接器工具警告 LNK4102 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4102
dev_langs: C++
helpviewer_keywords: LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 80efad60da9f6742110811a5cf4c12f07c7def67
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4102"></a>链接器工具警告 LNK4102
导出删除的析构函数 name;图像可能无法正确运行  
  
 程序已尝试导出删除析构函数。 产生的删除可能会跨 DLL 边界，以便进程可以释放不拥有的内存。 请确保在.def 文件中，未列出给定的符号和符号未列出作为自变量的**/导入**或**/导出**链接器命令行中的选项。  
  
 如果你正在重新生成的 C 运行时库，你可以忽略此消息。