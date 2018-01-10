---
title: "BSCMAKE 命令行 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: BSCMAKE, command line
ms.assetid: 8006e8cf-8bfe-4c23-868a-b0a25e6bbf0f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c00a3842db37cc5027809f717ac47bd471dd073f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="bscmake-command-line"></a>BSCMAKE 命令行
若要运行 BSCMAKE，使用以下命令行语法：  
  
```  
BSCMAKE [options] sbrfiles  
```  
  
 选项仅出现在`options`字段在命令行上。  
  
 *Sbrfiles*字段指定一个或多个由编译器或汇编程序创建的.sbr 文件。 用空格或制表符分隔的.sbr 文件的名称。 必须指定扩展;没有默认值。 你可以指定路径的文件名，并可以使用操作系统通配符 (* 和？)。  
  
 在增量生成，你可以指定不是原始的生成的一部分的新.sbr 文件。 如果你希望所有发布内容保留在浏览信息文件，则必须指定所有.sbr 文件 （包括文件已截断） 最初用来创建.bsc 文件。 如果省略的.sbr 文件时，会删除该文件所占的浏览信息文件。  
  
 不要指定完全生成的截断的.sbr 文件。 完全生成需要来自所有指定的.sbr 文件的贡献。 在执行完全生成之前，重新编译该项目并创建新的.sbr 文件每个空文件。  
  
 以下命令运行 BSCMAKE 生成从三个.sbr 文件调用 MAIN.bsc 文件：  
  
```  
BSCMAKE main.sbr file1.sbr file2.sbr  
```  
  
 有关相关信息，请参阅[BSCMAKE 命令文件](../../build/reference/bscmake-command-file-response-file.md)和[BSCMAKE 选项](../../build/reference/bscmake-options.md)。  
  
## <a name="see-also"></a>请参阅  
 [BSCMAKE 参考](../../build/reference/bscmake-reference.md)