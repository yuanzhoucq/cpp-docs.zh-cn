---
title: "CKeyFrame 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- afxanimationcontroller/CKeyFrame
- CKeyFrame
dev_langs:
- C++
helpviewer_keywords:
- CKeyFrame class
ms.assetid: d050a562-20f6-4c65-8ce5-ccb3aef1a20e
caps.latest.revision: 18
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: d8ecff2e36148fb114ee708712b6e8bd0fe558ed
ms.lasthandoff: 02/24/2017

---
# <a name="ckeyframe-class"></a>CKeyFrame 类
表示动画关键帧。  
  
## <a name="syntax"></a>语法  
  
```  
class CKeyFrame : public CBaseKeyFrame;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CKeyFrame::CKeyFrame](#ckeyframe)|已重载。 构造一个取决于其他关键帧的关键帧。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CKeyFrame::AddToStoryboard](#addtostoryboard)|添加到情节提要的一个关键帧。 (重写[CBaseKeyFrame::AddToStoryboard](../../mfc/reference/cbasekeyframe-class.md#addtostoryboard)。)|  
|[CKeyFrame::AddToStoryboardAfterTransition](#addtostoryboardaftertransition)|添加关键帧，以转换后的情节提要。|  
|[CKeyFrame::AddToStoryboardAtOffset](#addtostoryboardatoffset)|将添加到情节提要偏移量处的关键帧。|  
|[CKeyFrame::GetExistingKeyframe](#getexistingkeyframe)|返回指向此关键帧依赖的关键帧的指针。|  
|[CKeyFrame::GetOffset](#getoffset)|从其他关键帧返回某一偏移量。|  
|[CKeyFrame::GetTransition](#gettransition)|返回到转换取决于此关键帧的指针。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CKeyFrame::m_offset](#m_offset)|指定从存储在 m_pExistingKeyFrame 一个关键帧此关键帧的偏移量。|  
|[CKeyFrame::m_pExistingKeyFrame](#m_pexistingkeyframe)|存储指向现有关键帧的指针。 此关键帧添加到现有关键帧 m_offset 的情节提要。|  
|[CKeyFrame::m_pTransition](#m_ptransition)|存储在此关键帧处开始的过渡的指针。|  
  
## <a name="remarks"></a>备注  
 此类实现动画关键帧。 关键帧表示情节提要的时间中的某一刻，并可以用于指定转换的开始和结束时间。 关键帧可能基于其他关键帧和具有偏移量 （以秒为单位），或可能根据转换并且表示某一时刻这一转换的结束的时间。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseKeyFrame](../../mfc/reference/cbasekeyframe-class.md)  
  
 [CKeyFrame](../../mfc/reference/ckeyframe-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="a-nameaddtostoryboarda--ckeyframeaddtostoryboard"></a><a name="addtostoryboard"></a>CKeyFrame::AddToStoryboard  
 添加到情节提要的一个关键帧。  
  
```  
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>参数  
 `pStoryboard`  
 指向一个情节提要的指针。  
  
 `bDeepAdd`  
 指定是否要添加关键帧或转换以递归方式。  
  
### <a name="return-value"></a>返回值  
 如果为 TRUE，已成功添加关键帧。  
  
### <a name="remarks"></a>备注  
 此方法添加到情节提要的关键帧。 如果这取决于其他关键帧或转换，并且 bDeepAdd 为 TRUE，此方法将尝试以递归方式添加它们。  
  
##  <a name="a-nameaddtostoryboardaftertransitiona--ckeyframeaddtostoryboardaftertransition"></a><a name="addtostoryboardaftertransition"></a>CKeyFrame::AddToStoryboardAfterTransition  
 添加关键帧，以转换后的情节提要。  
  
