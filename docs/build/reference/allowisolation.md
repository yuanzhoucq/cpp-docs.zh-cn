---
title: /ALLOWISOLATION
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
ms.openlocfilehash: 02012e7561fe8462f5f25ae13d961c35561666ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273139"
---
# <a name="allowisolation"></a>/ALLOWISOLATION

指定清单查找的行为。

## <a name="syntax"></a>语法

```

/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>备注

**/ALLOWISOLATION**会导致操作系统进行清单查找和加载。

**/ALLOWISOLATION**是默认值。

**/ALLOWISOLATION:NO**指示就好像没有清单，并使加载可执行文件[EDITBIN 参考](editbin-reference.md)若要设置`IMAGE_DLLCHARACTERISTICS_NO_ISOLATION`可选标头的位`DllCharacteristics`字段。

当对可执行文件禁用隔离时，Windows 加载程序不会尝试为新创建的进程查找应用程序清单。 新进程没有默认激活上下文，即使可执行文件本身中的清单或清单是否具有名称*可执行文件名称*.exe.manifest 的清单。

## <a name="see-also"></a>请参阅

[EDITBIN 选项](editbin-options.md)<br/>
[/ALLOWISOLATION（清单查找）](allowisolation-manifest-lookup.md)<br/>
[清单文件引用](/windows/desktop/SbsCs/manifest-files-reference)
