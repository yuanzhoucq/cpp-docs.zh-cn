---
title: 链接器工具警告 LNK4105
ms.date: 11/04/2016
f1_keywords:
- LNK4105
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
ms.openlocfilehash: 655a6dfde77984cd0c941ec0d8abb0c4d099c80f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183288"
---
# <a name="linker-tools-warning-lnk4105"></a>链接器工具警告 LNK4105

没有用选项 "option" 指定的参数;忽略选项

仅当设置了[/LIBPATH](../../build/reference/libpath-additional-libpath.md)选项时，才会出现此警告。 如果未指定具有此选项的目录，则链接器将忽略该选项并生成此警告消息。

如果不需要重写现有的环境库设置，请从链接器命令行中删除/LIBPATH 选项。 如果要使用库的替代搜索路径，请指定/LIBPATH 选项后面的备用路径。

## <a name="example"></a>示例

```
link /libpath:c:\filepath\lib bar.obj
```

在搜索默认位置之前，将指示链接器在 `c:\filepath\lib` 中搜索所需的库。
