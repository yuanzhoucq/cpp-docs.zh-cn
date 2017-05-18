---
title: "CBaseKeyFrame 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::AddToStoryboard
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::GetAnimationKeyframe
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::IsAdded
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::IsKeyframeAtOffset
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_bAdded
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_bIsKeyframeAtOffset
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_keyframe
dev_langs:
- C++
helpviewer_keywords:
- CBaseKeyFrame class
ms.assetid: 285a2eff-e7c4-43be-b5aa-737727e6866d
caps.latest.revision: 17
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: cfbaac379097c89b5dcb52fa36c0cd1f6e3d2c7f
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cbasekeyframe-class"></a>CBaseKeyFrame 类
实现关键帧的基本功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CBaseKeyFrame : public CObject;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CBaseKeyFrame::CBaseKeyFrame](#cbasekeyframe)|构造一个关键帧对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CBaseKeyFrame::AddToStoryboard](#addtostoryboard)|将添加到情节提要的关键帧。|  
|[CBaseKeyFrame::GetAnimationKeyframe](#getanimationkeyframe)|返回基础的关键帧值。|  
|[CBaseKeyFrame::IsAdded](#isadded)|指示是否已添加关键帧的情节提要。|  
|[CBaseKeyFrame::IsKeyframeAtOffset](#iskeyframeatoffset)|指定是否应将该关键帧添加到情节提要的偏移量或转换之后。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CBaseKeyFrame::m_bAdded](#m_badded)|指定此关键帧是否已添加到情节提要。|  
|[CBaseKeyFrame::m_bIsKeyframeAtOffset](#m_biskeyframeatoffset)|指定是否应将此关键帧添加到情节提要与另一个现有关键帧的偏移量处或末尾的某些转换。|  
|[CBaseKeyFrame::m_keyframe](#m_keyframe)|表示 Windows 动画 API 关键帧。 未初始化关键帧时它被设置为 UI_ANIMATION_KEYFRAME_STORYBOARD_START 的预定义值。|  
  
## <a name="remarks"></a>备注  
 封装 UI_ANIMATION_KEYFRAME 变量。 作为任何关键帧实现的基类。 关键帧表示情节提要的时间中的某一刻，并可以用于指定转换的开始和结束时间。 有两种类型的关键帧的关键帧添加到情节提要指定偏移量 （以时间） 或在指定的转换之后添加关键帧。 因为某些过渡的持续时间不能知道在动画开始之前，只能在运行时确定某些关键帧的实际值。 因为关键帧可能依赖于过渡，这反过来依赖于关键帧，很重要，在生成关键帧链时防止无限递归。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CBaseKeyFrame`  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="addtostoryboard"></a>CBaseKeyFrame::AddToStoryboard  
 将添加到情节提要的关键帧。  
  
```  
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>参数  
 `pStoryboard`  
 指向一个情节提要的指针。  
  
 `bDeepAdd`  
 如果此参数为 TRUE，但要添加的关键帧依赖于某些其他关键帧或过渡，此方法将尝试添加此关键帧或转换到第一次情节提要。  
  
### <a name="return-value"></a>返回值  
 如果关键帧已添加到情节提要成功，则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 调用此方法来添加关键帧的情节提要。  
  
##  <a name="cbasekeyframe"></a>CBaseKeyFrame::CBaseKeyFrame  
 构造一个关键帧对象。  
  
```  
CBaseKeyFrame();
```  
  
##  <a name="getanimationkeyframe"></a>CBaseKeyFrame::GetAnimationKeyframe  
 返回基础的关键帧值。  
  
```  
UI_ANIMATION_KEYFRAME GetAnimationKeyframe() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前的关键帧。 默认值为 UI_ANIMATION_KEYFRAME_STORYBOARD_START。  
  
### <a name="remarks"></a>备注  
 这是对基础的关键帧值的访问器。  
  
##  <a name="isadded"></a>CBaseKeyFrame::IsAdded  
 指示是否已添加关键帧的情节提要。  
  
```  
BOOL IsAdded() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果一个关键帧添加到情节提要; 则为 TRUE则 FALSE。  
  
### <a name="remarks"></a>备注  
 在基类中 IsAdded 始终返回 TRUE，但在派生类中重写。  
  
##  <a name="iskeyframeatoffset"></a>CBaseKeyFrame::IsKeyframeAtOffset  
 指定是否应将该关键帧添加到情节提要的偏移量或转换之后。  
  
```  
BOOL IsKeyframeAtOffset() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果该关键帧应添加到情节提要中某些指定的偏移位置，则为 TRUE。 如果该关键帧应添加到情节提要一些转换后，则为 FALSE。  
  
### <a name="remarks"></a>备注  
 指定是否应将该关键帧添加到情节提要偏移量处。 必须在派生类中指定的偏移量或转换。  
  
##  <a name="m_badded"></a>CBaseKeyFrame::m_bAdded  
 指定此关键帧是否已添加到情节提要。  
  
```  
BOOL m_bAdded;  
```  
  
##  <a name="m_biskeyframeatoffset"></a>CBaseKeyFrame::m_bIsKeyframeAtOffset  
 指定是否应将此关键帧添加到情节提要与另一个现有关键帧的偏移量处或末尾的某些转换。  
  
```  
BOOL m_bIsKeyframeAtOffset;  
```  
  
##  <a name="m_keyframe"></a>CBaseKeyFrame::m_keyframe  
 表示 Windows 动画 API 关键帧。 未初始化关键帧时它被设置为 UI_ANIMATION_KEYFRAME_STORYBOARD_START 的预定义值。  
  
```  
UI_ANIMATION_KEYFRAME m_keyframe;  
```  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

