---
title: "CKeyFrame 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboard
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboardAfterTransition
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboardAtOffset
- AFXANIMATIONCONTROLLER/CKeyFrame::GetExistingKeyframe
- AFXANIMATIONCONTROLLER/CKeyFrame::GetOffset
- AFXANIMATIONCONTROLLER/CKeyFrame::GetTransition
- AFXANIMATIONCONTROLLER/CKeyFrame::m_offset
- AFXANIMATIONCONTROLLER/CKeyFrame::m_pExistingKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::m_pTransition
dev_langs:
- C++
helpviewer_keywords:
- CKeyFrame [MFC], CKeyFrame
- CKeyFrame [MFC], AddToStoryboard
- CKeyFrame [MFC], AddToStoryboardAfterTransition
- CKeyFrame [MFC], AddToStoryboardAtOffset
- CKeyFrame [MFC], GetExistingKeyframe
- CKeyFrame [MFC], GetOffset
- CKeyFrame [MFC], GetTransition
- CKeyFrame [MFC], m_offset
- CKeyFrame [MFC], m_pExistingKeyFrame
- CKeyFrame [MFC], m_pTransition
ms.assetid: d050a562-20f6-4c65-8ce5-ccb3aef1a20e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 03cfc0766dd15a2762612cf5f41e72ffb1c1885f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ckeyframe-class"></a>CKeyFrame 类
表示动画关键帧。  
  
## <a name="syntax"></a>语法  
  
```  
class CKeyFrame : public CBaseKeyFrame;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CKeyFrame::CKeyFrame](#ckeyframe)|已重载。 构造取决于其他关键帧的关键帧。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CKeyFrame::AddToStoryboard](#addtostoryboard)|将关键帧添加到情节提要。 (重写[CBaseKeyFrame::AddToStoryboard](../../mfc/reference/cbasekeyframe-class.md#addtostoryboard)。)|  
|[CKeyFrame::AddToStoryboardAfterTransition](#addtostoryboardaftertransition)|添加关键帧转换后的情节提要。|  
|[CKeyFrame::AddToStoryboardAtOffset](#addtostoryboardatoffset)|将添加到情节提要偏移量的一个关键帧。|  
|[CKeyFrame::GetExistingKeyframe](#getexistingkeyframe)|返回指向此关键帧依赖的关键帧的指针。|  
|[CKeyFrame::GetOffset](#getoffset)|返回从其他关键帧的偏移量。|  
|[CKeyFrame::GetTransition](#gettransition)|将指针返回到转换取决于此关键帧。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|name|描述|  
|----------|-----------------|  
|[CKeyFrame::m_offset](#m_offset)|指定此关键帧从存储在 m_pExistingKeyFrame 关键帧的偏移量。|  
|[CKeyFrame::m_pExistingKeyFrame](#m_pexistingkeyframe)|将存储指向现有关键帧的指针的指针。 此关键帧添加到与现有的关键帧的 m_offset 情节提要。|  
|[CKeyFrame::m_pTransition](#m_ptransition)|存储指向匹配位置始于此关键帧的过渡。|  
  
## <a name="remarks"></a>备注  
 此类实现动画关键帧。 关键帧表示情节提要时刻，可以用于指定转换的开始和结束时间。 关键帧可能基于其他关键帧和具有相对的偏移量 （以秒为单位），或可能根据转换并且表示在此转换的结束的时间的一段时间。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseKeyFrame](../../mfc/reference/cbasekeyframe-class.md)  
  
 [CKeyFrame](../../mfc/reference/ckeyframe-class.md)  
  
## <a name="requirements"></a>惠?  
 **标头：** afxanimationcontroller.h  
  
##  <a name="addtostoryboard"></a>CKeyFrame::AddToStoryboard  
 将关键帧添加到情节提要。  
  
```  
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>参数  
 `pStoryboard`  
 指向情节提要的指针。  
  
 `bDeepAdd`  
 指定是否添加关键帧或转换以递归方式。  
  
### <a name="return-value"></a>返回值  
 为 TRUE，如果已成功添加关键帧。  
  
### <a name="remarks"></a>备注  
 此方法将添加到情节提要的关键帧。 如果它依赖于其他关键帧或转换和 bDeepAdd 为 TRUE，此方法会尝试以递归方式添加它们。  
  
