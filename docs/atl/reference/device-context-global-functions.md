---
title: 设备上下文全局函数
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
ms.openlocfilehash: d225bd0cd996fd908479b5a93aad81ea0428900b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496098"
---
# <a name="device-context-global-functions"></a>设备上下文全局函数

此函数为给定设备创建设备上下文。

|||
|-|-|
|[AtlCreateTargetDC](#atlcreatetargetdc)|创建设备上下文。|

##  <a name="atlcreatetargetdc"></a>  AtlCreateTargetDC

为[DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice)结构中指定的设备创建设备上下文。

```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```

### <a name="parameters"></a>参数

*hdc*<br/>
中设备上下文的现有句柄, 或为 NULL。

*ptd*<br/>
中指向`DVTARGETDEVICE`结构的指针, 该结构包含有关目标设备的信息。

### <a name="return-value"></a>返回值

返回中`DVTARGETDEVICE`指定的设备的设备上下文的句柄。 如果未指定设备, 则会将句柄返回到默认显示设备。

### <a name="remarks"></a>备注

如果结构为 NULL, 并且*hdc*为 null, 则为默认显示设备创建设备上下文。

如果*hdc*不为 null, 并且*ptd*为 null, 则函数返回现有的*hdc*。

## <a name="requirements"></a>要求

**标头:** atlwin。h

## <a name="see-also"></a>请参阅

[函数](../../atl/reference/atl-functions.md)
