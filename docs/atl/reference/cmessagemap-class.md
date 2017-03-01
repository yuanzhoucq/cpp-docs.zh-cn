---
title: "CMessageMap 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMessageMap
- ATL.CMessageMap
- ATL::CMessageMap
dev_langs:
- C++
helpviewer_keywords:
- CMessageMap class
- message maps, ATL
- ATL, message handlers
ms.assetid: 1f97bc16-a8a0-4cf0-b90f-1778813a5c8e
caps.latest.revision: 22
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: f0b40c73101463b934e3fcf299171bea142fe838
ms.lasthandoff: 02/24/2017

---
# <a name="cmessagemap-class"></a>CMessageMap 类
此类允许对象的消息映射为由另一个对象的访问。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
class ATL_NO_VTABLE CMessageMap
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMessageMap::ProcessWindowMessage](#processwindowmessage)|访问消息映射中的`CMessageMap`的派生类。|  
  
## <a name="remarks"></a>备注  
 `CMessageMap`是一个抽象基类，它允许对象的消息映射为可由另一个对象访问。 为了使对象公开其消息映射，其类必须派生自`CMessageMap`。  
  
 ATL 使用`CMessageMap`到包含支持 windows 和动态消息映射链接。 例如，任何类包含[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)对象必须派生自`CMessageMap`。 以下代码摘自[SUBEDIT](../../visual-cpp-samples.md)示例。 通过[CComControl](../../atl/reference/ccomcontrol-class.md)、`CAtlEdit`类自动派生自`CMessageMap`。  
  
 [!code-cpp[NVC_ATL_Windowing #&90;](../../atl/codesnippet/cpp/cmessagemap-class_1.h)]  
  
 因为包含窗口， `m_EditCtrl`，将使用消息映射中包含的类，`CAtlEdit`派生自`CMessageMap`。  
  
 关于消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)在文章"ATL 窗口类"。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlwin.h  
  
##  <a name="a-nameprocesswindowmessagea--cmessagemapprocesswindowmessage"></a><a name="processwindowmessage"></a>CMessageMap::ProcessWindowMessage  
 访问由标识的消息映射`dwMsgMapID`中`CMessageMap`的派生类。  
  
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
 [in]将处理该消息的消息映射的标识符。 使用默认消息映射中，声明[BEGIN_MSG_MAP](http://msdn.microsoft.com/library/8bbb5af9-18b1-48c6-880e-166f599ee554)，被 0 除标识。 使用替换消息映射声明[ALT_MSG_MAP(msgMapID)](http://msdn.microsoft.com/library/2c8871bf-abc0-4d52-bcf7-6b2ab9eb5af8)，由标识`msgMapID`。  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果消息已完全处理; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 由窗口过程的调用[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)对象或对象的动态链接到的消息映射。  
  
## <a name="see-also"></a>另请参阅  
 [CDynamicChain 类](../../atl/reference/cdynamicchain-class.md)   
 [BEGIN_MSG_MAP](http://msdn.microsoft.com/library/8bbb5af9-18b1-48c6-880e-166f599ee554)   
 [ALT_MSG_MAP](http://msdn.microsoft.com/library/2c8871bf-abc0-4d52-bcf7-6b2ab9eb5af8)   
 [类概述](../../atl/atl-class-overview.md)

