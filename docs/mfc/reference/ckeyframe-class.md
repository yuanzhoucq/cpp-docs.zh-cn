---
title: CKeyFrame 类
ms.date: 11/04/2016
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
ms.openlocfilehash: f535503338a82c7cc70455ae6a08cdab0f13c624
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372296"
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
|[钥匙框架：：CKeyFrame](#ckeyframe)|已重载。 构造依赖于其他关键帧的关键帧。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CKeyFrame：：添加到故事板](#addtostoryboard)|向情节提要添加关键帧。 （覆盖[CBaseKeyFrame：：添加到情节板](../../mfc/reference/cbasekeyframe-class.md#addtostoryboard)。|
|[CKeyFrame：在过渡后添加到故事板](#addtostoryboardaftertransition)|过渡后向情节提要添加关键帧。|
|[CKeyframe：：添加到故事板的偏移](#addtostoryboardatoffset)|在偏移时将关键帧添加到情节提要。|
|[关键帧：获取现有关键帧](#getexistingkeyframe)|返回指向此关键帧所依赖的关键帧的指针。|
|[关键帧：获取偏移](#getoffset)|返回与其他关键帧的偏移量。|
|[关键帧：获取过渡](#gettransition)|返回指向此关键帧所依赖的过渡的指针。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[关键帧：m_offset](#m_offset)|指定此关键帧与存储在m_pExistingKeyFrame的关键帧的偏移量。|
|[CKeyFrame：m_pExistingKeyFrame](#m_pexistingkeyframe)|存储指向现有 keframe 的指针。 此关键帧将添加到情节提要中，m_offset添加到现有关键帧中。|
|[CKeyFrame：m_pTransition](#m_ptransition)|存储从此关键帧开始的换转指针。|

## <a name="remarks"></a>备注

此类实现动画关键帧。 关键帧表示情节提要中的一个时刻，可用于指定过渡的开始和结束时间。 关键帧可能基于其他关键帧，并且具有偏移量（以秒为单位），或者可能基于过渡，并代表此转换结束时的一个时刻。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBaseKey框架](../../mfc/reference/cbasekeyframe-class.md)

[基卡框架](../../mfc/reference/ckeyframe-class.md)

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="ckeyframeaddtostoryboard"></a><a name="addtostoryboard"></a>CKeyFrame：：添加到故事板

向情节提要添加关键帧。

```
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>参数

*板*<br/>
指向情节提要的指针。

*bDeepAdd*<br/>
指定是递归添加关键帧还是转换。

### <a name="return-value"></a>返回值

如果成功添加了关键帧，则为 TRUE。

### <a name="remarks"></a>备注

此方法将关键帧添加到情节提要。 如果它依赖于其他关键帧或转换，并且 bDeepAdd 为 TRUE，则此方法会尝试递归添加它们。

## <a name="ckeyframeaddtostoryboardaftertransition"></a><a name="addtostoryboardaftertransition"></a>CKeyFrame：在过渡后添加到故事板

过渡后向情节提要添加关键帧。

```
BOOL AddToStoryboardAfterTransition(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>参数

*板*<br/>
指向情节提要的指针。

*bDeepAdd*<br/>
指定是否递归添加转换。

### <a name="return-value"></a>返回值

如果成功添加了关键帧，则为 TRUE。

### <a name="remarks"></a>备注

框架调用此函数，以便在转换后将关键帧添加到情节提要。

## <a name="ckeyframeaddtostoryboardatoffset"></a><a name="addtostoryboardatoffset"></a>CKeyframe：：添加到故事板的偏移

在偏移时将关键帧添加到情节提要。

```
virtual BOOL AddToStoryboardAtOffset(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>参数

*板*<br/>
指向情节提要的指针。

*bDeepAdd*<br/>
指定是否添加此关键帧取决于递归的关键帧。

### <a name="return-value"></a>返回值

如果成功添加了关键帧，则为 TRUE。

### <a name="remarks"></a>备注

框架调用此功能，以偏移时将关键帧添加到情节提要。

## <a name="ckeyframeckeyframe"></a><a name="ckeyframe"></a>钥匙框架：：CKeyFrame

构造依赖于转换的关键帧。

```
CKeyFrame(CBaseTransition* pTransition);

CKeyFrame(
    CBaseKeyFrame* pKeyframe,
    UI_ANIMATION_SECONDS offset = 0.0);
```

### <a name="parameters"></a>参数

*p 转换*<br/>
指向转换的指针。

*p键框*<br/>
指向关键帧的指针。

*偏移量*<br/>
与 pKeyframe 指定的关键帧的偏移（以秒为单位）。

### <a name="remarks"></a>备注

构造的关键帧将在指定的过渡结束时在情节提要中表示一个时刻。

## <a name="ckeyframegetexistingkeyframe"></a><a name="getexistingkeyframe"></a>关键帧：获取现有关键帧

返回指向此关键帧所依赖的关键帧的指针。

```
CBaseKeyFrame* GetExistingKeyframe();
```

### <a name="return-value"></a>返回值

如果此关键帧不依赖于其他关键帧，则指向关键帧的有效指针或 NULL。

### <a name="remarks"></a>备注

这是此关键帧所依赖的关键帧的访问器。

## <a name="ckeyframegetoffset"></a><a name="getoffset"></a>关键帧：获取偏移

返回与其他关键帧的偏移量。

```
UI_ANIMATION_SECONDS GetOffset();
```

### <a name="return-value"></a>返回值

与其他关键帧的偏移量（以秒为单位）。

### <a name="remarks"></a>备注

应调用此方法以确定与其他关键帧的偏移量（以秒为单位）。

## <a name="ckeyframegettransition"></a><a name="gettransition"></a>关键帧：获取过渡

返回指向此关键帧所依赖的过渡的指针。

```
CBaseTransition* GetTransition();
```

### <a name="return-value"></a>返回值

如果此关键帧不依赖于转换，则指向转换的有效指针或 NULL。

### <a name="remarks"></a>备注

这是此关键帧所依赖的过渡的访问器。

## <a name="ckeyframem_offset"></a><a name="m_offset"></a>关键帧：m_offset

指定此关键帧与存储在m_pExistingKeyFrame的关键帧的偏移量。

```
UI_ANIMATION_SECONDS m_offset;
```

## <a name="ckeyframem_pexistingkeyframe"></a><a name="m_pexistingkeyframe"></a>CKeyFrame：m_pExistingKeyFrame

存储指向现有 keframe 的指针。 此关键帧将添加到情节提要中，m_offset添加到现有关键帧中。

```
CBaseKeyFrame* m_pExistingKeyFrame;
```

## <a name="ckeyframem_ptransition"></a><a name="m_ptransition"></a>CKeyFrame：m_pTransition

存储从此关键帧开始的换转指针。

```
CBaseTransition* m_pTransition;
```

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
