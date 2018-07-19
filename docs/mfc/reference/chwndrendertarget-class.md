---
title: CHwndRenderTarget 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::Attach
- AFXRENDERTARGET/CHwndRenderTarget::CheckWindowState
- AFXRENDERTARGET/CHwndRenderTarget::Create
- AFXRENDERTARGET/CHwndRenderTarget::Detach
- AFXRENDERTARGET/CHwndRenderTarget::GetHwnd
- AFXRENDERTARGET/CHwndRenderTarget::GetHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::ReCreate
- AFXRENDERTARGET/CHwndRenderTarget::Resize
- AFXRENDERTARGET/CHwndRenderTarget::m_pHwndRenderTarget
dev_langs:
- C++
helpviewer_keywords:
- CHwndRenderTarget [MFC], CHwndRenderTarget
- CHwndRenderTarget [MFC], Attach
- CHwndRenderTarget [MFC], CheckWindowState
- CHwndRenderTarget [MFC], Create
- CHwndRenderTarget [MFC], Detach
- CHwndRenderTarget [MFC], GetHwnd
- CHwndRenderTarget [MFC], GetHwndRenderTarget
- CHwndRenderTarget [MFC], ReCreate
- CHwndRenderTarget [MFC], Resize
- CHwndRenderTarget [MFC], m_pHwndRenderTarget
ms.assetid: aa65b69f-7202-46ea-af81-ef325da0b840
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0e0962d4a0c97db27f7d5ae31ec58eb26f20a7f7
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038388"
---
# <a name="chwndrendertarget-class"></a>CHwndRenderTarget 类
ID2D1HwndRenderTarget 包装器。  
  
## <a name="syntax"></a>语法  
  
```  
class CHwndRenderTarget : public CRenderTarget;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CHwndRenderTarget::CHwndRenderTarget](#chwndrendertarget)|构造 CHwndRenderTarget 对象与 HWND。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CHwndRenderTarget::Attach](#attach)|附加现有呈现器对对象的目标接口|  
|[CHwndRenderTarget::CheckWindowState](#checkwindowstate)|指示是否封闭关联与此呈现器目标的 HWND。|  
|[CHwndRenderTarget::Create](#create)|创建与窗口关联的呈现器目标|  
|[CHwndRenderTarget::Detach](#detach)|分离呈现器目标接口从该对象|  
|[CHwndRenderTarget::GetHwnd](#gethwnd)|返回与此关联的 HWND 呈现器目标。|  
|[CHwndRenderTarget::GetHwndRenderTarget](#gethwndrendertarget)|返回 ID2D1HwndRenderTarget 接口。|  
|[CHwndRenderTarget::ReCreate](#recreate)|重新创建的窗口相关联的呈现器目标|  
|[CHwndRenderTarget::Resize](#resize)|呈现器目标的大小更改为指定的像素大小|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CHwndRenderTarget::operator ID2D1HwndRenderTarget *](#operator_id2d1hwndrendertarget_star)|返回 ID2D1HwndRenderTarget 接口。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|name|描述|  
|----------|-----------------|  
|[CHwndRenderTarget::m_pHwndRenderTarget](#m_phwndrendertarget)|指向 ID2D1HwndRenderTarget 对象的指针。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
 [CHwndRenderTarget](../../mfc/reference/chwndrendertarget-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxrendertarget.h  
  
##  <a name="attach"></a>  CHwndRenderTarget::Attach  
 附加现有呈现器对对象的目标接口  
  
```  
void Attach(ID2D1HwndRenderTarget* pTarget);
```  
  
### <a name="parameters"></a>参数  
 *pTarget*  
 现有呈现器目标接口。 不能为 NULL  
  
##  <a name="checkwindowstate"></a>  CHwndRenderTarget::CheckWindowState  
 指示是否封闭关联与此呈现器目标的 HWND。  
  
```  
D2D1_WINDOW_STATE CheckWindowState() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个值，该值指示与此关联的 HWND 是否呈现目标被封闭。  
  
##  <a name="chwndrendertarget"></a>  CHwndRenderTarget::CHwndRenderTarget  
 构造 CHwndRenderTarget 对象与 HWND。  
  
```  
CHwndRenderTarget(HWND hwnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 *hwnd*  
 与此关联的 HWND 呈现器目标  
  
##  <a name="create"></a>  CHwndRenderTarget::Create  
 创建与窗口关联的呈现器目标  
  
```  
BOOL Create(HWND hWnd);
```  
  
### <a name="parameters"></a>参数  
 *hWnd*  
 与此关联的 HWND 呈现器目标  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE  
  
##  <a name="detach"></a>  CHwndRenderTarget::Detach  
 分离呈现器目标接口从该对象  
  
```  
ID2D1HwndRenderTarget* Detach();
```  
  
### <a name="return-value"></a>返回值  
 指向分离呈现器目标接口。  
  
##  <a name="gethwnd"></a>  CHwndRenderTarget::GetHwnd  
 返回与此关联的 HWND 呈现器目标。  
  
```  
HWND GetHwnd() const;  
```  
  
### <a name="return-value"></a>返回值  
 与此关联的 HWND 呈现器目标。  
  
##  <a name="gethwndrendertarget"></a>  CHwndRenderTarget::GetHwndRenderTarget  
 返回 ID2D1HwndRenderTarget 接口。  
  
```  
ID2D1HwndRenderTarget* GetHwndRenderTarget();
```  
  
### <a name="return-value"></a>返回值  
 指向 ID2D1HwndRenderTarget 接口或如果尚未初始化对象的 NULL 指针。  
  
##  <a name="m_phwndrendertarget"></a>  CHwndRenderTarget::m_pHwndRenderTarget  
 指向 ID2D1HwndRenderTarget 对象的指针。  
  
```  
ID2D1HwndRenderTarget* m_pHwndRenderTarget;  
```  
  
##  <a name="operator_id2d1hwndrendertarget_star"></a>  CHwndRenderTarget::operator ID2D1HwndRenderTarget *  
 返回 ID2D1HwndRenderTarget 接口。  
  
```  
operator ID2D1HwndRenderTarget*();
```   
  
### <a name="return-value"></a>返回值  
 指向 ID2D1HwndRenderTarget 接口或如果尚未初始化对象的 NULL 指针。  
  
##  <a name="recreate"></a>  CHwndRenderTarget::ReCreate  
 重新创建的窗口相关联的呈现器目标  
  
```  
BOOL ReCreate(HWND hWnd);
```  
  
### <a name="parameters"></a>参数  
 *hWnd*  
 与此关联的 HWND 呈现器目标  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE。  
  
##  <a name="resize"></a>  CHwndRenderTarget::Resize  
 呈现器目标的大小更改为指定的像素大小  
  
```  
BOOL Resize(const CD2DSizeU& size);
```  
  
### <a name="parameters"></a>参数  
 *size*  
 以设备像素为单位的呈现器目标的新的大小  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE。  
  
## <a name="see-also"></a>请参阅  
 [类](../../mfc/reference/mfc-classes.md)
