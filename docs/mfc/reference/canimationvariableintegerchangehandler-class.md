---
title: "CAnimationVariableIntegerChangeHandler 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::SetAnimationController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationVariableIntegerChangeHandler [MFC], CAnimationVariableIntegerChangeHandler
- CAnimationVariableIntegerChangeHandler [MFC], CreateInstance
- CAnimationVariableIntegerChangeHandler [MFC], OnIntegerValueChanged
- CAnimationVariableIntegerChangeHandler [MFC], SetAnimationController
ms.assetid: 6ac8e91b-e514-4ff6-babd-33f77c4b2b61
caps.latest.revision: 18
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 4a770b6508067913aec51b8b3878f33e30eed4bb
ms.openlocfilehash: 5348c1cdb665c7b50e4f3bbb504ed9f7d6606ea4
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="canimationvariableintegerchangehandler-class"></a>CAnimationVariableIntegerChangeHandler 类
实现回调，它在动画变量值更改时由动画 API 调用。  
  
## <a name="syntax"></a>语法  
  
```  
class CAnimationVariableIntegerChangeHandler : public CUIAnimationVariableIntegerChangeHandlerBase<CAnimationVariableIntegerChangeHandler>;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler](#canimationvariableintegerchangehandler)|构造 `CAnimationVariableIntegerChangeHandler` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAnimationVariableIntegerChangeHandler::CreateInstance](#createinstance)|创建的实例`CAnimationVariableIntegerChangeHandler`回调。|  
|[CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged](#onintegervaluechanged)|动画变量的值已更改时调用。 （重写 `CUIAnimationVariableIntegerChangeHandlerBase::OnIntegerValueChanged`。）|  
|[CAnimationVariableIntegerChangeHandler::SetAnimationController](#setanimationcontroller)|将存储到动画控制器路由事件的指针。|  
  
## <a name="remarks"></a>备注  
 此事件处理程序是创建并调用 CAnimationVariable::EnableIntegerValueChangedEvent 或 CAnimationBaseObject::EnableIntegerValueChangedEvent （可启用时传递给 IUIAnimationVariable::SetVariableIntegerChangeHandler 方法所有动画对象中封装的动画变量的此事件）。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [MFC 类](../../mfc/reference/mfc-classes.md)  
  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationVariableIntegerChangeHandlerBase`  
  
 `CAnimationVariableIntegerChangeHandler`  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="canimationvariableintegerchangehandler"></a>CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler  
 构造 CAnimationVariableIntegerChangeHandler 对象。  
  
```  
CAnimationVariableIntegerChangeHandler ();
```  
  
##  <a name="createinstance"></a>CAnimationVariableIntegerChangeHandler::CreateInstance  
 创建 CAnimationVariableIntegerChangeHandler 回调的实例。  
  
```  
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,  
    IUIAnimationVariableIntegerChangeHandler** ppHandler);
```  
  
### <a name="parameters"></a>参数  
 `pAnimationController`  
 指向动画控制器，它将接收此事件的指针。  
  
 `ppHandler`  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回，则为 S_OK。 否则，它返回一个 HRESULT 错误代码。  
  
##  <a name="onintegervaluechanged"></a>CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged  
 动画变量的值已更改时调用。  
  
```  
IFACEMETHOD(OnIntegerValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in INT32 newValue,
    __in INT32 previousValue);
```  
  
### <a name="parameters"></a>参数  
 `storyboard`  
 具有动画效果变量情节提要。  
  
 `variable`  
 已更新动画变量。  
  
 `newValue`  
 新舍入的值。  
  
 `previousValue`  
 以前的舍入的值。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功; 则为 S_OK否则为 E_FAIL。  
  
##  <a name="setanimationcontroller"></a>CAnimationVariableIntegerChangeHandler::SetAnimationController  
 将存储到动画控制器路由事件的指针。  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>参数  
 `pAnimationController`  
 指向动画控制器，它将接收此事件的指针。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

