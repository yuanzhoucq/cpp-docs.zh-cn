---
title: /ALLOWISOLATION
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION_EDITBIN
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
ms.openlocfilehash: 3dae8ee83e25492fab0ba2c6a55681728d5f3453
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440370"
---
# <a name="allowisolation"></a>/ALLOWISOLATION

指定清单查找的行为。

## <a name="syntax"></a>语法

```

/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>备注

**/ALLOWISOLATION**导致操作系统进行清单查找和加载。

默认值为 **/ALLOWISOLATION** 。

**/ALLOWISOLATION： NO**表示加载可执行文件，就像没有清单一样，并导致[EDITBIN 引用](editbin-reference.md)在可选标头的 `DllCharacteristics` 字段中设置 `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` 位。

当对可执行文件禁用隔离时，Windows 加载程序不会尝试为新创建的进程查找应用程序清单。 新进程没有默认激活上下文，即使可执行文件本身中有清单或存在名为*executable*. .manifest 的清单也是如此。

## <a name="see-also"></a>另请参阅

[EDITBIN 选项](editbin-options.md)<br/>
[/ALLOWISOLATION（清单查找）](allowisolation-manifest-lookup.md)<br/>
[清单文件引用](/windows/win32/SbsCs/manifest-files-reference)
