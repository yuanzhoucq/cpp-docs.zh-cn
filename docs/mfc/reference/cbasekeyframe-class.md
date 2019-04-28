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
ms.openlocfilehash: d36c924d30bd728fcd54b6cdf6805ade25e20b5c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62218396"
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
|[CBaseKeyFrame::IsKeyframeAtOffset](#iskeyframeatoffset)|指定是否应添加关键帧偏移量，或转换后的情节提要。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CBaseKeyFrame::m_bAdded](#m_badded)|指定此关键帧是否已添加到情节提要。|
|[CBaseKeyFrame::m_bIsKeyframeAtOffset](#m_biskeyframeatoffset)|指定是否应将此关键帧添加到情节提要另一个现有关键帧偏移量位置处或末尾的某些转换。|
|[CBaseKeyFrame::m_keyframe](#m_keyframe)|表示 Windows 动画 API 关键帧。 关键帧未初始化时将它设置为预定义值 UI_ANIMATION_KEYFRAME_STORYBOARD_START。|

## <a name="remarks"></a>备注

封装 UI_ANIMATION_KEYFRAME 变量。 用作任何关键帧实现的基类。 关键帧表示情节提要中的某个时刻，并可用于指定转换的开始和结束时间。 有两种类型的关键帧的关键帧添加到情节提要按指定的偏移量 （以时间表示） 或指定转换后添加关键帧。 不能在动画开始之前已知的某些转换的持续时间，因为某些关键帧的实际值是在仅限运行时确定。 关键帧可能取决于过渡，这反过来依赖于关键帧，因为很重要，可生成关键帧链时防止无限递归。

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

*pStoryboard*<br/>
指向情节提要的指针。

*bDeepAdd*<br/>
如果此参数为 TRUE，并且要添加的关键帧取决于一些其他关键帧或转换，此方法将尝试添加此关键帧或转换到情节提要第一次。

### <a name="return-value"></a>返回值

如果关键帧已添加到情节提要成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

调用此方法以添加关键帧的情节提要。

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

如果关键帧添加到情节提要; 则为 TRUE则 FALSE。

### <a name="remarks"></a>备注

基类中 IsAdded 始终返回 TRUE，但在派生类中重写。

##  <a name="iskeyframeatoffset"></a>  CBaseKeyFrame::IsKeyframeAtOffset

指定是否应添加关键帧偏移量，或转换后的情节提要。

```
BOOL IsKeyframeAtOffset() const;
```

### <a name="return-value"></a>返回值

如果该关键帧应添加到情节提要按某些指定的偏移量，则为 TRUE。 如果该关键帧应添加一些转换后的情节提要，则为 FALSE。

### <a name="remarks"></a>备注

指定是否应添加关键帧偏移量位置处的情节提要。 必须在派生类中指定的偏移量或转换。

##  <a name="m_badded"></a>  CBaseKeyFrame::m_bAdded

指定此关键帧是否已添加到情节提要。

```
BOOL m_bAdded;
```

##  <a name="m_biskeyframeatoffset"></a>  CBaseKeyFrame::m_bIsKeyframeAtOffset

指定是否应将此关键帧添加到情节提要另一个现有关键帧偏移量位置处或末尾的某些转换。

```
BOOL m_bIsKeyframeAtOffset;
```

##  <a name="m_keyframe"></a>  CBaseKeyFrame::m_keyframe

表示 Windows 动画 API 关键帧。 关键帧未初始化时将它设置为预定义值 UI_ANIMATION_KEYFRAME_STORYBOARD_START。

```
UI_ANIMATION_KEYFRAME m_keyframe;
```

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
