---
title: 指定内联文件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, inline files
- inline files [C++], specifying NMAKE
- files [C++], inline
ms.assetid: 393eccfb-3fc9-4bac-a30c-8ac8d221cca3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2c0d85436aef5ed48c0a8787f8bce330bf6d3e96
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380100"
---
# <a name="specifying-an-inline-file"></a>指定内联文件
指定两个命令的尖括号 (<<) 在命令中其中*filename*要显示。 尖括号不能为宏扩展。  
  
## <a name="syntax"></a>语法  
  
```  
<<[filename]  
```  
  
## <a name="remarks"></a>备注  
 当运行该命令时，用替换尖括号*filename*，如果指定，或通过 NMAKE 生成的唯一名称。 如果指定， *filename*必须遵循而无需空格或制表符的尖括号。允许的路径。 需要或采用无扩展名。 如果*filename*文件创建在当前的指定或指定的目录，该名称覆盖任何现有文件; 否则，在临时目录中创建 (或当前目录中，如果在 TMP 环境变量未定义）。 如果先前*filename*是重复使用，NMAKE 替换以前的文件。  
  
## <a name="see-also"></a>请参阅  
 [生成文件中的内联文件](../build/inline-files-in-a-makefile.md)