---
title: 对象状态宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
ms.openlocfilehash: 5617ce7fb972c98775072f72244f91052d41ece3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326167"
---
# <a name="object-status-macros"></a>对象状态宏

此宏设置属于 ActiveX 控件的标志。

|||
|-|-|
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|用于 ATL ActiveX 控件，用于设置 OLEMISC 标志。|

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="declare_olemisc_status"></a><a name="declare_olemisc_status"></a>DECLARE_OLEMISC_STATUS

用于 ATL ActiveX 控件，用于设置 OLEMISC 标志。

```
DECLARE_OLEMISC_STATUS( miscstatus )
```

### <a name="parameters"></a>参数

*错误状态*<br/>
所有适用的 OLEMISC 标志。

### <a name="remarks"></a>备注

此宏用于为 ActiveX 控件设置 OLEMISC 标志。 有关详细信息，请参阅[IOleObject：获取 MiscCStatus。](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus)

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]

## <a name="see-also"></a>另请参阅

[宏](../../atl/reference/atl-macros.md)
