---
title: "DUMPBIN 命令行 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- dumpbin
dev_langs:
- C++
helpviewer_keywords:
- DUMPBIN program, command line
ms.assetid: e6ad17d3-965d-41aa-9dfd-75bb073718d4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7cf71e413cbdd505f10e86994811ed7648af86e6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="dumpbin-command-line"></a>DUMPBIN 命令行
若要运行 DUMPBIN，使用以下语法：  
  
```  
DUMPBIN [options] files...  
```  
  
 指定一个或多个二进制文件，以及控制的信息所需的任何选项。 DUMPBIN 到标准输出中显示的信息。 你可以将它重定向到文件，或使用 /OUT 选项指定输出的文件名称。  
  
 如果不指定选项的文件上运行 DUMPBIN 时 DUMPBIN 显示 /SUMMARY 输出。  
  
 当你键入命令`dumpbin`DUMPBIN 而无需任何其他命令行输入时，显示一条总结了其选项的用法语句。  
  
## <a name="see-also"></a>请参阅  
 [C/c + + 生成工具](../../build/reference/c-cpp-build-tools.md)   
 [DUMPBIN 参考](../../build/reference/dumpbin-reference.md)