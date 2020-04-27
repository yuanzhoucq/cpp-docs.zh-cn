---
title: _ATL_MODULE70 结构
ms.date: 11/04/2016
f1_keywords:
- _ATL_MODULE70
- ATL::_ATL_MODULE70
- ATL._ATL_MODULE70
helpviewer_keywords:
- ATL_MODULE70 structure
- _ATL_MODULE70 structure
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
ms.openlocfilehash: 8d39cdd281e09cdfe09546627aa630a11d12464e
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168561"
---
# <a name="_atl_module70-structure"></a>_ATL_MODULE70 结构

包含每个 ATL 模块使用的数据。

## <a name="syntax"></a>语法

```cpp
struct _ATL_MODULE70 {
    UINT cbSize;
    LONG m_nLockCnt;
    _ATL_TERMFUNC_ELEM* m_pTermFuncs;
    CComCriticalSection m_csStaticDataInitAndTypeInfo;
};
```

## <a name="members"></a>成员

`cbSize`<br/>
用于版本控制的结构的大小。

`m_nLockCnt`<br/>
用于确定模块应保持活动状态的引用计数。

`m_pTermFuncs`<br/>
跟踪 ATL 关闭时已注册要调用的函数。

`m_csStaticDataInitAndTypeInfo`<br/>
用于协调对多线程情况下内部数据的访问。

## <a name="remarks"></a>备注

[_ATL_MODULE](atl-typedefs.md#_atl_module)定义为的`_ATL_MODULE70`typedef。

## <a name="requirements"></a>要求

**标头：** atlbase。h

## <a name="see-also"></a>另请参阅

[类和结构](../../atl/reference/atl-classes.md)
