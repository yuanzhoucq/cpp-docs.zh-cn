---
title: _U_RECT 类
ms.date: 11/04/2016
f1_keywords:
- ATL::_U_RECT
- _U_RECT
- ATL._U_RECT
helpviewer_keywords:
- U_RECT class
- _U_RECT class
ms.assetid: 5f880a2d-09cf-4327-bf32-a3519c4dcd63
ms.openlocfilehash: 8a4d5b2a770b3f0ecfe10be0fbad22a702aa0531
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325813"
---
# <a name="_u_rect-class"></a>_U_RECT 类

此参数适配器类允许将`RECT`指针或引用传递给在指针方面实现的函数。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class _U_RECT
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[_U_RECT：_U_RECT](#_u_rect___u_rect)|构造函数。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[_U_RECT：m_lpRect](#_u_rect__m_lprect)|指向 的`RECT`指针。|

## <a name="remarks"></a>备注

类定义两个构造函数重载：一个接受**RECT&** 参数，另一个`LPRECT`接受参数。 第一个构造函数将引用参数的地址存储在类的单个数据成员[m_lpRect](#_u_rect__m_lprect)。 指针构造函数的参数直接存储而不转换。

## <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="_u_rectm_lprect"></a><a name="_u_rect__m_lprect"></a>_U_RECT：m_lpRect

类保存作为公共`LPRECT`数据成员传递给其任一构造函数的值。

```
LPRECT m_lpRect;
```

## <a name="_u_rect_u_rect"></a><a name="_u_rect___u_rect"></a>_U_RECT：_U_RECT

引用参数的地址存储在类的单个数据成员[中，m_lpRect](#_u_rect__m_lprect)。

```
_U_RECT(RECT& rc);
_U_RECT(LPRECT lpRect);
```

### <a name="parameters"></a>参数

*钢筋混凝土*<br/>
`RECT` 引用。

*lpRect*<br/>
指针`RECT`。

### <a name="remarks"></a>备注

指针构造函数的参数直接存储而不转换。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