##  <a name="addtostoryboardaftertransition"></a>CKeyFrame::AddToStoryboardAfterTransition  
 添加关键帧转换后的情节提要。  
  
```  
BOOL AddToStoryboardAfterTransition(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>参数  
 `pStoryboard`  
 指向情节提要的指针。  
  
 `bDeepAdd`  
 指定是否转换以递归方式添加。  
  
### <a name="return-value"></a>返回值  
 为 TRUE，如果已成功添加关键帧。  
  
### <a name="remarks"></a>备注  
 由框架添加关键帧转换后的情节提要调用此函数。  
  
##  <a name="addtostoryboardatoffset"></a>CKeyFrame::AddToStoryboardAtOffset  
 将添加到情节提要偏移量的一个关键帧。  
  
```  
virtual BOOL AddToStoryboardAtOffset(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>参数  
 `pStoryboard`  
 指向情节提要的指针。  
  
 `bDeepAdd`  
 指定是否要添加关键帧此关键帧依赖于以递归方式。  
  
### <a name="return-value"></a>返回值  
 为 TRUE，如果已成功添加关键帧。  
  
### <a name="remarks"></a>备注  
 要添加到情节提要偏移量的一个关键帧的框架通过调用此函数。  
  
##  <a name="ckeyframe"></a>CKeyFrame::CKeyFrame  
 构造取决于过渡的关键帧。  
  
```  
CKeyFrame(CBaseTransition* pTransition);

 
CKeyFrame(
    CBaseKeyFrame* pKeyframe,  
    UI_ANIMATION_SECONDS offset = 0.0);
```  
  
### <a name="parameters"></a>参数  
 `pTransition`  
 指向过渡的指针。  
  
 `pKeyframe`  
 指向关键帧的指针。  
  
 `offset`  
 偏移量，以秒为单位，从由 pKeyframe 指定的关键帧。  
  
### <a name="remarks"></a>备注  
 指定的转换结束时，构造的关键帧将表示一段时间内的情节提要。  
  
##  <a name="getexistingkeyframe"></a>CKeyFrame::GetExistingKeyframe  
 返回指向此关键帧依赖的关键帧的指针。  
  
```  
CBaseKeyFrame* GetExistingKeyframe();
```  
  
### <a name="return-value"></a>返回值  
 指向关键帧，则为 NULL，如果此关键帧不依赖于其他关键帧的有效指针。  
  
### <a name="remarks"></a>备注  
 这是对依赖此关键帧的关键帧的访问器。  
  
##  <a name="getoffset"></a>CKeyFrame::GetOffset  
 返回从其他关键帧的偏移量。  
  
```  
UI_ANIMATION_SECONDS GetOffset();
```  
  
### <a name="return-value"></a>返回值  
 以秒为单位，从其他关键帧的偏移量。  
  
### <a name="remarks"></a>备注  
 应调用此方法，以确定以秒为单位，从其他关键帧的偏移量。  
  
##  <a name="gettransition"></a>CKeyFrame::GetTransition  
 将指针返回到转换取决于此关键帧。  
  
```  
CBaseTransition* GetTransition();
```  
  
### <a name="return-value"></a>返回值  
 指向转换，则为 NULL，如果此关键帧不依赖于转换的有效指针。  
  
### <a name="remarks"></a>备注  
 这是对转换取决于此关键帧的访问器。  
  
##  <a name="m_offset"></a>CKeyFrame::m_offset  
 指定此关键帧从存储在 m_pExistingKeyFrame 关键帧的偏移量。  
  
```  
UI_ANIMATION_SECONDS m_offset;  
```  
  
##  <a name="m_pexistingkeyframe"></a>CKeyFrame::m_pExistingKeyFrame  
 将存储指向现有关键帧的指针的指针。 此关键帧添加到与现有的关键帧的 m_offset 情节提要。  
  
```  
CBaseKeyFrame* m_pExistingKeyFrame;  
```  
  
##  <a name="m_ptransition"></a>CKeyFrame::m_pTransition  
 存储指向匹配位置始于此关键帧的过渡。  
  
```  
CBaseTransition* m_pTransition;  
```  
  
## <a name="see-also"></a>请参阅  
 [类](../../mfc/reference/mfc-classes.md)
