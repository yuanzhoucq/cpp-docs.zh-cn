---
title: "_U_STRINGorID 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ebc1b8f65f2a0841baf09b5c95528f571f97ce38
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ustringorid-class"></a>_U_STRINGorID 类
此自变量适配器类允许任一资源名称 ( `LPCTSTR`s) 或资源 Id ( **UINT**s) 传递到函数，而无需调用方将 ID 转换为字符串使用**MAKEINTRESOURCE**宏。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
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
|[_U_STRINGorID::m_lpstr](#_u_stringorid__m_lpstr)|资源标识符。|  
  
## <a name="remarks"></a>备注  
 此类专用于如实现对 Windows 资源管理 API 的包装器[FindResource](http://msdn.microsoft.com/library/windows/desktop/ms648042)， [LoadIcon](http://msdn.microsoft.com/library/windows/desktop/ms648072)，和[LoadMenu](http://msdn.microsoft.com/library/windows/desktop/ms647990)函数，它们接受`LPCTSTR`资源的名称，或者其 id。 可能的自变量  
  
 类定义两个构造函数重载： 一种方法接受`LPCTSTR`参数，而另接受**UINT**自变量。 **UINT**自变量转换为与使用 Windows 资源管理函数兼容的资源类型**MAKEINTRESOURCE**宏，并且在类的单个数据成员中存储的结果[m_lpstr](#_u_stringorid__m_lpstr)。 自变量`LPCTSTR`构造函数存储直接进行转换。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlwin.h  
  
##  <a name="_u_stringorid__m_lpstr"></a>_U_STRINGorID::m_lpstr  
 类包含传递给其构造函数之一为公共的值`LPCTSTR`数据成员。  
  
```
LPCTSTR m_lpstr;
```  
  
##  <a name="_u_stringorid___u_stringorid"></a>_U_STRINGorID::_U_STRINGorID  
 **UINT**构造函数将其自变量转换为与使用 Windows 资源管理函数兼容的资源类型**MAKEINTRESOURCE**宏和结果存储在类的单数据成员[m_lpstr](#_u_stringorid__m_lpstr)。  
  
```
_U_STRINGorID(UINT nID);  
_U_STRINGorID(LPCTSTR lpString);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 是资源 id。  
  
 `lpString`  
 资源名称。  
  
### <a name="remarks"></a>备注  
 自变量`LPCTSTR`构造函数存储直接进行转换。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)
