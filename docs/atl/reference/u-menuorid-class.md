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
ms.openlocfilehash: 419c9e79178db12efe278838ec8630e04ac3c461
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325840"
---
# <a name="_u_menuorid-class"></a>_U_MENUorID 类

此类为`CreateWindow`和`CreateWindowEx`提供包装。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class _U_MENUorID
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[_U_MENUorID：_U_MENUorID](#_u_menuorid___u_menuorid)|构造函数。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[_U_MENUorID：m_hMenu](#_u_menuorid__m_hmenu)|菜单的句柄。|

## <a name="remarks"></a>备注

此参数适配器类允许将 ID （UINTs） 或菜单句柄 （HMENUs） 传递给函数，而无需调用方的显式强制转换。

此类旨在实现 Windows API 的包装，尤其是[CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww)和[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)函数，这两个函数都接受可能是子窗口标识符 （UINT） 而不是菜单句柄的 HMENU 参数。 例如，您可以看到此类正在用作[CWindowImpl：：：create](cwindowimpl-class.md#create)的参数。

类定义两个构造函数重载：一个接受 UINT 参数，另一个接受 HMENU 参数。 UINT 参数只是强制转换为构造函数中的 HMENU，并将结果存储在类的单个数据成员[m_hMenu](#_u_menuorid__m_hmenu)中。 HMENU 构造函数的参数直接存储而不转换。

## <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="_u_menuoridm_hmenu"></a><a name="_u_menuorid__m_hmenu"></a>_U_MENUorID：m_hMenu

类保存作为公共 HMENU 数据成员传递给其任一构造函数的值。

```
HMENU m_hMenu;
```

## <a name="_u_menuorid_u_menuorid"></a><a name="_u_menuorid___u_menuorid"></a>_U_MENUorID：_U_MENUorID

UINT 参数只是强制转换为构造函数中的 HMENU，并将结果存储在类的单个数据成员[m_hMenu](#_u_menuorid__m_hmenu)中。

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

HMENU 构造函数的参数直接存储而不转换。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
