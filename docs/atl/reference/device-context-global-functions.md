---
title: 设备上下文全局函数
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
ms.openlocfilehash: e640f310a1976c29a39f0ab7c2575dfd1073c889
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330155"
---
# <a name="device-context-global-functions"></a>设备上下文全局函数

此功能为给定设备创建设备上下文。

|||
|-|-|
|[AtlCreateTargetDC](#atlcreatetargetdc)|创建设备上下文。|

## <a name="atlcreatetargetdc"></a><a name="atlcreatetargetdc"></a>AtlCreate目标DC

为[DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice)结构中指定的设备创建设备上下文。

```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```

### <a name="parameters"></a>参数

*hdc*<br/>
[在]设备上下文的现有句柄，或 NULL。

*ptd*<br/>
[在]指向包含有关目标设备`DVTARGETDEVICE`的信息的结构的指针。

### <a name="return-value"></a>返回值

将句柄返回到 中指定的设备的设备上下文`DVTARGETDEVICE`。 如果未指定设备，则将句柄返回到默认显示设备。

### <a name="remarks"></a>备注

如果结构为*NULL，hdc*为 NULL，则为默认显示设备创建设备上下文。

如果*hdc*不是 NULL，并且*ptd*为 NULL，则函数将返回现有的*hdc*。

## <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="see-also"></a>另请参阅

[函数](../../atl/reference/atl-functions.md)
