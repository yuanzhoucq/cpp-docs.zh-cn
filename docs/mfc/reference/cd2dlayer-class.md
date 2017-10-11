---
title: "CD2DLayer 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DLayer
- AFXRENDERTARGET/CD2DLayer
- AFXRENDERTARGET/CD2DLayer::CD2DLayer
- AFXRENDERTARGET/CD2DLayer::Attach
- AFXRENDERTARGET/CD2DLayer::Create
- AFXRENDERTARGET/CD2DLayer::Destroy
- AFXRENDERTARGET/CD2DLayer::Detach
- AFXRENDERTARGET/CD2DLayer::Get
- AFXRENDERTARGET/CD2DLayer::GetSize
- AFXRENDERTARGET/CD2DLayer::IsValid
- AFXRENDERTARGET/CD2DLayer::m_pLayer
dev_langs:
- C++
helpviewer_keywords:
- CD2DLayer [MFC], CD2DLayer
- CD2DLayer [MFC], Attach
- CD2DLayer [MFC], Create
- CD2DLayer [MFC], Destroy
- CD2DLayer [MFC], Detach
- CD2DLayer [MFC], Get
- CD2DLayer [MFC], GetSize
- CD2DLayer [MFC], IsValid
- CD2DLayer [MFC], m_pLayer
ms.assetid: 2f96378e-66bb-40d1-9661-6afe324de3c1
caps.latest.revision: 18
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 4a770b6508067913aec51b8b3878f33e30eed4bb
ms.openlocfilehash: cdb6cfe624b0b3ba22d91ab30998aebf5bc96820
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="cd2dlayer-class"></a>CD2DLayer 类
ID2D1Layer 包装器。  
  
## <a name="syntax"></a>语法  
  
```  
class CD2DLayer : public CD2DResource;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DLayer::CD2DLayer](#cd2dlayer)|构造 CD2DLayer 对象。|  
|[CD2DLayer:: ~ CD2DLayer](#_dtorcd2dlayer)|析构函数。 当 D2D 层对象被销毁时调用。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DLayer::Attach](#attach)|附加现有的资源的对象的接口|  
|[CD2DLayer::Create](#create)|创建 CD2DLayer。 (重写[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create)。)|  
|[CD2DLayer::Destroy](#destroy)|销毁 CD2DLayer 对象。 (重写[CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy)。)|  
|[CD2DLayer::Detach](#detach)|分离资源接口从该对象|  
|[CD2DLayer::Get](#get)|返回 ID2D1Layer 接口|  
|[CD2DLayer::GetSize](#getsize)|以独立于设备的像素为单位返回呈现器目标的大小|  
|[CD2DLayer::IsValid](#isvalid)|检查资源有效性 (重写[CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid)。)|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DLayer::operator ID2D1Layer *](#operator_id2d1layer_star)|返回 ID2D1Layer 接口|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DLayer::m_pLayer](#m_player)|将存储指向 ID2D1Layer 对象的指针。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 `CD2DLayer`  
  
## <a name="requirements"></a>要求  
 **标头：** afxrendertarget.h  
  
##  <a name="_dtorcd2dlayer"></a>CD2DLayer:: ~ CD2DLayer  
 析构函数。 当 D2D 层对象被销毁时调用。  
  
```  
virtual ~CD2DLayer();
```  
  
##  <a name="attach"></a>CD2DLayer::Attach  
 附加现有的资源的对象的接口  
  
```  
void Attach(ID2D1Layer* pResource);
```  
  
### <a name="parameters"></a>参数  
 `pResource`  
 现有资源接口。 不能为 NULL  
  
##  <a name="cd2dlayer"></a>CD2DLayer::CD2DLayer  
 构造 CD2DLayer 对象。  
  
```  
CD2DLayer(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `pParentTarget`  
 指向该呈现器目标的指针。  
  
 `bAutoDestroy`  
 指示该对象将销毁所有者 (pParentTarget)。  
  
##  <a name="create"></a>CD2DLayer::Create  
 创建 CD2DLayer。  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>参数  
 `pRenderTarget`  
 指向该呈现器目标的指针。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回，则为 S_OK。 否则，它返回一个 HRESULT 错误代码。  
  
##  <a name="destroy"></a>CD2DLayer::Destroy  
 销毁 CD2DLayer 对象。  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DLayer::Detach  
 分离资源接口从该对象  
  
```  
ID2D1Layer* Detach();
```  
  
### <a name="return-value"></a>返回值  
 指向分离的资源接口指针。  
  
##  <a name="get"></a>CD2DLayer::Get  
 返回 ID2D1Layer 接口  
  
```  
ID2D1Layer* Get();
```  
  
### <a name="return-value"></a>返回值  
 指向 ID2D1Layer 接口或如果尚未初始化对象的 NULL 指针。  
  
##  <a name="getsize"></a>CD2DLayer::GetSize  
 以独立于设备的像素为单位返回呈现器目标的大小  
  
```  
CD2DSizeF GetSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 以独立于设备的像素为单位的呈现器目标的当前大小  
  
##  <a name="isvalid"></a>CD2DLayer::IsValid  
 检查资源有效性  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果资源是有效，则为，TRUE否则为 FALSE。  
  
##  <a name="m_player"></a>CD2DLayer::m_pLayer  
 将存储指向 ID2D1Layer 对象的指针。  
  
```  
ID2D1Layer* m_pLayer;  
```  
  
##  <a name="operator_id2d1layer_star"></a>CD2DLayer::operator ID2D1Layer *  
 返回 ID2D1Layer 接口  
  
```  
operator ID2D1Layer* ();
```  
  
### <a name="return-value"></a>返回值  
 指向 ID2D1Layer 接口或如果尚未初始化对象的 NULL 指针。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

