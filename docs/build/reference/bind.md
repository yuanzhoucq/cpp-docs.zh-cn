---
title: -BIND |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /bind
dev_langs:
- C++
helpviewer_keywords:
- -BIND editbin option
- entry points, addresses
- BIND editbin option
- entry points
- /BIND editbin option
- import address table
ms.assetid: 3772b330-1868-4c90-857d-c31faa867982
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b77c778017dc78235948e8d23db136c1f63ab12d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="bind"></a>/BIND
```  
/BIND[:PATH=path]  
```  
  
## <a name="remarks"></a>备注  
 此选项可执行文件或 DLL 的导入地址表中设置的入口点的地址。 使用此选项以降低程序的加载时间。  
  
 指定的程序的可执行文件和 Dll 中的*文件*EDITBIN 命令行上的自变量。 可选*路径*/BIND 自变量指定的位置指定的文件使用的 Dll。 使用分号分隔多个目录 (**;**)。 如果*路径*未指定，则 EDITBIN 搜索在 PATH 环境变量中指定的目录。 如果*路径*EDITBIN 忽略 PATH 变量的指定。  
  
 默认情况下，程序加载程序加载程序时设置入口点的地址。 此过程所用的时间会有所不同，具体取决于 Dll 的数目和引用在程序中的入口点数目。 如果某个程序修改用 /BIND，并且基址的可执行文件和其 Dll 不与已经加载的 Dll 冲突，则不需要设置这些地址操作系统。 不正确地基于文件的情况下，操作系统将程序的 Dll，并重新计算的入口点地址，这将添加到程序的加载时间。  
  
## <a name="see-also"></a>请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)