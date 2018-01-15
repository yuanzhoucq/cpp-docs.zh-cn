---
title: "CMessageMap 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMessageMap
- ATLWIN/ATL::CMessageMap
- ATLWIN/ATL::CMessageMap::ProcessWindowMessage
dev_langs: C++
helpviewer_keywords:
- CMessageMap class
- message maps, ATL
- ATL, message handlers
ms.assetid: 1f97bc16-a8a0-4cf0-b90f-1778813a5c8e
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 04aff6922358048fcbd330096eb26a412cdb75ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmessagemap-class"></a>CMessageMap 类
此类允许对象的消息映射要由另一个对象的访问。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
class ATL_NO_VTABLE CMessageMap
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMessageMap::ProcessWindowMessage](#processwindowmessage)|访问消息映射中的`CMessageMap`-派生类。|  
  
## <a name="remarks"></a>备注  
 `CMessageMap`是一个抽象基类，允许对象的消息映射要由另一个对象进行访问。 为了使要公开其消息映射的对象，其类必须派生自`CMessageMap`。  
  
 使用 ATL`CMessageMap`到支持包含 windows 和动态消息映射链接。 例如，任何类包含[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)对象必须派生自`CMessageMap`。 以下代码摘自[SUBEDIT](../../visual-cpp-samples.md)示例。 通过[CComControl](../../atl/reference/ccomcontrol-class.md)、`CAtlEdit`类自动派生自`CMessageMap`。  
  
 [!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/cpp/cmessagemap-class_1.h)]  
  
 因为包含的窗口中， `m_EditCtrl`，将在包含的类中，使用消息映射`CAtlEdit`派生自`CMessageMap`。  
  
 有关消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)本文"ATL 窗口类。"  
  
## <a name="requirements"></a>惠?  
 **标头：** atlwin.h  
  
##  <a name="processwindowmessage"></a>CMessageMap::ProcessWindowMessage  
 访问由标识的消息映射`dwMsgMapID`中`CMessageMap`-派生类。  
  
```
virtual BOOL ProcessWindowMessage(  
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT& lResult,
    DWORD dwMsgMapID) = 0;
```  
  
### <a name="parameters"></a>参数  
 `hWnd`  
 [in]接收消息的窗口句柄。  
  
 `uMsg`  
 [in]发送到窗口的消息。  
  
 `wParam`  
 [in]消息特定的附加信息。  
  
 `lParam`  
 [in]消息特定的附加信息。  
  
 `lResult`  
 [out]消息处理的结果。  
  
 `dwMsgMapID`  
 [in]将处理该消息的消息映射的标识符。 使用默认消息映射中，声明[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)，由 0。 使用声明的备用消息映射， [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)，由标识`msgMapID`。  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果消息已完全处理; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 由窗口过程的调用[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)对象或对象的动态链接到消息映射。  
  
## <a name="see-also"></a>请参阅  
 [CDynamicChain 类](../../atl/reference/cdynamicchain-class.md)   
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)   
 [类概述](../../atl/atl-class-overview.md)
