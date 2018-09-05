---
title: _ATL_MODULE70 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- _ATL_MODULE70
- ATL::_ATL_MODULE70
- ATL._ATL_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- ATL_MODULE70 structure
- _ATL_MODULE70 structure
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7afe6867f359b334654f58aad39ad7f143dd428
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764886"
---
# <a name="atlmodule70-structure"></a>_ATL_MODULE70 结构

包含使用 ATL 的每个模块的数据。

## <a name="syntax"></a>语法

```
struct _ATL_MODULE70 {
    UINT cbSize;
    LONG m_nLockCnt;
    _ATL_TERMFUNC_ELEM* m_pTermFuncs;
    CComCriticalSection m_csStaticDataInitAndTypeInfo;
};
```

## <a name="members"></a>成员

`cbSize`  
用于版本控制的结构的大小。

`m_nLockCnt`  
引用计数以确定多长时间，该模块应始终处于活动状态。

`m_pTermFuncs`  
跟踪已注册 ATL 关闭时要调用的函数。

`m_csStaticDataInitAndTypeInfo`  
用于协调对在多线程情况下的内部数据的访问。

## <a name="remarks"></a>备注

[_ATL_MODULE](atl-typedefs.md#_atl_module)定义的 typedef 为`_ATL_MODULE70`。

## <a name="requirements"></a>要求

**标头：** atlbase.h

## <a name="see-also"></a>请参阅

[类和结构](../../atl/reference/atl-classes.md)

