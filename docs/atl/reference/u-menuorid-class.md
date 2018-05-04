---
title: _U_MENUorID 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL._U_MENUorID
- ATL::_U_MENUorID
- _U_MENUorID
dev_langs:
- C++
helpviewer_keywords:
- U_MENUorID class
- _U_MENUorID class
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 847a735cdba6b9ff4173e23acf78ea7dc4d3034c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="umenuorid-class"></a>_U_MENUorID 类
此类提供的包装**CreateWindow**和**CreateWindowEx**。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
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
 此自变量适配器类允许任一 Id ( **UINT**s) 或菜单句柄 ( `HMENU`s) 传递到函数，而无需在调用方的部分上的显式转换。  
  
 此类专用于实现包装 Windows api 中，特别是[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)和[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)函数，这两种接受`HMENU`可能是子任务的自变量窗口标识符 ( **UINT**) 而不是菜单句柄。 例如，你可以看到中使用此类作为参数传递给[CWindowImpl::Create](cwindowimpl-class.md#create)。  

  
 类定义两个构造函数重载： 一种方法接受**UINT**参数，而另接受`HMENU`自变量。 **UINT**自变量只是强制转换为`HMENU`中构造函数，并在类的单个数据成员中存储的结果[m_hMenu](#_u_menuorid__m_hmenu)。 自变量`HMENU`构造函数存储直接进行转换。  
  
## <a name="requirements"></a>要求  
 **标头：** atlwin.h  
  
##  <a name="_u_menuorid__m_hmenu"></a>  _U_MENUorID::m_hMenu  
 类包含传递给其构造函数之一为公共的值`HMENU`数据成员。  
  
```
HMENU m_hMenu;
```  
  
##  <a name="_u_menuorid___u_menuorid"></a>  _U_MENUorID::_U_MENUorID  
 **UINT**自变量只是强制转换为`HMENU`中构造函数，并在类的单个数据成员中存储的结果[m_hMenu](#_u_menuorid__m_hmenu)。  
  
```
_U_MENUorID(UINT nID);  
_U_MENUorID(HMENU hMenu);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 子窗口标识符。  
  
 `hMenu`  
 菜单句柄。  
  
### <a name="remarks"></a>备注  
 自变量`HMENU`构造函数存储直接进行转换。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)
