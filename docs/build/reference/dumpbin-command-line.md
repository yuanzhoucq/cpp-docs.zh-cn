---
title: DUMPBIN 命令行 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- dumpbin
dev_langs:
- C++
helpviewer_keywords:
- DUMPBIN program, command line
ms.assetid: e6ad17d3-965d-41aa-9dfd-75bb073718d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc807a8f67ddaae894a0e0cba55475b804a0abce
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
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