```  
BOOL AddToStoryboardAfterTransition(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>参数  
 `pStoryboard`  
 指向一个情节提要的指针。  
  
 `bDeepAdd`  
 指定是否转换以递归方式添加。  
  
### <a name="return-value"></a>返回值  
 如果为 TRUE，已成功添加关键帧。  
  
### <a name="remarks"></a>备注  
 此函数是由框架调用以添加关键帧转换后的情节提要。  
  
##  <a name="a-nameaddtostoryboardatoffseta--ckeyframeaddtostoryboardatoffset"></a><a name="addtostoryboardatoffset"></a>CKeyFrame::AddToStoryboardAtOffset  
 将添加到情节提要偏移量处的关键帧。  
  
```  
virtual BOOL AddToStoryboardAtOffset(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>参数  
 `pStoryboard`  
 指向一个情节提要的指针。  
  
 `bDeepAdd`  
 指定是否要添加关键帧此关键帧依赖以递归方式。  
  
### <a name="return-value"></a>返回值  
 如果为 TRUE，已成功添加关键帧。  
  
### <a name="remarks"></a>备注  
 要添加到情节提要偏移量处的关键帧的框架调用此函数。  
  
##  <a name="a-nameckeyframea--ckeyframeckeyframe"></a><a name="ckeyframe"></a>CKeyFrame::CKeyFrame  
 构造一个取决于转换的关键帧。  
  
```  
CKeyFrame(CBaseTransition* pTransition);

 
CKeyFrame(
    CBaseKeyFrame* pKeyframe,  
    UI_ANIMATION_SECONDS offset = 0.0);
```  
  
### <a name="parameters"></a>参数  
 `pTransition`  
 转换指针。  
  
 `pKeyframe`  
 指向关键帧的指针。  
  
 `offset`  
 偏移量，以秒为单位，从 pKeyframe 由指定的关键帧。  
  
### <a name="remarks"></a>备注  
 指定的转换结束时，构造的关键帧将表示某个时刻情节提要。  
  
##  <a name="a-namegetexistingkeyframea--ckeyframegetexistingkeyframe"></a><a name="getexistingkeyframe"></a>CKeyFrame::GetExistingKeyframe  
 返回指向此关键帧依赖的关键帧的指针。  
  
```  
CBaseKeyFrame* GetExistingKeyframe();
```  
  
### <a name="return-value"></a>返回值  
 指向关键帧，则为 NULL，如果此关键帧不依赖于其他关键帧的有效指针。  
  
### <a name="remarks"></a>备注  
 这是对此关键帧依赖的关键帧的访问器。  
  
##  <a name="a-namegetoffseta--ckeyframegetoffset"></a><a name="getoffset"></a>CKeyFrame::GetOffset  
 从其他关键帧返回某一偏移量。  
  
```  
UI_ANIMATION_SECONDS GetOffset();
```  
  
### <a name="return-value"></a>返回值  
 以秒为单位，从其他关键帧的偏移量。  
  
### <a name="remarks"></a>备注  
 应调用此方法来确定其他关键帧之后的秒数中的偏移量。  
  
##  <a name="a-namegettransitiona--ckeyframegettransition"></a><a name="gettransition"></a>CKeyFrame::GetTransition  
 返回到转换取决于此关键帧的指针。  
  
```  
CBaseTransition* GetTransition();
```  
  
### <a name="return-value"></a>返回值  
 指向转换，则为 NULL，如果此关键帧不依赖于转换的有效指针。  
  
### <a name="remarks"></a>备注  
 这是对转换取决于此关键帧的访问器。  
  
##  <a name="a-namemoffseta--ckeyframemoffset"></a><a name="m_offset"></a>CKeyFrame::m_offset  
 指定从存储在 m_pExistingKeyFrame 一个关键帧此关键帧的偏移量。  
  
```  
UI_ANIMATION_SECONDS m_offset;  
```  
  
##  <a name="a-namempexistingkeyframea--ckeyframempexistingkeyframe"></a><a name="m_pexistingkeyframe"></a>CKeyFrame::m_pExistingKeyFrame  
 存储指向现有关键帧的指针。 此关键帧添加到现有关键帧 m_offset 的情节提要。  
  
```  
CBaseKeyFrame* m_pExistingKeyFrame;  
```  
  
##  <a name="a-namemptransitiona--ckeyframemptransition"></a><a name="m_ptransition"></a>CKeyFrame::m_pTransition  
 存储在此关键帧处开始的过渡的指针。  
  
```  
CBaseTransition* m_pTransition;  
```  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

