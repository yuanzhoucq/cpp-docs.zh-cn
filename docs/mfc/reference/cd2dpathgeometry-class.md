---
title: "CD2DPathGeometry 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::Attach
- AFXRENDERTARGET/CD2DPathGeometry::Create
- AFXRENDERTARGET/CD2DPathGeometry::Destroy
- AFXRENDERTARGET/CD2DPathGeometry::Detach
- AFXRENDERTARGET/CD2DPathGeometry::GetFigureCount
- AFXRENDERTARGET/CD2DPathGeometry::GetSegmentCount
- AFXRENDERTARGET/CD2DPathGeometry::Open
- AFXRENDERTARGET/CD2DPathGeometry::Stream
- AFXRENDERTARGET/CD2DPathGeometry::m_pPathGeometry
dev_langs: C++
helpviewer_keywords:
- CD2DPathGeometry [MFC], CD2DPathGeometry
- CD2DPathGeometry [MFC], Attach
- CD2DPathGeometry [MFC], Create
- CD2DPathGeometry [MFC], Destroy
- CD2DPathGeometry [MFC], Detach
- CD2DPathGeometry [MFC], GetFigureCount
- CD2DPathGeometry [MFC], GetSegmentCount
- CD2DPathGeometry [MFC], Open
- CD2DPathGeometry [MFC], Stream
- CD2DPathGeometry [MFC], m_pPathGeometry
ms.assetid: 686216eb-5080-4242-ace5-8fa1ce96307c
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9142b268c5f09a88883d048c35287966d9ef8aab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cd2dpathgeometry-class"></a>CD2DPathGeometry 类
ID2D1PathGeometry 包装器。  
  
## <a name="syntax"></a>语法  
  
```  
class CD2DPathGeometry : public CD2DGeometry;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DPathGeometry::CD2DPathGeometry](#cd2dpathgeometry)|构造 CD2DPathGeometry 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DPathGeometry::Attach](#attach)|附加现有的资源的对象的接口|  
|[CD2DPathGeometry::Create](#create)|创建 CD2DPathGeometry。 (重写[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create)。)|  
|[CD2DPathGeometry::Destroy](#destroy)|销毁 CD2DPathGeometry 对象。 (重写[CD2DGeometry::Destroy](../../mfc/reference/cd2dgeometry-class.md#destroy)。)|  
|[CD2DPathGeometry::Detach](#detach)|分离资源接口从该对象|  
|[CD2DPathGeometry::GetFigureCount](#getfigurecount)|检索路径几何图形中的图形的数量。|  
|[CD2DPathGeometry::GetSegmentCount](#getsegmentcount)|检索的路径几何图形中的段的数目。|  
|[CD2DPathGeometry::Open](#open)|检索用于填充图形和段的路径几何图形几何图形接收器。|  
|[CD2DPathGeometry::Stream](#stream)|将路径几何图形的内容复制到指定 ID2D1GeometrySink。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|name|描述|  
|----------|-----------------|  
|[CD2DPathGeometry::m_pPathGeometry](#m_ppathgeometry)|指向 ID2D1PathGeometry 的指针。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DGeometry](../../mfc/reference/cd2dgeometry-class.md)  
  
 `CD2DPathGeometry`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxrendertarget.h  
  
##  <a name="attach"></a>CD2DPathGeometry::Attach  
 附加现有的资源的对象的接口  
  
```  
void Attach(ID2D1PathGeometry* pResource);
```  
  
### <a name="parameters"></a>参数  
 `pResource`  
 现有资源接口。 不能为 NULL  
  
##  <a name="cd2dpathgeometry"></a>CD2DPathGeometry::CD2DPathGeometry  
 构造 CD2DPathGeometry 对象。  
  
```  
CD2DPathGeometry(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `pParentTarget`  
 指向该呈现器目标的指针。  
  
 `bAutoDestroy`  
 指示该对象将销毁所有者 (pParentTarget)。  
  
##  <a name="create"></a>CD2DPathGeometry::Create  
 创建 CD2DPathGeometry。  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>参数  
 `pRenderTarget`  
 指向该呈现器目标的指针。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回，则为 S_OK。 否则，它返回一个 HRESULT 错误代码。  
  
##  <a name="destroy"></a>CD2DPathGeometry::Destroy  
 销毁 CD2DPathGeometry 对象。  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DPathGeometry::Detach  
 分离资源接口从该对象  
  
```  
ID2D1PathGeometry* Detach();
```  
  
### <a name="return-value"></a>返回值  
 指向分离的资源接口指针。  
  
##  <a name="getfigurecount"></a>CD2DPathGeometry::GetFigureCount  
 检索路径几何图形中的图形的数量。  
  
```  
int GetFigureCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回路径几何图形中的图形数。  
  
##  <a name="getsegmentcount"></a>CD2DPathGeometry::GetSegmentCount  
 检索的路径几何图形中的段的数目。  
  
```  
int GetSegmentCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回路径几何图形中的段的数目。  
  
##  <a name="m_ppathgeometry"></a>CD2DPathGeometry::m_pPathGeometry  
 指向 ID2D1PathGeometry 的指针。  
  
```  
ID2D1PathGeometry* m_pPathGeometry;  
```  
  
##  <a name="open"></a>CD2DPathGeometry::Open  
 检索用于填充图形和段的路径几何图形几何图形接收器。  
  
```  
ID2D1GeometrySink* Open();
```  
  
### <a name="return-value"></a>返回值  
 用于填充图形和段的路径几何图形 ID2D1GeometrySink 指向的指针。  
  
##  <a name="stream"></a>CD2DPathGeometry::Stream  
 将路径几何图形的内容复制到指定 ID2D1GeometrySink。  
  
```  
BOOL Stream(ID2D1GeometrySink* geometrySink);
```  
  
### <a name="parameters"></a>参数  
 `geometrySink`  
 路径几何图形的内容复制到接收器。 修改此接收器不会更改此路径几何图形的内容。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE。  
  
## <a name="see-also"></a>请参阅  
 [类](../../mfc/reference/mfc-classes.md)
