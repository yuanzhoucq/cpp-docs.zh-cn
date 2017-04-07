---
title: "CAnimationManagerEventHandler 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::OnManagerStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::SetAnimationController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationManagerEventHandler class
ms.assetid: 6089ec07-e661-4805-b227-823b4652aade
caps.latest.revision: 18
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
ms.openlocfilehash: e62d676c073998718b4df47223d1679b1187d66e
ms.lasthandoff: 02/24/2017

---
# <a name="canimationmanagereventhandler-class"></a>CAnimationManagerEventHandler 类
实现回调，它在动画管理器状态更改时由动画 API 调用。  
  
## <a name="syntax"></a>语法  
  
```  
class CAnimationManagerEventHandler : public CUIAnimationManagerEventHandlerBase<CAnimationManagerEventHandler>;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CAnimationManagerEventHandler::CAnimationManagerEventHandler](#canimationmanagereventhandler)|构造 `CAnimationManagerEventHandler` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAnimationManagerEventHandler::CreateInstance](#createinstance)|创建的一个实例`CAnimationManagerEventHandler`对象。|  
|[CAnimationManagerEventHandler::OnManagerStatusChanged](#onmanagerstatuschanged)|动画管理器的状态发生更改时调用。 （重写 `CUIAnimationManagerEventHandlerBase::OnManagerStatusChanged`。）|  
|[CAnimationManagerEventHandler::SetAnimationController](#setanimationcontroller)|存储事件路由的动画控制器的指针。|  
  
## <a name="remarks"></a>备注  
 创建并调用 CAnimationController::EnableAnimationManagerEvent 时传递给 IUIAnimationManager::SetManagerEventHandler 方法，此事件处理程序。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationManagerEventHandlerBase`  
  
 `CAnimationManagerEventHandler`  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="canimationmanagereventhandler"></a>CAnimationManagerEventHandler::CAnimationManagerEventHandler  
 [!INCLUDE[dev10_sp1required](../../mfc/reference/includes/dev10_sp1required_md.md)]  
  
 构造 CAnimationManagerEventHandler 对象。  
  
```  
CAnimationManagerEventHandler();
```  
  
##  <a name="createinstance"></a>CAnimationManagerEventHandler::CreateInstance  
 [!INCLUDE[dev10_sp1required](../../mfc/reference/includes/dev10_sp1required_md.md)]  
  
 创建 CAnimationManagerEventHandler 对象的实例。  
  
```  
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,  
    IUIAnimationManagerEventHandler** ppManagerEventHandler);
```  
  
### <a name="parameters"></a>参数  
 `pAnimationController`  
 一个指向动画控制器，它将接收此事件。  
  
 `ppManagerEventHandler`  
 输出。 如果该方法成功，则包含指向将处理状态更新为动画管理器的 COM 对象的指针。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，它会返回 S_OK。 否则，它返回一个 HRESULT 错误代码。  
  
##  <a name="onmanagerstatuschanged"></a>CAnimationManagerEventHandler::OnManagerStatusChanged  
 [!INCLUDE[dev10_sp1required](../../mfc/reference/includes/dev10_sp1required_md.md)]  
  
 动画管理器的状态发生更改时调用。  
  
```  
IFACEMETHOD(OnManagerStatusChanged)(
  UI_ANIMATION_MANAGER_STATUS newStatus,
  UI_ANIMATION_MANAGER_STATUS previousStatus);
```  
  
### <a name="parameters"></a>参数  
 `newStatus`  
 新的状态。  
  
 `previousStatus`  
 以前的状态。  
  
### <a name="return-value"></a>返回值  
 当前实现始终返回，则为 S_OK;  
  
##  <a name="setanimationcontroller"></a>CAnimationManagerEventHandler::SetAnimationController  
 [!INCLUDE[dev10_sp1required](../../mfc/reference/includes/dev10_sp1required_md.md)]  
  
 存储事件路由的动画控制器的指针。  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>参数  
 `pAnimationController`  
 一个指向动画控制器，它将接收此事件。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

