---
title: _AtlCreateWndData Structure
ms.date: 11/04/2016
f1_keywords:
- ATL::_AtlCreateWndData
- ATL._AtlCreateWndData
- _AtlCreateWndData
helpviewer_keywords:
- _AtlCreateWndData structure
- AtlCreateWndData structure
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
ms.openlocfilehash: d6e3168b5c86de5bce3c3b9d3b0fbdea28ae604f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57286923"
---
# <a name="atlcreatewnddata-structure"></a>_AtlCreateWndData Structure

此结构包含在 atl。 窗口化代码中的类实例数据

## <a name="syntax"></a>语法

```
    struct _AtlCreateWndData{
    void* m_pThis;
    DWORD m_dwThreadID;
    _AtlCreateWndData* m_pNext;
};
```

## <a name="members"></a>成员

`m_pThis`<br/>
**这**用于获得在窗口过程中对类实例的指针。

`m_dwThreadID`<br/>
当前类实例的线程 ID。

`m_pNext`<br/>
指向下一个指针`_AtlCreateWndData`对象。

## <a name="requirements"></a>要求

**标头：** atlbase.h

## <a name="see-also"></a>请参阅

[类和结构](../../atl/reference/atl-classes.md)
