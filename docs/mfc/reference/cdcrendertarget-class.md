---
title: "CDCRenderTarget 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::Attach
- AFXRENDERTARGET/CDCRenderTarget::BindDC
- AFXRENDERTARGET/CDCRenderTarget::Create
- AFXRENDERTARGET/CDCRenderTarget::Detach
- AFXRENDERTARGET/CDCRenderTarget::GetDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::m_pDCRenderTarget
dev_langs:
- C++
helpviewer_keywords:
- CDCRenderTarget [MFC], CDCRenderTarget
- CDCRenderTarget [MFC], Attach
- CDCRenderTarget [MFC], BindDC
- CDCRenderTarget [MFC], Create
- CDCRenderTarget [MFC], Detach
- CDCRenderTarget [MFC], GetDCRenderTarget
- CDCRenderTarget [MFC], m_pDCRenderTarget
ms.assetid: aa8059c9-08e6-49e4-9b8c-00fa54077a61
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 4a770b6508067913aec51b8b3878f33e30eed4bb
ms.openlocfilehash: e195979967ac5422be67b634d44e2f5d1afa9263
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="cdcrendertarget-class"></a>CDCRenderTarget 类
ID2D1DCRenderTarget 包装器。  
  
## <a name="syntax"></a>语法  
  
```  
class CDCRenderTarget : public CRenderTarget;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CDCRenderTarget::CDCRenderTarget](#cdcrendertarget)|构造 CDCRenderTarget 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDCRenderTarget::Attach](#attach)|附加现有呈现器对对象的目标接口|  
|[CDCRenderTarget::BindDC](#binddc)|将呈现器目标绑定到它发出的绘图命令的设备上下文|  
|[CDCRenderTarget::Create](#create)|创建 CDCRenderTarget。|  
|[CDCRenderTarget::Detach](#detach)|分离呈现器目标接口从该对象|  
|[CDCRenderTarget::GetDCRenderTarget](#getdcrendertarget)|返回 ID2D1DCRenderTarget 接口|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CDCRenderTarget::operator ID2D1DCRenderTarget *](#operator_id2d1dcrendertarget_star)|返回 ID2D1DCRenderTarget 接口|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CDCRenderTarget::m_pDCRenderTarget](#m_pdcrendertarget)|指向 ID2D1DCRenderTarget 对象的指针。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
 [CDCRenderTarget](../../mfc/reference/cdcrendertarget-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxrendertarget.h  
  
##  <a name="attach"></a>CDCRenderTarget::Attach  
 附加现有呈现器对对象的目标接口  
  
```  
void Attach(ID2D1DCRenderTarget* pTarget);
```  
  
### <a name="parameters"></a>参数  
 `pTarget`  
 现有呈现器目标接口。 不能为 NULL  
  
##  <a name="binddc"></a>CDCRenderTarget::BindDC  
 将呈现器目标绑定到它发出的绘图命令的设备上下文  
  
```  
BOOL BindDC(
    const CDC& dc,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>参数  
 `dc`  
 设备上下文呈现目标发出绘图命令  
  
 `rect`  
 设备上下文 (HDC) 呈现器目标绑定到的句柄的尺寸  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE。  
  
##  <a name="cdcrendertarget"></a>CDCRenderTarget::CDCRenderTarget  
 构造 CDCRenderTarget 对象。  
  
```  
CDCRenderTarget();
```  
  
##  <a name="create"></a>CDCRenderTarget::Create  
 创建 CDCRenderTarget。  
  
```  
BOOL Create(const D2D1_RENDER_TARGET_PROPERTIES& props);
```  
  
### <a name="parameters"></a>参数  
 `props`  
 呈现模式、 像素格式、 远程处理选项、 DPI 信息和硬件呈现所需的最小 DirectX 支持中。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE。  
  
##  <a name="detach"></a>CDCRenderTarget::Detach  
 分离呈现器目标接口从该对象  
  
```  
ID2D1DCRenderTarget* Detach();
```  
  
### <a name="return-value"></a>返回值  
 指向分离呈现器目标接口。  
  
##  <a name="getdcrendertarget"></a>CDCRenderTarget::GetDCRenderTarget  
 返回 ID2D1DCRenderTarget 接口  
  
```  
ID2D1DCRenderTarget* GetDCRenderTarget();
```  
  
### <a name="return-value"></a>返回值  
 指向 ID2D1DCRenderTarget 接口或如果尚未初始化对象的 NULL 指针。  
  
##  <a name="m_pdcrendertarget"></a>CDCRenderTarget::m_pDCRenderTarget  
 指向 ID2D1DCRenderTarget 对象的指针。  
  
```  
ID2D1DCRenderTarget* m_pDCRenderTarget;  
```  
  
##  <a name="operator_id2d1dcrendertarget_star"></a>CDCRenderTarget::operator ID2D1DCRenderTarget *  
 返回 ID2D1DCRenderTarget 接口  
  
```  
operator ID2D1DCRenderTarget*();
```   
  
### <a name="return-value"></a>返回值  
 指向 ID2D1DCRenderTarget 接口或如果尚未初始化对象的 NULL 指针。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

