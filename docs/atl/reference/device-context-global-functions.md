---
title: 设备上下文全局函数
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
ms.openlocfilehash: 25ceae897d3cc845ab06fd4d898c87518b15eacb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551194"
---
# <a name="device-context-global-functions"></a>设备上下文全局函数

此函数创建给定设备的设备上下文。

|||
|-|-|
|[AtlCreateTargetDC](#atlcreatetargetdc)|创建设备上下文。|

##  <a name="atlcreatetargetdc"></a>  AtlCreateTargetDC

创建设备上下文中指定的设备[DVTARGETDEVICE](/windows/desktop/api/objidl/ns-objidl-tagdvtargetdevice)结构。

```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```

### <a name="parameters"></a>参数

*hdc*<br/>
[in]设备上下文或为 NULL 的现有句柄。

*ptd*<br/>
[in]一个指向`DVTARGETDEVICE`结构，其中包含有关目标设备的信息。

### <a name="return-value"></a>返回值

返回的句柄中指定的设备的设备上下文`DVTARGETDEVICE`。 如果未不指定任何设备，则返回的句柄的默认显示设备。

### <a name="remarks"></a>备注

如果结构为 NULL 并且*hdc*为 NULL，则创建的默认显示设备的设备上下文。

如果*hdc*不为 NULL 并*ptd*为 NULL，该函数将返回现有*hdc*。

## <a name="requirements"></a>要求

**标头：** atlwin.h

## <a name="see-also"></a>请参阅

[函数](../../atl/reference/atl-functions.md)
