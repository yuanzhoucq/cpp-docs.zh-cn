---
title: CBaseKeyFrame 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CBaseKeyFrame [MFC], CBaseKeyFrame
- CBaseKeyFrame [MFC], AddToStoryboard
- CBaseKeyFrame [MFC], GetAnimationKeyframe
- CBaseKeyFrame [MFC], IsAdded
- CBaseKeyFrame [MFC], IsKeyframeAtOffset
- CBaseKeyFrame [MFC], m_bAdded
- CBaseKeyFrame [MFC], m_bIsKeyframeAtOffset
- CBaseKeyFrame [MFC], m_keyframe
ms.assetid: 285a2eff-e7c4-43be-b5aa-737727e6866d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3de348131dded63794e818d40c0ac5aeae910b03
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956702"
---
# <a name="cbasekeyframe-class"></a>CBaseKeyFrame 类
实现关键帧的基本功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CBaseKeyFrame : public CObject;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CBaseKeyFrame::CBaseKeyFrame](#cbasekeyframe)|构造一个关键帧对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CBaseKeyFrame::AddToStoryboard](#addtostoryboard)|添加关键帧的情节提要。|  
|[CBaseKeyFrame::GetAnimationKeyframe](#getanimationkeyframe)|返回基础的关键帧值。|  
|[CBaseKeyFrame::IsAdded](#isadded)|指示是否已添加关键帧的情节提要。|  
|[CBaseKeyFrame::IsKeyframeAtOffset](#iskeyframeatoffset)|指定是否应添加关键帧的偏移量或转换后的情节提要。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|name|描述|  
|----------|-----------------|  
|[CBaseKeyFrame::m_bAdded](#m_badded)|指定此关键帧是否已添加到情节提要。|  
|[CBaseKeyFrame::m_bIsKeyframeAtOffset](#m_biskeyframeatoffset)|指定是否应将此关键帧添加到情节提要从另一个现有的关键帧，偏移量处或末尾的某些转换。|  
|[CBaseKeyFrame::m_keyframe](#m_keyframe)|表示 Windows 动画 API 关键帧。 关键帧未初始化时就将它设置为预定义值 UI_ANIMATION_KEYFRAME_STORYBOARD_START 中。|  
  
## <a name="remarks"></a>备注  
 封装 UI_ANIMATION_KEYFRAME 变量。 用作任何关键帧实现的基类。 关键帧表示情节提要时刻，可以用于指定转换的开始和结束时间。 有两种类型的关键帧的关键帧添加到情节提要在指定的偏移量 （以时间表示） 或添加指定的转换后的关键帧。 不能在动画开始之前已知的某些转换的持续时间，因为只能在运行时确定某些关键帧的实际值。 关键帧可能取决于过渡，这反过来可以依赖于关键帧，因为很重要，以生成关键帧链时防止无限递归。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CBaseKeyFrame`  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="addtostoryboard"></a>  CBaseKeyFrame::AddToStoryboard  
 添加关键帧的情节提要。  
  
```  
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>参数  
 *pStoryboard*  
 指向情节提要的指针。  
  
 *bDeepAdd*  
 如果此参数为 TRUE，则所添加的关键帧依赖于某些其他关键帧或转换，此方法将尝试添加此关键帧或转换到第一次情节提要。  
  
### <a name="return-value"></a>返回值  
 如果关键帧已添加到情节提要成功，则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 调用此方法添加到情节提要的关键帧。  
  
##  <a name="cbasekeyframe"></a>  CBaseKeyFrame::CBaseKeyFrame  
 构造一个关键帧对象。  
  
```  
CBaseKeyFrame();
```  
  
##  <a name="getanimationkeyframe"></a>  CBaseKeyFrame::GetAnimationKeyframe  
 返回基础的关键帧值。  
  
```  
UI_ANIMATION_KEYFRAME GetAnimationKeyframe() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前关键帧。 默认值为 UI_ANIMATION_KEYFRAME_STORYBOARD_START。  
  
### <a name="remarks"></a>备注  
 这是对基础的关键帧值的访问器。  
  
##  <a name="isadded"></a>  CBaseKeyFrame::IsAdded  
 指示是否已添加关键帧的情节提要。  
  
```  
BOOL IsAdded() const;  
```  
  
### <a name="return-value"></a>返回值  
 关键帧添加到情节提要; 如果为 TRUEotehrwise FALSE。  
  
### <a name="remarks"></a>备注  
 基类中 IsAdded 始终返回 TRUE，但它在派生类中重写。  
  
##  <a name="iskeyframeatoffset"></a>  CBaseKeyFrame::IsKeyframeAtOffset  
 指定是否应添加关键帧的偏移量或转换后的情节提要。  
  
```  
BOOL IsKeyframeAtOffset() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果该关键帧应添加到情节提要某些指定的偏移量处，则为 TRUE。 如果该关键帧应添加一些转换后的情节提要，则为 FALSE。  
  
### <a name="remarks"></a>备注  
 指定是否应将关键帧添加到情节提要偏移量的位置。 必须在派生类中指定的偏移量或转换。  
  
##  <a name="m_badded"></a>  CBaseKeyFrame::m_bAdded  
 指定此关键帧是否已添加到情节提要。  
  
```  
BOOL m_bAdded;  
```  
  
##  <a name="m_biskeyframeatoffset"></a>  CBaseKeyFrame::m_bIsKeyframeAtOffset  
 指定是否应将此关键帧添加到情节提要从另一个现有的关键帧，偏移量处或末尾的某些转换。  
  
```  
BOOL m_bIsKeyframeAtOffset;  
```  
  
##  <a name="m_keyframe"></a>  CBaseKeyFrame::m_keyframe  
 表示 Windows 动画 API 关键帧。 关键帧未初始化时就将它设置为预定义值 UI_ANIMATION_KEYFRAME_STORYBOARD_START 中。  
  
```  
UI_ANIMATION_KEYFRAME m_keyframe;  
```  
  
## <a name="see-also"></a>请参阅  
 [类](../../mfc/reference/mfc-classes.md)
