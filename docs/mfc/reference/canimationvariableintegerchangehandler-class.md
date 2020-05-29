---
title: CAnimationVariableIntegerChangeHandler 类
ms.date: 11/04/2016
f1_keywords:
- CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::SetAnimationController
helpviewer_keywords:
- CAnimationVariableIntegerChangeHandler [MFC], CAnimationVariableIntegerChangeHandler
- CAnimationVariableIntegerChangeHandler [MFC], CreateInstance
- CAnimationVariableIntegerChangeHandler [MFC], OnIntegerValueChanged
- CAnimationVariableIntegerChangeHandler [MFC], SetAnimationController
ms.assetid: 6ac8e91b-e514-4ff6-babd-33f77c4b2b61
ms.openlocfilehash: dec940d2f5e68f0531fc917df447b5a1a5cb8189
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755060"
---
# <a name="canimationvariableintegerchangehandler-class"></a>CAnimationVariableIntegerChangeHandler 类

实现回调，它在动画变量值更改时由动画 API 调用。

## <a name="syntax"></a>语法

```
class CAnimationVariableIntegerChangeHandler : public CUIAnimationVariableIntegerChangeHandlerBase<CAnimationVariableIntegerChangeHandler>;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[动画变量素转换处理程序：：c动画变量在转换处理程序](#canimationvariableintegerchangehandler)|构造 `CAnimationVariableIntegerChangeHandler` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[动画可变转换处理程序：：创建实例](#createinstance)|创建回调实例`CAnimationVariableIntegerChangeHandler`。|
|[动画可变整数转换处理程序：：oninteger值已更改](#onintegervaluechanged)|当动画变量的值已更改时调用。 （重写 `CUIAnimationVariableIntegerChangeHandlerBase::OnIntegerValueChanged`。）|
|[动画可变转换处理程序：：设置动画控制器](#setanimationcontroller)|存储指向动画控制器的指针以路由事件。|

## <a name="remarks"></a>备注

此事件处理程序被创建并传递给 IUIAnimationvariable：：设置可变IntegerChangeHandler方法，当您调用 CAnimationvariable：：启用 IntegerValueChangeevent 或 CAnimationBaseObject：启用 IntegerValueChangeEvent（它启用此事件，用于封装在动画对象中的所有动画变量）。

## <a name="inheritance-hierarchy"></a>继承层次结构

[MFC 类](../../mfc/reference/mfc-classes.md)

`CUIAnimationCallbackBase`

`CUIAnimationVariableIntegerChangeHandlerBase`

`CAnimationVariableIntegerChangeHandler`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="canimationvariableintegerchangehandlercanimationvariableintegerchangehandler"></a><a name="canimationvariableintegerchangehandler"></a>动画变量素转换处理程序：：c动画变量在转换处理程序

构造一个 CAnimation 可变IntegerChangeHandler对象。

```
CAnimationVariableIntegerChangeHandler ();
```

## <a name="canimationvariableintegerchangehandlercreateinstance"></a><a name="createinstance"></a>动画可变转换处理程序：：创建实例

创建 CAnimation 可变IntegerChangeHandler回调的实例。

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationVariableIntegerChangeHandler** ppHandler);
```

### <a name="parameters"></a>参数

*动画控制器*<br/>
指向动画控制器的指针，该控制器将接收事件。

*普汉德勒*

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 否则，它将返回一个 HRESULT 错误代码。

## <a name="canimationvariableintegerchangehandleronintegervaluechanged"></a><a name="onintegervaluechanged"></a>动画可变整数转换处理程序：：oninteger值已更改

当动画变量的值已更改时调用。

```
IFACEMETHOD(OnIntegerValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in INT32 newValue,
    __in INT32 previousValue);
```

### <a name="parameters"></a>参数

*脚本*<br/>
为变量设置动画的情节提要。

*变量*<br/>
已更新的动画变量。

*newValue*<br/>
新的舍入值。

*上一个值*<br/>
上一个舍入的值。

### <a name="return-value"></a>返回值

如果方法成功，S_OK;否则E_FAIL。

## <a name="canimationvariableintegerchangehandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>动画可变转换处理程序：：设置动画控制器

存储指向动画控制器的指针以路由事件。

```cpp
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>参数

*动画控制器*<br/>
指向动画控制器的指针，该控制器将接收事件。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
