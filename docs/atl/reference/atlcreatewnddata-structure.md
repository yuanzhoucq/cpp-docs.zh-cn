---
title: _AtlCreateWndData 结构
ms.date: 11/04/2016
f1_keywords:
- ATL::_AtlCreateWndData
- ATL._AtlCreateWndData
- _AtlCreateWndData
helpviewer_keywords:
- _AtlCreateWndData structure
- AtlCreateWndData structure
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
ms.openlocfilehash: 6453156a59b73bcb06c7c86920e1dc524874cef8
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168535"
---
# <a name="_atlcreatewnddata-structure"></a>_AtlCreateWndData 结构

此结构包含 ATL 中的窗口代码中的类实例数据。

## <a name="syntax"></a>语法

```cpp
    struct _AtlCreateWndData{
    void* m_pThis;
    DWORD m_dwThreadID;
    _AtlCreateWndData* m_pNext;
};
```

## <a name="members"></a>成员

`m_pThis`<br/>
用于获取对窗口过程中的类实例的访问权限的**this**指针。

`m_dwThreadID`<br/>
当前类实例的线程 ID。

`m_pNext`<br/>
指向下一个`_AtlCreateWndData`对象的指针。

## <a name="requirements"></a>要求

**标头：** atlbase。h

## <a name="see-also"></a>另请参阅

[类和结构](../../atl/reference/atl-classes.md)
