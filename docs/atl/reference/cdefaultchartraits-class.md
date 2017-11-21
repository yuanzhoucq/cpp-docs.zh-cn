---
title: "CDefaultCharTraits 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits::CharToLower
- ATLCOLL/ATL::CDefaultCharTraits::CharToUpper
dev_langs: C++
helpviewer_keywords: CDefaultCharTraits class
ms.assetid: f94a3934-597f-401d-8513-ed6924ae069a
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 02595c426a631e15bf2f1b5baed2550a8befe20a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cdefaultchartraits-class"></a>CDefaultCharTraits 类
此类提供了两个静态函数将之间大写和小写字符转换。  
  
## <a name="syntax"></a>语法  
  
```
template <typename T>  
class CDefaultCharTraits
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要存储在集合中的数据类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDefaultCharTraits::CharToLower](#chartolower)|（静态）调用此函数可将字符转换为大写形式。|  
|[CDefaultCharTraits::CharToUpper](#chartoupper)|（静态）调用此函数可将字符转换为小写。|  
  
## <a name="remarks"></a>备注  
 此类提供了利用类的函数[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** atlcoll.h  
  
##  <a name="chartolower"></a>CDefaultCharTraits::CharToLower  
 调用此函数可将字符转换为小写。  
  
```
static wchar_t CharToLower(wchar_t x);  
static char CharToLower(char x);
```  
  
### <a name="parameters"></a>参数  
 *x*  
 要转换为小写的字符。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#132](../../atl/codesnippet/cpp/cdefaultchartraits-class_1.cpp)]  
  
##  <a name="chartoupper"></a>CDefaultCharTraits::CharToUpper  
 调用此函数可将字符转换为大写形式。  
  
```
static wchar_t CharToUpper(wchar_t x);  
static char CharToUpper(char x);
```  
  
### <a name="parameters"></a>参数  
 *x*  
 要转换为大写的字符。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)
