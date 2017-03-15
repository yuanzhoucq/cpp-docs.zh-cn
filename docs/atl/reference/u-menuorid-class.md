---
title: "_U_MENUorID 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: f7c0a5c34c4e103f830a029f58cdfa00dcb58a32
ms.lasthandoff: 02/24/2017

---
# <a name="umenuorid-class"></a>_U_MENUorID 类
此类提供的包装**CreateWindow**和**CreateWindowEx**。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
class _U_MENUorID
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[_U_MENUorID::_U_MENUorID](#_u_menuorid___u_menuorid)|构造函数。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[_U_MENUorID::m_hMenu](#_u_menuorid__m_hmenu)|一个菜单句柄。|  
  
## <a name="remarks"></a>备注  
 此参数适配器类允许任一 Id ( **UINT**s) 或菜单句柄 ( `HMENU`s) 传递到函数，而无需在调用方的部分的显式强制转换。  
  
 此类专用于实现包装 Windows API 中，尤其是[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)和[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)函数，这两种接受`HMENU`可能是子窗口标识符的参数 ( **UINT**) 而不是菜单句柄。 例如，可以看到正在使用此类以参数形式向[CWindowImpl::Create](cwindowimpl-class.md#create)。  

  
 该类定义两个构造函数重载︰ 一种方法接受**UINT**参数，而另接受`HMENU`参数。 **UINT**参数只是强制转换为`HMENU`中构造函数，并在类的单个数据成员中存储的结果[m_hMenu](#_u_menuorid__m_hmenu)。 参数`HMENU`构造函数存储直接而不进行转换。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlwin.h  
  
##  <a name="a-nameumenuoridmhmenua--umenuoridmhmenu"></a><a name="_u_menuorid__m_hmenu"></a>_U_MENUorID::m_hMenu  
 类包含传递给其构造函数之一为公共的值`HMENU`数据成员。  
  
```
HMENU m_hMenu;
```  
  
##  <a name="a-nameumenuoridumenuorida--umenuoridumenuorid"></a><a name="_u_menuorid___u_menuorid"></a>_U_MENUorID::_U_MENUorID  
 **UINT**参数只是强制转换为`HMENU`中构造函数，并在类的单个数据成员中存储的结果[m_hMenu](#_u_menuorid__m_hmenu)。  
  
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
 参数`HMENU`构造函数存储直接而不进行转换。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

