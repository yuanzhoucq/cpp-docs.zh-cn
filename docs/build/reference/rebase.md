---
title: -REBASE |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /rebase
dev_langs:
- C++
helpviewer_keywords:
- base addresses [C++]
- -REBASE editbin option
- REBASE editbin option
- DLLs [C++], linking
- executable files [C++], base address
- /REBASE editbin option [C++]
ms.assetid: 3f89d874-af5c-485b-974b-fd205f6e1a4b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4a5e2b68768b01d71532c358a14c53d8a033e1ed
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377084"
---
# <a name="rebase"></a>/REBASE
```  
/REBASE[:modifiers]  
```  
  
## <a name="remarks"></a>备注  
 此选项设置为指定的文件的基址。 EDITBIN 将分配新的基址，在连续的地址空间根据大小的最接近的 64 KB 向上舍入为每个文件中。 有关基址的详细信息，请参阅[基址](../../build/reference/base-base-address.md)（/ 基） 链接器选项。  
  
 指定的程序的可执行文件和 Dll 中的*文件*它们是以数据为基础的顺序在 EDITBIN 命令行上的自变量。 你可以选择指定一个或多个*修饰符*，每个用逗号分隔 (**，**):  
  
|修饰符|操作|  
|--------------|------------|  
|基本 **= * * * 地址*|提供起始地址重新分配到的文件的基址。 指定*地址*以十进制或 C 语言表示法。 如果未指定基的默认开始基址为 0x400000。 必须指定如果 DOWN 为使用的基，和*地址*设置基址的范围的末尾。|  
|BASEFILE|创建一个名为 COFFBASE 文件。TXT、 其是按链接列出的预期格式的文本文件/基本选项。|  
|向下|告知 EDITBIN 若要重新分配基址向下的从结束地址。 指定与位于以下地址范围的末尾的最高可能地址中的第一个文件的顺序重新分配文件。 必须使用向下使用基，以确保足够的地址空间使这些文件。 若要确定由指定的文件所需的地址空间，文件运行使用 /REBASE EDITBIN 和将 64 KB 添加到显示的总大小。|  
  
## <a name="see-also"></a>请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)