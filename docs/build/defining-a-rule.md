---
title: 定义规则
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, inference rules
- defining inference rules
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
ms.openlocfilehash: 7031f56d82fcaf557388c7600d493ebda48add1a
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416925"
---
# <a name="defining-a-rule"></a>定义规则

*Fromext*表示依赖文件的扩展并*toext*表示目标文件的扩展名。

```
.fromext.toext:
   commands
```

## <a name="remarks"></a>备注

扩展不区分大小写。 可以调用宏来表示*fromext*并*toext*; 宏展开在预处理期间。 句点 （.） 前面*fromext*必须出现在行的开头。 冒号 （:） 前面有零个或多个空格或制表符。 它可以后接只能由空格或制表符、 分号 （;） 以指定的命令、 数字符号 （#） 来指定的注释或换行字符。 不允许存在其他空格。 描述块与指定的命令。

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

[规则中的搜索路径](../build/search-paths-in-rules.md)

## <a name="see-also"></a>请参阅

[推理规则](../build/inference-rules.md)
