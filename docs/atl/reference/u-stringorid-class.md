---
title: _U_STRINGorID 类
ms.date: 11/04/2016
f1_keywords:
- ATL._U_STRINGorID
- ATL::_U_STRINGorID
- _U_STRINGorID
helpviewer_keywords:
- _U_STRINGorID class
- U_STRINGorID class
ms.assetid: 443cdc00-d265-4b27-8ef3-2feb95f3e5e3
ms.openlocfilehash: 4e46ceec077b8daf8ef2a76110d2fc19dd39ae26
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325827"
---
# <a name="_u_stringorid-class"></a>_U_STRINGorID 类

此参数适配器类允许将资源名称 （LPCTSTRs） 或资源 ID （UINT） 传递给函数，而无需调用方使用 MAKEINTRESOURCE 宏将 ID 转换为字符串。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class _U_STRINGorID
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[_U_STRINGorID：_U_STRINGorID](#_u_stringorid___u_stringorid)|构造函数。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[_U_STRINGorID：m_lpstr](#_u_stringorid__m_lpstr)|资源标识符。|

## <a name="remarks"></a>备注

此类旨在实现 Windows 资源管理 API 的包装器，如[FindResource、LoadIcon](/windows/win32/api/winbase/nf-winbase-findresourcea)和[LoadMenu](/windows/win32/api/winuser/nf-winuser-loadmenuw)函数，这些函数接受可以是资源名称或其 ID 的 LPCTSTR 参数。 [LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw)

该类定义两个构造函数重载：一个接受 LPCTSTR 参数，另一个接受 UINT 参数。 UINT 参数将转换为与 Windows 资源管理函数兼容的资源类型，使用 MAKEINTRESOURCE 宏和存储在类的单个数据成员m_lpstr[的结果。](#_u_stringorid__m_lpstr) LPCTSTR 构造函数的参数直接存储而不转换。

## <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="_u_stringoridm_lpstr"></a><a name="_u_stringorid__m_lpstr"></a>_U_STRINGorID：m_lpstr

类保存作为公共 LPCTSTR 数据成员传递给其任一构造函数的值。

```
LPCTSTR m_lpstr;
```

## <a name="_u_stringorid_u_stringorid"></a><a name="_u_stringorid___u_stringorid"></a>_U_STRINGorID：_U_STRINGorID

UINT 构造函数使用 MAKEINTRESOURCE 宏将其参数转换为与 Windows 资源管理函数兼容的资源类型，结果存储在类的单个数据成员[m_lpstr](#_u_stringorid__m_lpstr)。

```
_U_STRINGorID(UINT nID);
_U_STRINGorID(LPCTSTR lpString);
```

### <a name="parameters"></a>参数

*nID*<br/>
资源 ID。

*lpString*<br/>
资源名称。

### <a name="remarks"></a>备注

LPCTSTR 构造函数的参数直接存储而不转换。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
