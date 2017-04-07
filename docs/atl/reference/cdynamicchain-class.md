---
title: "CDynamicChain 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDynamicChain
- ATLWIN/ATL::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CallChain
- ATLWIN/ATL::CDynamicChain::RemoveChainEntry
- ATLWIN/ATL::CDynamicChain::SetChainEntry
dev_langs:
- C++
helpviewer_keywords:
- message maps, chaining
- chaining message maps
- CDynamicChain class
ms.assetid: f084b2be-0e77-4836-973d-ae278a1e9da8
caps.latest.revision: 21
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
ms.openlocfilehash: 4da97d0b3d72400d7e285fde187e6860759900af
ms.lasthandoff: 02/24/2017

---
# <a name="cdynamicchain-class"></a>CDynamicChain 类
此类提供支持消息映射的动态链接的方法。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
class CDynamicChain
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CDynamicChain::CDynamicChain](#cdynamicchain)|构造函数。|  
|[CDynamicChain:: ~ CDynamicChain](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDynamicChain::CallChain](#callchain)|将定向到另一个对象的消息映射的 Windows 消息。|  
|[CDynamicChain::RemoveChainEntry](#removechainentry)|从集合中移除一个消息映射条目。|  
|[CDynamicChain::SetChainEntry](#setchainentry)|将消息映射条目添加到集合，或修改现有条目。|  
  
## <a name="remarks"></a>备注  
 `CDynamicChain`管理启用的 Windows 消息定向，在运行时，另一个对象的消息映射到的消息映射的集合。  
  
 若要添加的消息映射的动态链接的支持，请执行以下操作︰  
  
-   派生您的类从`CDynamicChain`。 在消息映射中指定[CHAIN_MSG_MAP_DYNAMIC](http://msdn.microsoft.com/library/7e5c72b7-cb31-4f3b-8a1b-6293804af220)链接到另一个对象的默认消息映射宏。  
  
-   派生你想要从链接到每个的类[CMessageMap](../../atl/reference/cmessagemap-class.md)。 `CMessageMap`允许对象来公开其消息映射到其他对象。  
  
-   调用`CDynamicChain::SetChainEntry`以确定哪个对象和哪一条消息映射您希望链接到。  
  
 例如，假设您的类定义，如下所示︰  
  
 [!code-cpp[NVC_ATL_Windowing #&88;](../../atl/codesnippet/cpp/cdynamicchain-class_1.h)]  
  
 客户端然后调用`CMyWindow::SetChainEntry`:  
  
 [!code-cpp[NVC_ATL_Windowing #&89;](../../atl/codesnippet/cpp/cdynamicchain-class_2.cpp)]  
  
 其中`chainedObj`是链接的对象，是从派生的类的实例`CMessageMap`。 现在，如果`myCtl`接收一条消息，不由处理`OnPaint`或`OnSetFocus`，窗口过程将把消息引入`chainedObj`的默认消息映射。  
  
 有关消息映射链接的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)在文章"ATL 窗口类"。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlwin.h  
  
##  <a name="callchain"></a>CDynamicChain::CallChain  
 将定向到另一个对象的消息映射的 Windows 消息。  
  
```
BOOL CallChain(  
    DWORD dwChainID,
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT& lResult);
```  
  
### <a name="parameters"></a>参数  
 `dwChainID`  
 [in]使用链接的对象和其消息映射关联的唯一标识符。  
  
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
  
### <a name="return-value"></a>返回值  
 **TRUE**如果消息已完全处理; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 有关调用的窗口过程`CallChain`，您必须指定[CHAIN_MSG_MAP_DYNAMIC](http://msdn.microsoft.com/library/7e5c72b7-cb31-4f3b-8a1b-6293804af220)消息映射中的宏。 有关示例，请参阅[CDynamicChain](../../atl/reference/cdynamicchain-class.md)概述。  
  
 `CallChain`要求对以前调用[SetChainEntry](#setchainentry)关联`dwChainID`值，该值具有对象和其消息映射。  
  
##  <a name="cdynamicchain"></a>CDynamicChain::CDynamicChain  
 构造函数。  
  
```
CDynamicChain();
```  
  
##  <a name="dtor"></a>CDynamicChain:: ~ CDynamicChain  
 析构函数。  
  
```
~CDynamicChain();
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源。  
  
##  <a name="removechainentry"></a>CDynamicChain::RemoveChainEntry  
 从集合中移除指定的消息映射。  
  
```
BOOL RemoveChainEntry(DWORD dwChainID);
```  
  
### <a name="parameters"></a>参数  
 `dwChainID`  
 [in]使用链接的对象和其消息映射关联的唯一标识符。 最初定义此值，通过调用[SetChainEntry](#setchainentry)。  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果成功从集合中移除的消息映射。 否则为**FALSE**。  
  
##  <a name="setchainentry"></a>CDynamicChain::SetChainEntry  
 将指定的消息映射添加到集合。  
  
```
BOOL SetChainEntry(  
    DWORD dwChainID,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);
```  
  
### <a name="parameters"></a>参数  
 `dwChainID`  
 [in]使用链接的对象和其消息映射关联的唯一标识符。  
  
 `pObject`  
 [in]指向声明消息映射的链接对象的指针。 此对象必须派生自[CMessageMap](../../atl/reference/cmessagemap-class.md)。  
  
 `dwMsgMapID`  
 [in]消息映射中的链接对象的标识符。 默认值为 0，它标识用声明的默认消息映射[BEGIN_MSG_MAP](http://msdn.microsoft.com/library/8bbb5af9-18b1-48c6-880e-166f599ee554)。 若要指定的替换消息映射声明与[ALT_MSG_MAP(msgMapID)](http://msdn.microsoft.com/library/2c8871bf-abc0-4d52-bcf7-6b2ab9eb5af8)，传递`msgMapID`。  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果消息映射成功添加到集合。 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 如果`dwChainID`集合中已经存在值，其关联的对象和消息映射替换为`pObject`和`dwMsgMapID`分别。 否则，添加新条目。  
  
## <a name="see-also"></a>另请参阅  
 [CWindowImpl 类](../../atl/reference/cwindowimpl-class.md)   
 [类概述](../../atl/atl-class-overview.md)

