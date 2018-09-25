---
title: CAnimationVariableChangeHandler 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::OnValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::SetAnimationController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationVariableChangeHandler [MFC], OnValueChanged
- CAnimationVariableChangeHandler [MFC], SetAnimationController
ms.assetid: 2ea4996d-5c04-4dfc-be79-d42d55050795
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 23521a9ee9706787df0568547fe3419fe7e4fae5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424594"
---
# <a name="canimationvariablechangehandler-class"></a>CAnimationVariableChangeHandler 类

实现回调，它在动画变量值更改时由动画 API 调用。

## <a name="syntax"></a>语法

```
class CAnimationVariableChangeHandler : public CUIAnimationVariableChangeHandlerBase<CAnimationVariableChangeHandler>;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|`CAnimationVariableChangeHandler::CAnimationVariableChangeHandler`|构造 `CAnimationVariableChangeHandler` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|`CAnimationVariableChangeHandler::CreateInstance`|创建的实例`CAnimationVariableChangeHandler`对象。|
|[CAnimationVariableChangeHandler::OnValueChanged](#onvaluechanged)|动画变量的值发生更改时调用。 （重写 `CUIAnimationVariableChangeHandlerBase::OnValueChanged`。）|
|[CAnimationVariableChangeHandler::SetAnimationController](#setanimationcontroller)|存储指向动画控制器的路由事件。|

## <a name="remarks"></a>备注

创建此事件处理程序并将其传递给`IUIAnimationVariable::SetVariableChangeHandler`方法，在调用时`CAnimationVariable::EnableValueChangedEvent`或`CAnimationBaseObject::EnableValueChangedEvent`（这会使所有动画变量，在动画对象中封装此事件）。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CUIAnimationCallbackBase`

`CUIAnimationVariableChangeHandlerBase`

`CAnimationVariableChangeHandler`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="onvaluechanged"></a>  CAnimationVariableChangeHandler::OnValueChanged

动画变量的值发生更改时调用。

```
IFACEMETHOD(OnValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in DOUBLE newValue,
    __in DOUBLE previousValue);
```

### <a name="parameters"></a>参数

*情节提要*<br/>
情节提要，对变量进行动画处理。

*变量*<br/>
已更新的动画变量。

*newValue*<br/>
新值。

*previousValue*<br/>
以前的值。

### <a name="return-value"></a>返回值

如果该方法成功，它会返回 S_OK。 否则，它返回一个 HRESULT 错误代码。

##  <a name="setanimationcontroller"></a>  CAnimationVariableChangeHandler::SetAnimationController

存储指向动画控制器的路由事件。

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>参数

*pAnimationController*<br/>
一个指向动画控制器，它将接收事件。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
