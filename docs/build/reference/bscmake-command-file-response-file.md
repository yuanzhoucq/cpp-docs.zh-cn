---
title: BSCMAKE 命令文件 （响应文件） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BSCMAKE, response file
- BSCMAKE, command file
- response files, BSCMAKE
- command files, BSCMAKE
- response files
- command files
ms.assetid: abdffeea-35c7-4f2d-8c17-7d0d80bac314
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a879306078c52e0ad11d29f1786a2e55c2480d2f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369560"
---
# <a name="bscmake-command-file-response-file"></a>BSCMAKE 命令文件（响应文件）
你可以提供部分或全部命令文件中的命令行输入。 指定命令文件使用以下语法：  
  
```  
BSCMAKE @filename  
```  
  
 允许只能有一个命令文件。 你可以指定具有路径*filename*。 位于之前*filename*使用 at 符号 (@)。 BSCMAKE 假定不扩展。 你可以指定其他*sbrfiles*之后在命令行上*filename*。 命令文件是包含在命令行中的指定它的相同顺序 BSCMAKE 的输入的文本文件。 用一个或多个空格、 制表符或换行符分隔的命令行参数。  
  
 以下命令调用 BSCMAKE 使用命令文件：  
  
```  
BSCMAKE @prog1.txt  
```  
  
 下面是示例命令文件：  
  
```  
/n /v /o main.bsc /El  
/S (  
toolbox.h  
verdate.h c:\src\inc\screen.h  
)  
file1.sbr file2.sbr file3.sbr file4.sbr  
```  
  
## <a name="see-also"></a>请参阅  
 [BSCMAKE 参考](../../build/reference/bscmake-reference.md)