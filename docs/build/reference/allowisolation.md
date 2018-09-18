---
title: -ALLOWISOLATION |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ALLOWISOLATION
dev_langs:
- C++
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 12ee07a0ea6dbe2c3bea21aaa6b394b4c3e6f156
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704077"
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

**/ALLOWISOLATION:NO**指示就好像没有清单，并使加载可执行文件[EDITBIN 参考](../../build/reference/editbin-reference.md)若要设置`IMAGE_DLLCHARACTERISTICS_NO_ISOLATION`可选标头的位`DllCharacteristics`字段。

当对可执行文件禁用隔离时，Windows 加载程序不会尝试为新创建的进程查找应用程序清单。 新进程没有默认激活上下文，即使可执行文件本身中的清单或清单是否具有名称*可执行文件名称*.exe.manifest 的清单。

## <a name="see-also"></a>请参阅

[EDITBIN 选项](../../build/reference/editbin-options.md)<br/>
[/ALLOWISOLATION （清单查找）](../../build/reference/allowisolation-manifest-lookup.md)
[清单文件引用](/windows/desktop/SbsCs/manifest-files-reference)