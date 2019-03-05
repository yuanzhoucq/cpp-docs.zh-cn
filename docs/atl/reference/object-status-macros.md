---
title: 对象状态宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
ms.openlocfilehash: cb5ff6d7570b03b32852fc450f58043446f721f4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267259"
---
# <a name="object-status-macros"></a>对象状态宏

此宏设置属于 ActiveX 控件的标志。

|||
|-|-|
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|ATL ActiveX 控件中用于设置 OLEMISC 标志。|

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="declare_olemisc_status"></a>  DECLARE_OLEMISC_STATUS

ATL ActiveX 控件中用于设置 OLEMISC 标志。

```
DECLARE_OLEMISC_STATUS( miscstatus )
```

### <a name="parameters"></a>参数

*miscstatus*<br/>
所有适用 OLEMISC 标志。

### <a name="remarks"></a>备注

使用此宏设置 ActiveX 控件的 OLEMISC 标志。 请参阅[IOleObject::GetMiscStatus](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getmiscstatus)的更多详细信息。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]

## <a name="see-also"></a>请参阅

[宏](../../atl/reference/atl-macros.md)
