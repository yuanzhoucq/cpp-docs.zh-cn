---
title: _U_STRINGorID 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL._U_STRINGorID
- ATL::_U_STRINGorID
- _U_STRINGorID
dev_langs:
- C++
helpviewer_keywords:
- _U_STRINGorID class
- U_STRINGorID class
ms.assetid: 443cdc00-d265-4b27-8ef3-2feb95f3e5e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9c465e5da4d3822782bd9c7b81e497ea544e3bd1
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43759949"
---
# <a name="ustringorid-class"></a>_U_STRINGorID 类

此参数适配器类允许资源名称 (LPCTSTRs) 或资源 Id （示） 要传递给函数，而无需调用方将 ID 转换为使用 MAKEINTRESOURCE 宏的字符串。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
class _U_STRINGorID
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[_U_STRINGorID::_U_STRINGorID](#_u_stringorid___u_stringorid)|构造函数。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[_U_STRINGorID::m_lpstr](#_u_stringorid__m_lpstr)|资源标识符中。|

## <a name="remarks"></a>备注

此类用于实现与 Windows 资源管理 API 的包装器，例如[FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea)， [LoadIcon](/windows/desktop/api/winuser/nf-winuser-loadicona)，并[LoadMenu](/windows/desktop/api/winuser/nf-winuser-loadmenua)函数，接受LPCTSTR 参数可能是资源的名称或其 id。

该类定义两个构造函数重载： 一个接受 LPCTSTR 参数和另一个接受 UINT 参数。 UINT 参数转换为资源类型使用 MAKEINTRESOURCE 宏和结果存储在类的单个数据成员中的 Windows 资源管理功能与兼容[m_lpstr](#_u_stringorid__m_lpstr)。 转换不直接存储 LPCTSTR 构造函数的参数。

## <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="_u_stringorid__m_lpstr"></a>  _U_STRINGorID::m_lpstr

类包含传递给其构造函数之一为公共的 LPCTSTR 数据成员的值。

```
LPCTSTR m_lpstr;
```

##  <a name="_u_stringorid___u_stringorid"></a>  _U_STRINGorID::_U_STRINGorID

UINT 构造函数将其自变量转换为与 Windows 资源管理功能使用 MAKEINTRESOURCE 宏兼容的资源类型并将结果存储在类的单个数据成员中， [m_lpstr](#_u_stringorid__m_lpstr)。

```
_U_STRINGorID(UINT nID);  
_U_STRINGorID(LPCTSTR lpString);
```

### <a name="parameters"></a>参数

*nID*  
资源 id。

*lpString*  
资源名称。

### <a name="remarks"></a>备注

转换不直接存储 LPCTSTR 构造函数的参数。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
