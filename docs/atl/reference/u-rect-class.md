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
ms.openlocfilehash: 306092a00a1e119263f4563eea181d7d3ee2b4b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274520"
---
# <a name="urect-class"></a>_U_RECT 类

此参数适配器类允许`RECT`指针或引用要传递给实现方面的指针的函数。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
class _U_RECT
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[_U_RECT::_U_RECT](#_u_rect___u_rect)|构造函数。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[_U_RECT::m_lpRect](#_u_rect__m_lprect)|指向`RECT`。|

## <a name="remarks"></a>备注

该类定义两个构造函数重载： 一个接受**RECT &** 参数，另一个接受`LPRECT`参数。 第一个构造函数将引用自变量的地址存储在类的单个数据成员[m_lpRect](#_u_rect__m_lprect)。 转换不直接存储指针构造函数的参数。

## <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="_u_rect__m_lprect"></a>  _U_RECT::m_lpRect

类包含公共作为传递给其构造函数之一的值`LPRECT`数据成员。

```
LPRECT m_lpRect;
```

##  <a name="_u_rect___u_rect"></a>  _U_RECT::_U_RECT

引用自变量的地址存储在类的单个数据成员[m_lpRect](#_u_rect__m_lprect)。

```
_U_RECT(RECT& rc);
_U_RECT(LPRECT lpRect);
```

### <a name="parameters"></a>参数

*rc*<br/>
一个`RECT`引用。

*lpRect*<br/>
一个`RECT`指针。

### <a name="remarks"></a>备注

转换不直接存储指针构造函数的参数。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
