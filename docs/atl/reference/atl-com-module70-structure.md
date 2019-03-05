---
title: _ATL_COM_MODULE70 结构
ms.date: 11/04/2016
f1_keywords:
- ATL::_ATL_COM_MODULE70
- ATL._ATL_COM_MODULE70
- _ATL_COM_MODULE70
helpviewer_keywords:
- _ATL_COM_MODULE70 structure
- ATL_COM_MODULE70 structure
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
ms.openlocfilehash: c6361fc5374ed732cd9ccbfbbd1d3d1c2fc8f1f0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261279"
---
# <a name="atlcommodule70-structure"></a>_ATL_COM_MODULE70 结构

由 COM 相关代码在 atl。

## <a name="syntax"></a>语法

```
struct _ATL_COM_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInstTypeLib;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapFirst;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapLast;
    CRITICAL_SECTION m_csObjMap;
};
```

## <a name="members"></a>成员

`cbSize`<br/>
用于版本控制的结构的大小。

`m_hInstTypeLib`<br/>
对此模块的类型库句柄实例。

`m_ppAutoObjMapFirst`<br/>
数组元素，该值指示此模块的对象映射条目的开头的地址。

`m_ppAutoObjMapLast`<br/>
指示此模块的对象映射条目的结束位置的数组元素的地址。

`m_csObjMap`<br/>
若要序列化到对象的映射条目的访问的关键部分。 在内部由 atl。

## <a name="remarks"></a>备注

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)定义为 _ATL_COM_MODULE70 的 typedef。

## <a name="requirements"></a>要求

**标头：** atlbase.h

## <a name="see-also"></a>请参阅

[类和结构](../../atl/reference/atl-classes.md)
