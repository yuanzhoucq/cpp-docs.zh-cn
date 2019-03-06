---
title: 依赖项的搜索路径
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, dependents
- dependents, NMAKE
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
ms.openlocfilehash: 9f2251a5fff9d708a783797d04606572e5ebce62
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426454"
---
# <a name="search-paths-for-dependents"></a>依赖项的搜索路径

每个依赖项有一个可选的搜索路径，按如下所示指定：

## <a name="syntax"></a>语法

```
{directory[;directory...]}dependent
```

## <a name="remarks"></a>备注

NMAKE 查找从属项首先在当前目录中，然后在目录中指定的顺序。 宏可以指定部分或全部搜索路径。 将目录名称括在大括号 （{}）;用分号 （;） 分隔多个目录。 允许空格或制表符。

## <a name="see-also"></a>请参阅

[依赖项](../build/dependents.md)
