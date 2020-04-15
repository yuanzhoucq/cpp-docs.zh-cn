---
title: CBaseKeyFrame 类
ms.date: 11/04/2016
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
ms.openlocfilehash: 3fcd55f6a157f4b837090a3608fb509b870aae5d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352989"
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
|[CBaseKey框架：C基键框架](#cbasekeyframe)|构造关键帧对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CBaseKeyFrame：：添加故事板](#addtostoryboard)|将关键帧添加到情节提要。|
|[CBase键框：获取动画关键帧](#getanimationkeyframe)|返回基础关键帧值。|
|[CBaseKey框架：已添加](#isadded)|告诉是否已将关键帧添加到情节提要中。|
|[CBaseKey框架：是关键帧帧偏移](#iskeyframeatoffset)|指定关键帧是否应在偏移时或过渡后添加到情节提要。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CBaseKey框架：：m_bAdded](#m_badded)|指定此关键帧是否已添加到情节提要。|
|[CBaseKeyFrame：m_bIsKeyframeAtOffset](#m_biskeyframeatoffset)|指定是否应将此关键帧添加到与另一个现有关键帧偏移量或某些转换结束时的情节提要。|
|[CBaseKeyFrame：m_keyframe](#m_keyframe)|表示 Windows 动画 API 关键帧。 未初始化关键帧时，它将设置为预定义值UI_ANIMATION_KEYFRAME_STORYBOARD_START。|

## <a name="remarks"></a>备注

封装UI_ANIMATION_KEYFRAME变量。 用作任何关键帧实现的基类。 关键帧表示情节提要中的一个时刻，可用于指定过渡的开始和结束时间。 有两种类型的关键帧 - 在指定的偏移量（时间）添加到情节提要的关键帧，或指定转换后添加的关键帧。 由于某些转换的持续时间在动画启动之前无法知道，因此某些关键帧的实际值仅在运行时确定。 由于关键帧可能依赖于过渡（而过渡又取决于关键帧，因此在构建关键帧链时防止无限递归非常重要。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CBaseKeyFrame`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="cbasekeyframeaddtostoryboard"></a><a name="addtostoryboard"></a>CBaseKeyFrame：：添加故事板

将关键帧添加到情节提要。

```
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>参数

*板*<br/>
指向情节提要的指针。

*bDeepAdd*<br/>
如果此参数为 TRUE，并且要添加的关键帧取决于其他关键帧或转换，则此方法将尝试先添加此关键帧或转换为情节提要。

### <a name="return-value"></a>返回值

如果关键帧已成功添加到情节提要，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

调用此方法是为了向情节提要添加关键帧。

## <a name="cbasekeyframecbasekeyframe"></a><a name="cbasekeyframe"></a>CBaseKey框架：C基键框架

构造关键帧对象。

```
CBaseKeyFrame();
```

## <a name="cbasekeyframegetanimationkeyframe"></a><a name="getanimationkeyframe"></a>CBase键框：获取动画关键帧

返回基础关键帧值。

```
UI_ANIMATION_KEYFRAME GetAnimationKeyframe() const;
```

### <a name="return-value"></a>返回值

当前关键帧。 默认值为UI_ANIMATION_KEYFRAME_STORYBOARD_START。

### <a name="remarks"></a>备注

这是对基础关键帧值的访问器。

## <a name="cbasekeyframeisadded"></a><a name="isadded"></a>CBaseKey框架：已添加

告诉是否已将关键帧添加到情节提要中。

```
BOOL IsAdded() const;
```

### <a name="return-value"></a>返回值

如果关键帧已添加到情节提要，则为 TRUE;奥特威斯·法尔。

### <a name="remarks"></a>备注

在基类 Is添加中始终返回 TRUE，但在派生类中重写 TRUE。

## <a name="cbasekeyframeiskeyframeatoffset"></a><a name="iskeyframeatoffset"></a>CBaseKey框架：是关键帧帧偏移

指定关键帧是否应在偏移时或过渡后添加到情节提要。

```
BOOL IsKeyframeAtOffset() const;
```

### <a name="return-value"></a>返回值

如果关键帧应添加到情节提要，在某些指定的偏移量。 如果关键帧应在一些转换后添加到情节提要中，则 FALSE。

### <a name="remarks"></a>备注

指定是否应在偏移量下将关键帧添加到情节提要。 偏移量或过渡必须在派生类中指定。

## <a name="cbasekeyframem_badded"></a><a name="m_badded"></a>CBaseKey框架：：m_bAdded

指定此关键帧是否已添加到情节提要。

```
BOOL m_bAdded;
```

## <a name="cbasekeyframem_biskeyframeatoffset"></a><a name="m_biskeyframeatoffset"></a>CBaseKeyFrame：m_bIsKeyframeAtOffset

指定是否应将此关键帧添加到与另一个现有关键帧偏移量或某些转换结束时的情节提要。

```
BOOL m_bIsKeyframeAtOffset;
```

## <a name="cbasekeyframem_keyframe"></a><a name="m_keyframe"></a>CBaseKeyFrame：m_keyframe

表示 Windows 动画 API 关键帧。 未初始化关键帧时，它将设置为预定义值UI_ANIMATION_KEYFRAME_STORYBOARD_START。

```
UI_ANIMATION_KEYFRAME m_keyframe;
```

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
