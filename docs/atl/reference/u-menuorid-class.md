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
ms.openlocfilehash: 9388ca1751ee27fb25d6751c961d23e5243f2918
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495133"
---
# <a name="_u_menuorid-class"></a>_U_MENUorID 类

此类提供和`CreateWindow` `CreateWindowEx`的包装。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

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
|[_U_MENUorID::m_hMenu](#_u_menuorid__m_hmenu)|菜单的句柄。|

## <a name="remarks"></a>备注

此参数适配器类允许将 Id (UINTs) 或菜单句柄 (HMENUs) 传递给函数, 而无需对调用方的部分进行显式强制转换。

此类旨在实现对 Windows API 的包装 (特别是[CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww)和[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)函数), 这两个函数都接受一个 HMENU 参数, 该参数可以是子窗口标识符 (UINT) 而不是菜单句柄。 例如, 你可以看到此类作为[CWindowImpl:: Create](cwindowimpl-class.md#create)的参数使用。

类定义了两个构造函数重载: 一个接受 UINT 参数, 另一个重载接受 HMENU 参数。 UINT 参数只是强制转换为构造函数中的 HMENU, 并将结果存储在类的单个数据成员[m_hMenu](#_u_menuorid__m_hmenu)中。 无需转换即可直接存储 HMENU 构造函数的参数。

## <a name="requirements"></a>要求

**标头:** atlwin。h

##  <a name="_u_menuorid__m_hmenu"></a>_U_MENUorID::m_hMenu

类将传递给它的任一构造函数的值保存为公共 HMENU 数据成员。

```
HMENU m_hMenu;
```

##  <a name="_u_menuorid___u_menuorid"></a>_U_MENUorID::_U_MENUorID

UINT 参数只是强制转换为构造函数中的 HMENU, 并将结果存储在类的单个数据成员[m_hMenu](#_u_menuorid__m_hmenu)中。

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

无需转换即可直接存储 HMENU 构造函数的参数。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
