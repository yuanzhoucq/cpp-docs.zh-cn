---
title: CAnimationVariableChangeHandler 类 |Microsoft 文档
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
ms.openlocfilehash: 2e35fc33b26fa6bead73458a46d7c4edee1cf136
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350987"
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
|[CAnimationVariableChangeHandler::OnValueChanged](#onvaluechanged)|动画变量的值已更改时调用。 （重写 `CUIAnimationVariableChangeHandlerBase::OnValueChanged`。）|  
|[CAnimationVariableChangeHandler::SetAnimationController](#setanimationcontroller)|将存储到动画控制器路由事件的指针。|  
  
## <a name="remarks"></a>备注  
 此事件处理程序是创建并传递给`IUIAnimationVariable::SetVariableChangeHandler`方法，当您调用`CAnimationVariable::EnableValueChangedEvent`或`CAnimationBaseObject::EnableValueChangedEvent`（这样的动画对象中封装所有动画变量的此事件）。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationVariableChangeHandlerBase`  
  
 `CAnimationVariableChangeHandler`  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="onvaluechanged"></a>  CAnimationVariableChangeHandler::OnValueChanged  
 动画变量的值已更改时调用。  
  
```  
IFACEMETHOD(OnValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in DOUBLE newValue,
    __in DOUBLE previousValue);
```  
  
### <a name="parameters"></a>参数  
 `storyboard`  
 具有动画效果变量情节提要。  
  
 `variable`  
 已更新动画变量。  
  
 `newValue`  
 新值。  
  
 `previousValue`  
 以前的值。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回，则为 S_OK。 否则，它返回一个 HRESULT 错误代码。  
  
##  <a name="setanimationcontroller"></a>  CAnimationVariableChangeHandler::SetAnimationController  
 将存储到动画控制器路由事件的指针。  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>参数  
 `pAnimationController`  
 指向动画控制器，它将接收此事件的指针。  
  
## <a name="see-also"></a>请参阅  
 [类](../../mfc/reference/mfc-classes.md)
