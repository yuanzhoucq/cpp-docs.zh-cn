---
title: "CBitmapRenderTarget 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::Attach
- AFXRENDERTARGET/CBitmapRenderTarget::Detach
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmap
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::m_pBitmapRenderTarget
dev_langs:
- C++
helpviewer_keywords:
- CBitmapRenderTarget class
ms.assetid: c89a4437-812e-4943-acb2-b429a04cc4d2
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 73410ae17465880f455e5b15026f6cc010803c19
ms.openlocfilehash: 11bea138185df23c9f3cc79491c71d86861a6bdc
ms.lasthandoff: 02/24/2017

---
# <a name="cbitmaprendertarget-class"></a>CBitmapRenderTarget 类
ID2D1BitmapRenderTarget 包装器。  
  
## <a name="syntax"></a>语法  
  
```  
class CBitmapRenderTarget : public CRenderTarget;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CBitmapRenderTarget::CBitmapRenderTarget](#cbitmaprendertarget)|构造 CBitmapRenderTarget 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CBitmapRenderTarget::Attach](#attach)|附加现有的呈现器目标接口的对象|  
|[CBitmapRenderTarget::Detach](#detach)|分离对象中的呈现器目标接口|  
|[CBitmapRenderTarget::GetBitmap](#getbitmap)|检索此呈现器目标位图。 返回的位图可以用于绘图操作。|  
|[CBitmapRenderTarget::GetBitmapRenderTarget](#getbitmaprendertarget)|返回 ID2D1BitmapRenderTarget 接口|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CBitmapRenderTarget::operator ID2D1BitmapRenderTarget *](#operator_id2d1bitmaprendertarget_star)|返回 ID2D1BitmapRenderTarget 接口|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CBitmapRenderTarget::m_pBitmapRenderTarget](#m_pbitmaprendertarget)|指向 ID2D1BitmapRenderTarget 对象的指针。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
 `CBitmapRenderTarget` 
  
## <a name="requirements"></a>要求  
 **标头︰** afxrendertarget.h  
  
##  <a name="attach"></a>CBitmapRenderTarget::Attach  
 附加现有的呈现器目标接口的对象  
  
```  
void Attach(ID2D1BitmapRenderTarget* pTarget);
```  
  
### <a name="parameters"></a>参数  
 `pTarget`  
 现有的呈现器目标接口。 不能为 NULL  
  
##  <a name="cbitmaprendertarget"></a>CBitmapRenderTarget::CBitmapRenderTarget  
 构造 CBitmapRenderTarget 对象。  
  
```  
CBitmapRenderTarget();
```  
  
##  <a name="detach"></a>CBitmapRenderTarget::Detach  
 分离对象中的呈现器目标接口  
  
```  
ID2D1BitmapRenderTarget* Detach();
```  
  
### <a name="return-value"></a>返回值  
 指向分离呈现器目标接口。  
  
##  <a name="getbitmap"></a>CBitmapRenderTarget::GetBitmap  
 检索此呈现器目标位图。 返回的位图可以用于绘图操作。  
  
```  
BOOL GetBitmap(CD2DBitmap& bitmap);
```  
  
### <a name="parameters"></a>参数  
 `bitmap`  
 此方法返回时，包含此呈现器目标的有效位图。 此位图可以用于绘图操作。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE。  
  
##  <a name="getbitmaprendertarget"></a>CBitmapRenderTarget::GetBitmapRenderTarget  
 返回 ID2D1BitmapRenderTarget 接口  
  
```  
ID2D1BitmapRenderTarget* GetBitmapRenderTarget();
```  
  
### <a name="return-value"></a>返回值  
 指向 ID2D1BitmapRenderTarget 接口或者如果对象尚未初始化为 NULL 指针。  
  
##  <a name="m_pbitmaprendertarget"></a>CBitmapRenderTarget::m_pBitmapRenderTarget  
 指向 ID2D1BitmapRenderTarget 对象的指针。  
  
```  
ID2D1BitmapRenderTarget* m_pBitmapRenderTarget;  
```  
  
##  <a name="operator_id2d1bitmaprendertarget_star"></a>CBitmapRenderTarget::operator ID2D1BitmapRenderTarget *  
 返回 ID2D1BitmapRenderTarget 接口  
  
```  
operator ID2D1BitmapRenderTarget*();
```   
  
### <a name="return-value"></a>返回值  
 指向 ID2D1BitmapRenderTarget 接口或者如果对象尚未初始化为 NULL 指针。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

