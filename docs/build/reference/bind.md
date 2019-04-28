---
title: /BIND
ms.date: 11/04/2016
f1_keywords:
- /bind
helpviewer_keywords:
- -BIND editbin option
- entry points, addresses
- BIND editbin option
- entry points
- /BIND editbin option
- import address table
ms.assetid: 3772b330-1868-4c90-857d-c31faa867982
ms.openlocfilehash: e8ba0a5f0235c8771567e4e43172bdf8c81c99a2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295027"
---
# <a name="bind"></a>/BIND

```
/BIND[:PATH=path]
```

## <a name="remarks"></a>备注

此选项设置为可执行文件或 DLL 的导入地址表中的入口点的地址。 使用此选项可减少加载的程序的时间。

指定的程序可执行文件和中的 Dll*文件*EDITBIN 命令行上的参数。 可选*路径*/BIND 参数指定使用指定的文件的 Dll 的位置。 用分号分隔多个目录 (**;**)。 如果*路径*未指定，则 EDITBIN 搜索路径环境变量中指定的目录。 如果*路径*EDITBIN 忽略 PATH 变量的指定。

默认情况下，程序加载程序加载程序时设置入口点的地址。 此过程所需的时间会有所不同，具体取决于 Dll 数和在程序中引用的入口点的数目。 如果某个程序修改与 /BIND，并且基址的可执行文件和其 Dll 不与已加载的 Dll 冲突，则不需要设置这些地址操作系统。 中会错误地基于文件的情况下，操作系统重新定位到该程序的 Dll，并重新计算的入口点地址，这将添加到程序的加载时间。

## <a name="see-also"></a>请参阅

[EDITBIN 选项](editbin-options.md)
