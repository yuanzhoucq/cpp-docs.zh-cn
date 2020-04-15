---
title: CAnimationVariableChangeHandler 类
ms.date: 11/04/2016
f1_keywords:
- CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::OnValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::SetAnimationController
helpviewer_keywords:
- CAnimationVariableChangeHandler [MFC], OnValueChanged
- CAnimationVariableChangeHandler [MFC], SetAnimationController
ms.assetid: 2ea4996d-5c04-4dfc-be79-d42d55050795
ms.openlocfilehash: 7f45fdad00bacf56e2ee8c30b76e99d626902534
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377083"
---
# <a name="canimationvariablechangehandler-class"></a>CAnimationVariableChangeHandler 类

实现回调，它在动画变量值更改时由动画 API 调用。

## <a name="syntax"></a>语法

```
class CAnimationVariableChangeHandler : public CUIAnimationVariableChangeHandlerBase<CAnimationVariableChangeHandler>;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|`CAnimationVariableChangeHandler::CAnimationVariableChangeHandler`|构造 `CAnimationVariableChangeHandler` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|`CAnimationVariableChangeHandler::CreateInstance`|创建`CAnimationVariableChangeHandler`对象的实例。|
|[C动画可变更改处理程序：：在值转换](#onvaluechanged)|当动画变量的值已更改时调用。 （重写 `CUIAnimationVariableChangeHandlerBase::OnValueChanged`。）|
|[动画变量更改处理程序：：设置动画控制器](#setanimationcontroller)|存储指向动画控制器的指针以路由事件。|

## <a name="remarks"></a>备注

此事件处理程序在调用`IUIAnimationVariable::SetVariableChangeHandler``CAnimationVariable::EnableValueChangedEvent`或`CAnimationBaseObject::EnableValueChangedEvent`时创建并传递给方法（这启用动画对象中封装的所有动画变量的此事件）。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CUIAnimationCallbackBase`

`CUIAnimationVariableChangeHandlerBase`

`CAnimationVariableChangeHandler`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="canimationvariablechangehandleronvaluechanged"></a><a name="onvaluechanged"></a>C动画可变更改处理程序：：在值转换

当动画变量的值已更改时调用。

```
IFACEMETHOD(OnValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in DOUBLE newValue,
    __in DOUBLE previousValue);
```

### <a name="parameters"></a>参数

*脚本*<br/>
为变量设置动画的情节提要。

*可变*<br/>
已更新的动画变量。

*新值*<br/>
新值。

*上一个值*<br/>
以前的值。

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 否则，它将返回一个 HRESULT 错误代码。

## <a name="canimationvariablechangehandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>动画变量更改处理程序：：设置动画控制器

存储指向动画控制器的指针以路由事件。

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>参数

*动画控制器*<br/>
指向动画控制器的指针，该控制器将接收事件。

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
