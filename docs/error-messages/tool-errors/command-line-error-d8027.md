---
title: 命令行错误 D8027 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8027
dev_langs:
- C++
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc93edb939001a1e1bed5d3f7a4113e8483e81dd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="command-line-error-d8027"></a>命令行错误 D8027
无法执行组件  
  
 编译器无法运行给定的编译器组件或链接器。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  内存不足，无法加载该组件。 当 NMAKE 调用的编译器，外部生成文件运行编译器。  
  
2.  当前操作系统无法运行该组件。 请确保路径点的可执行文件适合于你的操作系统。  
  
3.  该组件已损坏。 重新复制通过使用安装程序的分发磁盘中的组件。  
  
4.  未正确指定一个选项。 例如：  
  
    ```  
    cl /B1 file1.c  
    ```