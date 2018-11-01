---
title: 依赖项的搜索路径
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, dependents
- dependents, NMAKE
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
ms.openlocfilehash: 8856d845d51072d205c84278978c7fbb447aed9b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448797"
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