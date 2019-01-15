---
title: 共享常量
ms.date: 11/04/2016
f1_keywords:
- _SH_DENYNO
- _SH_DENYRD
- _SH_DENYRW
- _SH_DENYWR
- _SH_COMPAT
helpviewer_keywords:
- _SH_DENYRW constant
- SH_DENYRD constant
- _SH_COMPAT constant
- _SH_DENYRD constant
- SH_DENYRW constant
- sharing constants
- SH_DENYNO constant
- _SH_DENYWR constant
- SH_DENYWR constant
- _SH_DENYNO constant
- SH_COMPAT constant
ms.assetid: 95fadc3a-55dc-473d-98b5-e8211900465d
ms.openlocfilehash: 5bcebc4f9321ebf3f85bdd757118f779a759fc62
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220512"
---
# <a name="sharing-constants"></a>共享常量

文件共享模式的常量。

## <a name="syntax"></a>语法

```
#include <share.h>
```

## <a name="remarks"></a>备注

shflag 参数确定共享模式，其包括一个或多个清单常量。 这些常量可与 oflag 参数结合（请参阅[文件常量](../c-runtime-library/file-constants.md)）。

下表列出了常量及其含义：

|返回的常量|含义|
|--------------|-------------|
|`_SH_DENYRW`|拒绝对文件的读写访问权限|
|`_SH_DENYWR`|拒绝对文件的写访问权限|
|`_SH_DENYRD`|拒绝对文件的读访问权限|
|`_SH_DENYNO`|允许读写访问权限|
|`_SH_SECURE`|设置安全模式（共享读取、独占写入访问权限）。|

## <a name="see-also"></a>请参阅

[_sopen、_wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[全局常量](../c-runtime-library/global-constants.md)
