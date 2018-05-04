---
title: 创建。Sbr 文件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- SBR files
- BSCMAKE, input files
- .sbr files
- source browser files
- local symbols in browse information
- symbols
ms.assetid: bdb4b93c-a88a-441a-84fd-01087d03be25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdada1f4d07d02988da388e39e332c832f633adb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="creating-an-sbr-file"></a>创建 .Sbr 文件
BSCMAKE 的输入的文件是.sbr 文件。 编译器创建.sbr 文件以供每个对象文件 (.obj) 对其进行编译。 当生成或更新你的浏览信息文件时，所有的.sbr 文件为你的项目必须在磁盘上可使用。  
  
 若要创建的.sbr 文件与所有可能的信息，请指定[/FR](../../build/reference/fr-fr-create-dot-sbr-file.md)。  
  
 若要创建不包含本地符号的.sbr 文件，指定[/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md)。 如果.sbr 文件包含本地符号，则可以仍省略它们从.bsc 文件使用 BSCMAKE 的[/El 选项](../../build/reference/bscmake-options.md)`.`  
  
 你可以执行完全编译的情况下创建的.sbr 文件。 例如，可以指定到编译器来执行语法检查和仍生成的.sbr 文件，如果你指定 /FR 或 /Fr./Zs 选项  
  
 生成过程可能更有效，如果第一次压缩.sbr 文件以移除未引用的定义。 编译器自动包.sbr 文件。  
  
## <a name="see-also"></a>请参阅  
 [生成 .Bsc 文件](../../build/reference/building-a-dot-bsc-file.md)