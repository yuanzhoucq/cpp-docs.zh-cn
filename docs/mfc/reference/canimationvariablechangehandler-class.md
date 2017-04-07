---
title: "CAnimationVariableChangeHandler 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::OnValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::SetAnimationController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationVariableChangeHandler class
ms.assetid: 2ea4996d-5c04-4dfc-be79-d42d55050795
caps.latest.revision: 19
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
ms.openlocfilehash: 46c4eb9210b69c527375b12100ab7cc22fef0176
ms.lasthandoff: 02/24/2017

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
  
|名称|说明|  
|----------|-----------------|  
|`CAnimationVariableChangeHandler::CreateInstance`|创建的一个实例`CAnimationVariableChangeHandler`对象。|  
|[CAnimationVariableChangeHandler::OnValueChanged](#onvaluechanged)|动画变量的值发生更改时调用。 （重写 `CUIAnimationVariableChangeHandlerBase::OnValueChanged`。）|  
|[CAnimationVariableChangeHandler::SetAnimationController](#setanimationcontroller)|存储事件路由的动画控制器的指针。|  
  
## <a name="remarks"></a>备注  
 此事件处理程序被创建并传递到`IUIAnimationVariable::SetVariableChangeHandler`方法中，当您调用`CAnimationVariable::EnableValueChangedEvent`或`CAnimationBaseObject::EnableValueChangedEvent`（这会使所有的动画变量中的动画对象封装此事件）。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationVariableChangeHandlerBase`  
  
 `CAnimationVariableChangeHandler`  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="onvaluechanged"></a>CAnimationVariableChangeHandler::OnValueChanged  
 动画变量的值发生更改时调用。  
  
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
 已更新的动画变量。  
  
 `newValue`  
 新值。  
  
 `previousValue`  
 以前的值。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，它会返回 S_OK。 否则，它返回一个 HRESULT 错误代码。  
  
##  <a name="setanimationcontroller"></a>CAnimationVariableChangeHandler::SetAnimationController  
 存储事件路由的动画控制器的指针。  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>参数  
 `pAnimationController`  
 一个指向动画控制器，它将接收此事件。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

