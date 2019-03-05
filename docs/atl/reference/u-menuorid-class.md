---
title: _U_MENUorID 类
ms.date: 11/04/2016
f1_keywords:
- ATL._U_MENUorID
- ATL::_U_MENUorID
- _U_MENUorID
helpviewer_keywords:
- U_MENUorID class
- _U_MENUorID class
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
ms.openlocfilehash: d02d00e3c56fc253e8f89eec9815e01d60c6e2aa
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259355"
---
# <a name="umenuorid-class"></a>_U_MENUorID 类

此类提供包装`CreateWindow`和`CreateWindowEx`。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
class _U_MENUorID
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[_U_MENUorID::_U_MENUorID](#_u_menuorid___u_menuorid)|构造函数。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[_U_MENUorID::m_hMenu](#_u_menuorid__m_hmenu)|菜单句柄。|

## <a name="remarks"></a>备注

此参数适配器类允许调用方的部分 Id （示） 或菜单句柄 (HMENUs) 传递到函数，而无需显式强制转换。

此类用于实现对 Windows API 的包装器特别[CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa)并[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa)函数，这两种接受可能的子窗口的 HMENU 参数标识符 (UINT) 而不是菜单句柄。 例如，可以看到正在使用此类作为参数[CWindowImpl::Create](cwindowimpl-class.md#create)。

该类定义两个构造函数重载： 一个接受 UINT 参数和另一个接受的 HMENU 参数。 UINT 参数只是强制转换为构造函数和类的单个数据成员中存储的结果中 HMENU [m_hMenu](#_u_menuorid__m_hmenu)。 转换不直接存储 HMENU 构造函数的参数。

## <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="_u_menuorid__m_hmenu"></a>  _U_MENUorID::m_hMenu

类包含传递给其构造函数之一为公共的 HMENU 数据成员的值。

```
HMENU m_hMenu;
```

##  <a name="_u_menuorid___u_menuorid"></a>  _U_MENUorID::_U_MENUorID

UINT 参数只是强制转换为构造函数和类的单个数据成员中存储的结果中 HMENU [m_hMenu](#_u_menuorid__m_hmenu)。

```
_U_MENUorID(UINT nID);
_U_MENUorID(HMENU hMenu);
```

### <a name="parameters"></a>参数

*nID*<br/>
子窗口标识符。

*hMenu*<br/>
菜单句柄。

### <a name="remarks"></a>备注

转换不直接存储 HMENU 构造函数的参数。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
