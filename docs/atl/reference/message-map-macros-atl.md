---
title: "消息映射宏 (ATL) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: eefdd546-8934-4a30-b263-9c06a8addcbd
caps.latest.revision: 16
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 8097982d6574af2ce1ba592dbead8abf6f6433df
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="message-map-macros-atl"></a>消息映射宏 (ATL)
这些宏定义消息映射和条目。  
  
|||  
|-|-|  
|[ALT_MSG_MAP](#alt_msg_map)|标记的替换消息映射开头。|  
|[BEGIN_MSG_MAP](#begin_msg_map)|标记默认消息映射的开头。|  
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|链接到替换消息映射中的基类。|  
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|链接到替换消息映射中的类数据成员。|  
|[CHAIN_MSG_MAP](#chain_msg_map)|链接至基类中的默认消息映射。|  
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|链接至另一个类在运行时中的消息映射。|  
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|链接至默认消息映射中的类数据成员。|  
|[COMMAND_CODE_HANDLER](#command_code_handler)|映射**WM_COMMAND**到处理程序函数，基于通知代码的消息。|  
|[COMMAND_HANDLER](#command_handler)|映射**WM_COMMAND**消息处理程序函数，基于通知代码和菜单项、 控件或加速器的标识符。|  
|[COMMAND_ID_HANDLER](#command_id_handler)|映射**WM_COMMAND**消息处理程序函数，根据菜单项、 控件或加速器的标识符。|  
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|映射**WM_COMMAND**消息处理程序函数，基于通知代码和一组连续的控件标识符。|  
|[COMMAND_RANGE_HANDLER](#command_range_handler)|映射**WM_COMMAND**消息处理程序函数，基于一组连续的控件标识符。|  
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|实现空消息映射。|  
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|提供反映否则未处理的消息的默认处理程序。|  
|[END_MSG_MAP](#end_msg_map)|将消息映射的结尾标记。|  
|[FORWARD_NOTIFICATIONS](#forward_notifications)|将转发到父窗口的通知消息。|  
|[MESSAGE_HANDLER](#message_handler)|将 Windows 消息映射到处理程序函数。|  
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|将连续的 Windows 消息映射到处理程序函数。|  
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|映射**WM_NOTIFY**到处理程序函数，基于通知代码的消息。|  
|[NOTIFY_HANDLER](#notify_handler)|映射**WM_NOTIFY**消息处理程序函数，基于通知代码和控制标识符。|  
|[NOTIFY_ID_HANDLER](#notify_id_handler)|映射**WM_NOTIFY**消息处理程序函数，根据控制标识符。|  
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|映射**WM_NOTIFY**消息处理程序函数，基于通知代码和一组连续的控件标识符。|  
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|映射**WM_NOTIFY**消息处理程序函数，基于一组连续的控件标识符。|  
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|反映回窗口中，向他们发送通知消息。|  
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|映射反射**WM_COMMAND**到处理程序函数，基于通知代码的消息。|  
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|映射反射**WM_COMMAND**消息处理程序函数，基于通知代码和菜单项、 控件或加速器的标识符。|  
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|映射反射**WM_COMMAND**消息处理程序函数，根据菜单项、 控件或加速器的标识符。|  
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|映射反射**WM_COMMAND**消息处理程序函数，基于通知代码和一组连续的控件标识符。|  
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|映射反射**WM_COMMAND**消息处理程序函数，基于一组连续的控件标识符。|  
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|映射反射**WM_NOTIFY**到处理程序函数，基于通知代码的消息。|  
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|映射反射**WM_NOTIFY**消息处理程序函数，基于通知代码和控制标识符。|  
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|映射反射**WM_NOTIFY**消息处理程序函数，根据控制标识符。|  
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|映射反射**WM_NOTIFY**消息处理程序函数，基于通知代码和一组连续的控件标识符。|  
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|映射反射**WM_NOTIFY**消息处理程序函数，基于一组连续的控件标识符。|  

## <a name="requirements"></a>要求  
 **标头︰** atlwin.h  

##  <a name="alt_msg_map"></a>ALT_MSG_MAP  
 标记的替换消息映射开头。  
  
```
ALT_MSG_MAP(msgMapID)
```  
  
### <a name="parameters"></a>参数  
 `msgMapID`  
 [in]消息映射标识符。  
  
### <a name="remarks"></a>备注  
 ATL 标识每个消息映射由很多。 默认消息映射 (使用声明`BEGIN_MSG_MAP`宏) 中被 0 除标识。 由标识替换消息映射`msgMapID`。  
  
 消息映射用于处理发送到窗口消息。 例如， [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)允许您指定的包含对象中的消息映射的标识符。 [CContainedWindow::WindowProc](ccontainedwindowt-class.md#windowproc)然后使用此消息映射将定向到适当的处理程序函数或另一个消息映射包含的窗口消息。 声明处理程序函数的宏的列表，请参阅[BEGIN_MSG_MAP](#begin_msg_map)。  
  
 始终以与消息映射`BEGIN_MSG_MAP`。 然后，您可以声明后续替换消息映射。  
  
 [END_MSG_MAP](#end_msg_map)宏标记的消息映射的末尾。 请注意，始终有恰好一个实例`BEGIN_MSG_MAP`和`END_MSG_MAP`。  
  
 有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。  
  
### <a name="example"></a>示例  
 下面的示例显示了默认的消息映射和一个替换消息映射中，每个都包含一个处理程序函数︰  
  
 [!code-cpp[NVC_ATL_Windowing #&98;](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]  
  
 下面的示例演示两个替换消息映射。 默认消息映射为空。  
  
 [!code-cpp[NVC_ATL_Windowing #&99;](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]  
  
### <a name="requirements"></a>要求  
 **标头︰** atlwin.h   

##  <a name="begin_msg_map"></a>BEGIN_MSG_MAP  
 标记默认消息映射的开头。  
  
```
BEGIN_MSG_MAP(theClass)
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 [in]包含消息映射的类的名称。  
  
### <a name="remarks"></a>备注  
 [CWindowImpl::WindowProc](cwindowimpl-class.md#windowproc)使用默认消息映射来处理发送到窗口的消息。 消息映射将定向到适当的处理程序函数或另一个消息映射的消息。  

  
 下列宏将消息映射到处理程序函数。 此函数必须在定义`theClass`。  
  
|宏|描述|  
|-----------|-----------------|  
|[MESSAGE_HANDLER](#message_handler)|将 Windows 消息映射到处理程序函数。|  
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|将连续的 Windows 消息映射到处理程序函数。|  
|[COMMAND_HANDLER](#command_handler)|映射**WM_COMMAND**消息处理程序函数，基于通知代码和菜单项、 控件或加速器的标识符。|  
|[COMMAND_ID_HANDLER](#command_id_handler)|映射**WM_COMMAND**消息处理程序函数，根据菜单项、 控件或加速器的标识符。|  
|[COMMAND_CODE_HANDLER](#command_handler)|映射**WM_COMMAND**到处理程序函数，基于通知代码的消息。|  
|[COMMAND_RANGE_HANDLER](#command_range_handler)|映射一个连续的范围**WM_COMMAND**消息处理程序函数，基于菜单项、 控件或加速器的标识符。|  
|[NOTIFY_HANDLER](#notify_handler)|映射**WM_NOTIFY**消息处理程序函数，基于通知代码和控制标识符。|  
|[NOTIFY_ID_HANDLER](#notify_id_handler)|映射**WM_NOTIFY**消息处理程序函数，根据控制标识符。|  
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|映射**WM_NOTIFY**到处理程序函数，基于通知代码的消息。|  
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|映射一个连续的范围**WM_NOTIFY**消息处理程序函数，基于控制标识符。|  
  
 下列宏将消息定向到另一个消息映射。 此过程称为"链接"。  
  
|宏|描述|  
|-----------|-----------------|  
|[CHAIN_MSG_MAP](#chain_msg_map)|链接至基类中的默认消息映射。|  
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|链接至默认消息映射中的类数据成员。|  
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|链接到替换消息映射中的基类。|  
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|链接到替换消息映射中的类数据成员。|  
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|链接至另一个类在运行时中的默认消息映射。|  
  
 下列宏直接从父窗口的"反射"消息。 例如，控件通常将发送通知消息到其父窗口的处理，但父窗口可以反映消息传送给该控件。  
  
|宏|说明|  
|-----------|-----------------|  
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|映射反射**WM_COMMAND**消息处理程序函数，基于通知代码和菜单项、 控件或加速器的标识符。|  
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|映射反射**WM_COMMAND**消息处理程序函数，根据菜单项、 控件或加速器的标识符。|  
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|映射反射**WM_COMMAND**到处理程序函数，基于通知代码的消息。|  
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|映射反射**WM_COMMAND**消息处理程序函数，基于一组连续的控件标识符。|  
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|映射反射**WM_COMMAND**消息处理程序函数，基于通知代码和一组连续的控件标识符。|  
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|映射反射**WM_NOTIFY**消息处理程序函数，基于通知代码和控制标识符。|  
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|映射反射**WM_NOTIFY**消息处理程序函数，根据控制标识符。|  
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|映射反射**WM_NOTIFY**到处理程序函数，基于通知代码的消息。|  
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|映射反射**WM_NOTIFY**消息处理程序函数，基于一组连续的控件标识符。|  
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|映射反射**WM_NOTIFY**消息处理程序函数，基于通知代码和一组连续的控件标识符。|  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&102;](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]  
  
 当`CMyExtWindow`对象接收`WM_PAINT`消息，消息定向到`CMyExtWindow::OnPaint`实际处理。 如果`OnPaint`指示需要对消息进行进一步处理该消息将然后定向到的默认消息映射中`CMyBaseWindow`。  
  
 除了默认消息映射中，您可以定义使用的替换消息映射[ALT_MSG_MAP](#alt_msg_map)。 始终以与消息映射`BEGIN_MSG_MAP`。 然后，您可以声明后续替换消息映射。 下面的示例显示了默认的消息映射和一个替换消息映射中，每个都包含一个处理程序函数︰  
  
 [!code-cpp[NVC_ATL_Windowing #&98;](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]  
  
 下面的示例演示两个替换消息映射。 默认消息映射为空。  
  
 [!code-cpp[NVC_ATL_Windowing #&99;](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]  
  
 [END_MSG_MAP](#end_msg_map)宏标记的消息映射的末尾。 请注意，始终有恰好一个实例`BEGIN_MSG_MAP`和`END_MSG_MAP`。  
  
 有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。  
  
### <a name="requirements"></a>要求  
 **标头︰** atlwin.h   
  
##  <a name="chain_msg_map_alt"></a>CHAIN_MSG_MAP_ALT  
 消息映射中定义一个条目。  
  
```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```  
  
### <a name="parameters"></a>参数  
 `theChainClass`  
 [in]包含的消息映射的类的基类的名称。  
  
 `msgMapID`  
 [in]消息映射标识符。  
  
### <a name="remarks"></a>备注  
 `CHAIN_MSG_MAP_ALT`在基类中，直接将消息传递到替换消息映射。 您必须声明与此替换消息映射[ALT_MSG_MAP(msgMapID)](#alt_msg_map)。 若要将消息定向到基类的默认消息映射 (使用声明[BEGIN_MSG_MAP](#begin_msg_map))，使用`CHAIN_MSG_MAP`。 有关示例，请参阅[CHAIN_MSG_MAP](#chain_msg_map)。  
  
> [!NOTE]
>  始终以与消息映射`BEGIN_MSG_MAP`。 然后，您可以声明与后续的备用消息映射`ALT_MSG_MAP`。 [END_MSG_MAP](#end_msg_map)宏标记的消息映射的末尾。 每个消息映射必须有且仅一个实例的`BEGIN_MSG_MAP`和`END_MSG_MAP`。  
  
 有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。  
  
### <a name="requirements"></a>要求  
 **标头︰** atlwin.h   
  
##  <a name="chain_msg_map_alt_member"></a>CHAIN_MSG_MAP_ALT_MEMBER  
 消息映射中定义一个条目。  
  
```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```  
  
### <a name="parameters"></a>参数  
 `theChainMember`  
 [in]包含的消息映射的数据成员的名称。  
  
 `msgMapID`  
 [in]消息映射标识符。  
  
### <a name="remarks"></a>备注  
 `CHAIN_MSG_MAP_ALT_MEMBER`数据成员中，直接将消息传递到替换消息映射。 您必须声明与此替换消息映射[ALT_MSG_MAP(msgMapID)](#alt_msg_map)。 若要将消息定向到的数据成员默认消息映射 (使用声明[BEGIN_MSG_MAP](#begin_msg_map))，使用`CHAIN_MSG_MAP_MEMBER`。 有关示例，请参阅[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)。  
  
> [!NOTE]
>  始终以与消息映射`BEGIN_MSG_MAP`。 然后，您可以声明与后续的备用消息映射`ALT_MSG_MAP`。 [END_MSG_MAP](#end_msg_map)宏标记的消息映射的末尾。 每个消息映射必须有且仅一个实例的`BEGIN_MSG_MAP`和`END_MSG_MAP`。  
  
 有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。  
  
### <a name="requirements"></a>要求  
 **标头︰** atlwin.h   
  
##  <a name="chain_msg_map"></a>CHAIN_MSG_MAP  
 消息映射中定义一个条目。  
  
```
CHAIN_MSG_MAP(theChainClass)
```  
  
### <a name="parameters"></a>参数  
 `theChainClass`  
 [in]包含的消息映射的类的基类的名称。  
  
### <a name="remarks"></a>备注  
 `CHAIN_MSG_MAP`直接将消息传递到基类的默认消息映射 (使用声明[BEGIN_MSG_MAP](#begin_msg_map))。 若要将消息定向到基类的备用消息映射 (使用声明[ALT_MSG_MAP](#alt_msg_map))，使用[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)。  
  
> [!NOTE]
>  始终以与消息映射`BEGIN_MSG_MAP`。 然后，您可以声明与后续的备用消息映射`ALT_MSG_MAP`。 [END_MSG_MAP](#end_msg_map)宏标记的消息映射的末尾。 每个消息映射必须有且仅一个实例的`BEGIN_MSG_MAP`和`END_MSG_MAP`。  
  
 有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&107; 页](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]  
  
 此示例阐释了以下︰  
  
-   如果使用的窗口过程`CMyClass`的默认消息映射和`OnPaint`处理消息，该消息定向到`CMyBaseClass`的默认值以进行处理的消息映射。  
  
-   窗口过程是否正在使用中的第一个替换消息映射`CMyClass`，所有消息都定向到`CMyBaseClass`的默认消息映射。  
  
-   如果使用的窗口过程`CMyClass`的第二个替换消息映射和`OnChar`处理消息，该消息定向到指定的备用消息映射中`CMyBaseClass`。 `CMyBaseClass`必须与此消息映射声明`ALT_MSG_MAP(1)`。  
  
### <a name="requirements"></a>要求  
 **标头︰** atlwin.h   
  
##  <a name="chain_msg_map_dynamic"></a>CHAIN_MSG_MAP_DYNAMIC  
 消息映射中定义一个条目。  
  
```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```  
  
### <a name="parameters"></a>参数  
 *dynaChainID*  
 [in]对象的消息映射唯一标识符。  
  
### <a name="remarks"></a>备注  
 `CHAIN_MSG_MAP_DYNAMIC`直接将消息传递，在运行时，到另一个对象中的默认消息映射。 与之关联的对象以及其消息映射*dynaChainID*，它们通过定义[CDynamicChain::SetChainEntry](cdynamicchain-class.md#setchainentry)。 您必须派生您的类从`CDynamicChain`为了使用`CHAIN_MSG_MAP_DYNAMIC`。 有关示例，请参阅[CDynamicChain](../../atl/reference/cdynamicchain-class.md)概述。  

  
> [!NOTE]
>  始终以与消息映射[BEGIN_MSG_MAP](#begin_msg_map)。 然后，您可以声明与后续的备用消息映射`ALT_MSG_MAP`。 [END_MSG_MAP](#end_msg_map)宏标记的消息映射的末尾。 每个消息映射必须有且仅一个实例的`BEGIN_MSG_MAP`和`END_MSG_MAP`。  
  
 有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。  
  
### <a name="requirements"></a>要求  
 **标头︰** atlwin.h   
  
##  <a name="chain_msg_map_member"></a>CHAIN_MSG_MAP_MEMBER  
 消息映射中定义一个条目。  
  
```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```  
  
### <a name="parameters"></a>参数  
 `theChainMember`  
 [in]包含的消息映射的数据成员的名称。  
  
### <a name="remarks"></a>备注  
 `CHAIN_MSG_MAP_MEMBER`直接将消息传递到数据成员的默认消息映射 (使用声明[BEGIN_MSG_MAP](#begin_msg_map))。 若要将消息定向到的数据成员替换消息映射 (使用声明[ALT_MSG_MAP](#alt_msg_map))，使用[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)。  
  
> [!NOTE]
>  始终以与消息映射`BEGIN_MSG_MAP`。 然后，您可以声明与后续的备用消息映射`ALT_MSG_MAP`。 [END_MSG_MAP](#end_msg_map)宏标记的消息映射的末尾。 每个消息映射必须有且仅一个实例的`BEGIN_MSG_MAP`和`END_MSG_MAP`。  
  
 有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&108;](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]  
  
 此示例阐释了以下︰  
  
-   如果使用的窗口过程`CMyClass`的默认消息映射和`OnPaint`处理消息，该消息定向到`m_obj`的默认值以进行处理的消息映射。  
  
-   窗口过程是否正在使用中的第一个替换消息映射`CMyClass`，所有消息都定向到`m_obj`的默认消息映射。  
  
-   如果使用的窗口过程`CMyClass`的第二个替换消息映射和`OnChar`处理消息，该消息定向到指定的备用消息映射的`m_obj`。 类`CMyContainedClass`必须与此消息映射声明`ALT_MSG_MAP(1)`。  
  
### <a name="requirements"></a>要求  
 **标头︰** atlwin.h   
  
##  <a name="command_code_handler"></a>COMMAND_CODE_HANDLER  
 类似于[COMMAND_HANDLER](#command_handler)，但映射[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)消息仅根据通知代码。  
  
```
COMMAND_CODE_HANDLER(code, func)
```  
  
### <a name="parameters"></a>参数  
 `code`  
 [in]通知代码中。  
  
 `func`  
 [in]消息处理程序函数的名称。  
  
### <a name="requirements"></a>要求  
 **标头︰** atlwin.h   
  
##  <a name="command_handler"></a>COMMAND_HANDLER  
 消息映射中定义一个条目。  
  
```
COMMAND_HANDLER(id, code, func)
```    
  
### <a name="parameters"></a>参数  
 `id`  
 [in]菜单项、 控件或加速器的标识符。  
  
 `code`  
 [in]通知代码中。  
  
 `func`  
 [in]消息处理程序函数的名称。  
  
### <a name="remarks"></a>备注  
 `COMMAND_HANDLER`映射[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)给指定的处理程序函数，基于通知代码和控件标识符的消息。 例如:   
  
 [!code-cpp[NVC_ATL_Windowing #&119;](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]  
  
 中指定任何函数`COMMAND_HANDLER`必须定义宏，如下所示︰  
  
 `LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`  
  
 消息映射集`bHandled`到**TRUE**之前`CommandHandler`调用。 如果`CommandHandler`完全不处理消息，它应设置`bHandled`到**FALSE**来指示消息需要进一步处理。  
  
> [!NOTE]
>  始终以与消息映射[BEGIN_MSG_MAP](#begin_msg_map)。 然后，您可以声明与后续的备用消息映射[ALT_MSG_MAP](#alt_msg_map)。 [END_MSG_MAP](#end_msg_map)宏标记的消息映射的末尾。 每个消息映射必须有且仅一个实例的`BEGIN_MSG_MAP`和`END_MSG_MAP`。  
  
 除了`COMMAND_HANDLER`，您可以使用[MESSAGE_HANDLER](#message_handler)映射**WM_COMMAND**而无需考虑标识符或代码的消息。 在这种情况下，`MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)`将会引导所有**WM_COMMAND**向消息`OnHandlerFunction`。  
  
 有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。  
  
### <a name="requirements"></a>要求  
 **标头︰** atlwin.h   
  
##  <a name="command_id_handler"></a>COMMAND_ID_HANDLER  
 类似于[COMMAND_HANDLER](#command_handler)，但映射[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)消息仅根据菜单项、 控件或加速器的标识符。  
  
```
COMMAND_ID_HANDLER(id, func)
```  
  
### <a name="parameters"></a>参数  
 `id`  
 [in]菜单项、 控件或加速器发送消息的标识符。  
  
 `func`  
 [in]消息处理程序函数的名称。  
  
### <a name="requirements"></a>要求  
 **标头︰** atlwin.h   
  
##  <a name="command_range_code_handler"></a>COMMAND_RANGE_CODE_HANDLER  
 类似于[COMMAND_RANGE_HANDLER](#command_range_handler)，但映射[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)具有通过一系列的控件对单个处理程序函数的特定通知代码的消息。  
  
```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```    
  
### <a name="parameters"></a>参数  
 `idFirst`  
 [in]标记一个连续控件标识符的范围的开始。  
  
 `idLast`  
 [in]标记一个连续控件标识符的范围的末尾。  
  
 `code`  
 [in]通知代码中。  
  
 `func`  
 [in]消息处理程序函数的名称。  
  
### <a name="remarks"></a>备注  
 此范围取决于菜单项、 控件或加速器发送消息的标识符。  
  
### <a name="requirements"></a>要求  
 **标头︰** atlwin.h   
  
##  <a name="command_range_handler"></a>COMMAND_RANGE_HANDLER  
 类似于[COMMAND_HANDLER](#command_handler)，但映射[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)通过一系列的控件对单个处理程序函数的消息。  
  
```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```    
  
### <a name="parameters"></a>参数  
 `idFirst`  
 [in]标记一个连续控件标识符的范围的开始。  
  
 `idLast`  
 [in]标记一个连续控件标识符的范围的末尾。  
  
 `func`  
 [in]消息处理程序函数的名称。  
  
### <a name="remarks"></a>备注  
 此范围取决于菜单项、 控件或加速器发送消息的标识符。  
  
### <a name="requirements"></a>要求  
 **标头︰** atlwin.h   
  
##  <a name="declare_empty_msg_map"></a>DECLARE_EMPTY_MSG_MAP  
 声明空消息映射。  
  
```
DECLARE_EMPTY_MSG_MAP()
```  
  
### <a name="remarks"></a>备注  
 `DECLARE_EMPTY_MSG_MAP`就是调用该宏的便利宏[BEGIN_MSG_MAP](#begin_msg_map)和[END_MSG_MAP](#end_msg_map)若要创建空消息映射︰  
  
 [!code-cpp[NVC_ATL_Windowing #&122;](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]  
  
##  <a name="default_reflection_handler"></a>DEFAULT_REFLECTION_HANDLER  
 提供的默认处理程序将收到的子窗口 （控件） 的反射消息;该处理程序能正确地传递到未处理的消息`DefWindowProc`。  
  
```
DEFAULT_REFLECTION_HANDLER()
```  
  
### <a name="requirements"></a>要求  
 **标头︰** atlwin.h   
  
##  <a name="end_msg_map"></a>END_MSG_MAP  
 将消息映射的结尾标记。  
  
```
END_MSG_MAP()
```  
  
### <a name="remarks"></a>备注  
 始终使用[BEGIN_MSG_MAP](#begin_msg_map)宏来标记消息映射的开头。 使用[ALT_MSG_MAP](#alt_msg_map)声明后续替换消息映射。  
  
 请注意，始终有恰好一个实例`BEGIN_MSG_MAP`和`END_MSG_MAP`。  
  
 有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。  
  
### <a name="example"></a>示例  
 下面的示例显示了默认的消息映射和一个替换消息映射中，每个都包含一个处理程序函数︰  
  
 [!code-cpp[NVC_ATL_Windowing #&98;](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]  
  
 下面的示例演示两个替换消息映射。 默认消息映射为空。  
  
 [!code-cpp[NVC_ATL_Windowing #&99;](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]  
  
### <a name="requirements"></a>要求  
 **标头︰** atlwin.h   
  
##  <a name="forward_notifications"></a>FORWARD_NOTIFICATIONS  
 将转发到父窗口的通知消息。  
  
```
FORWARD_NOTIFICATIONS()
```  
  
### <a name="remarks"></a>备注  
 指定此宏作为消息映射的一部分。  
  
### <a name="requirements"></a>要求  
 **标头︰** atlwin.h   
  
##  <a name="message_handler"></a>MESSAGE_HANDLER  
 消息映射中定义一个条目。  
  
```
MESSAGE_HANDLER( msg, func )
```  
  
### <a name="parameters"></a>参数  
 `msg`  
 [in]Windows 消息中。  
  
 `func`  
 [in]消息处理程序函数的名称。  
  
### <a name="remarks"></a>备注  
 `MESSAGE_HANDLER`将 Windows 消息映射到指定的处理程序函数。  
  
 中指定任何函数`MESSAGE_HANDLER`必须定义宏，如下所示︰  
  
 `LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`  
  
 消息映射集`bHandled`到**TRUE**之前`MessageHandler`调用。 如果`MessageHandler`完全不处理消息，它应设置`bHandled`到**FALSE**来指示消息需要进一步处理。  
  
> [!NOTE]
>  始终以与消息映射[BEGIN_MSG_MAP](#begin_msg_map)。 然后，您可以声明与后续的备用消息映射[ALT_MSG_MAP](#alt_msg_map)。 [END_MSG_MAP](#end_msg_map)宏标记的消息映射的末尾。 每个消息映射必须有且仅一个实例的`BEGIN_MSG_MAP`和`END_MSG_MAP`。  
  
 除了`MESSAGE_HANDLER`，您可以使用[COMMAND_HANDLER](#command_handler)和[NOTIFY_HANDLER](#notify_handler)映射[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)和[WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)分别消息。  
  
 有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&129;](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]  
  
### <a name="requirements"></a>要求  
 **标头︰** atlwin.h   
  
##  <a name="message_range_handler"></a>MESSAGE_RANGE_HANDLER  
 类似于[MESSAGE_HANDLER](#message_handler)，但映射到单个处理程序函数的范围的 Windows 消息。  
  
```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```  
  
### <a name="parameters"></a>参数  
 *msgFirst*  
 [in]标记一组连续的消息的开始。  
  
 *msgLast*  
 [in]将标记一组连续的消息的末尾。  
  
 `func`  
 [in]消息处理程序函数的名称。  
  
### <a name="requirements"></a>要求  
 **标头︰** atlwin.h   
  
##  <a name="notify_code_handler"></a>NOTIFY_CODE_HANDLER  
 类似于[NOTIFY_HANDLER](#notify_handler)，但映射[WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)消息仅根据通知代码。  
  
```
NOTIFY_CODE_HANDLER(cd, func)
```  
  
### <a name="parameters"></a>参数  
 `cd`  
 [in]通知代码中。  
  
 `func`  
 [in]消息处理程序函数的名称。  
  
### <a name="requirements"></a>要求  
 **标头︰** atlwin.h   
  
##  <a name="notify_handler"></a>NOTIFY_HANDLER  
 消息映射中定义一个条目。  
  
```
NOTIFY_HANDLER( id, cd, func )
```  
  
### <a name="parameters"></a>参数  
 `id`  
 [in]发送消息的控件的标识符。  
  
 `cd`  
 [in]通知代码中。  
  
 `func`  
 [in]消息处理程序函数的名称。  
  
### <a name="remarks"></a>备注  
 `NOTIFY_HANDLER`映射[WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)给指定的处理程序函数，基于通知代码和控件标识符的消息。  
  
 中指定任何函数`NOTIFY_HANDLER`必须定义宏，如下所示︰  
  
 `LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`  
  
 消息映射集`bHandled`到**TRUE**之前`NotifyHandler`调用。 如果`NotifyHandler`完全不处理消息，它应设置`bHandled`到**FALSE**来指示消息需要进一步处理。  
  
> [!NOTE]
>  始终以与消息映射[BEGIN_MSG_MAP](#begin_msg_map)。 然后，您可以声明与后续的备用消息映射[ALT_MSG_MAP](#alt_msg_map)。 [END_MSG_MAP](#end_msg_map)宏标记的消息映射的末尾。 每个消息映射必须有且仅一个实例的`BEGIN_MSG_MAP`和`END_MSG_MAP`。  
  
 除了`NOTIFY_HANDLER`，您可以使用[MESSAGE_HANDLER](#message_handler)映射**WM_NOTIFY**而无需考虑标识符或代码的消息。 在这种情况下，`MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)`将会引导所有**WM_NOTIFY**向消息`OnHandlerFunction`。  
  
 有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&130;](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]  
  
### <a name="requirements"></a>要求  
 **标头︰** atlwin.h   
  
##  <a name="notify_id_handler"></a>NOTIFY_ID_HANDLER  
 类似于[NOTIFY_HANDLER](#notify_handler)，但映射[WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)消息仅根据控制标识符。  
  
```
NOTIFY_ID_HANDLER( id, func )
```  
  
### <a name="parameters"></a>参数  
 `id`  
 [in]发送消息的控件的标识符。  
  
 `func`  
 [in]消息处理程序函数的名称。  
  
### <a name="requirements"></a>要求  
 **标头︰** atlwin.h   
  
##  <a name="notify_range_code_handler"></a>NOTIFY_RANGE_CODE_HANDLER  
 类似于[NOTIFY_RANGE_HANDLER](#notify_range_handler)，但映射[WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)具有通过一系列的控件对单个处理程序函数的特定通知代码的消息。  
  
```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```  
  
### <a name="parameters"></a>参数  
 `idFirst`  
 [in]标记一个连续控件标识符的范围的开始。  
  
 `idLast`  
 [in]标记一个连续控件标识符的范围的末尾。  
  
 `cd`  
 [in]通知代码中。  
  
 `func`  
 [in]消息处理程序函数的名称。  
  
### <a name="remarks"></a>备注  
 此范围取决于发送消息的控件的标识符。  
  
### <a name="requirements"></a>要求  
 **标头︰** atlwin.h   
  
##  <a name="notify_range_handler"></a>NOTIFY_RANGE_HANDLER  
 类似于[NOTIFY_HANDLER](#notify_handler)，但映射[WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)通过一系列的控件对单个处理程序函数的消息。  
  
```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```  
  
### <a name="parameters"></a>参数  
 `idFirst`  
 [in]标记一个连续控件标识符的范围的开始。  
  
 `idLast`  
 [in]标记一个连续控件标识符的范围的末尾。  
  
 `func`  
 [in]消息处理程序函数的名称。  
  
### <a name="remarks"></a>备注  
 此范围取决于发送消息的控件的标识符。  
  
### <a name="requirements"></a>要求  
 **标头︰** atlwin.h   
  
##  <a name="reflect_notifications"></a>REFLECT_NOTIFICATIONS  
 反映通知消息返回到发送给它们的子窗口 （控件）。  
  
```
REFLECT_NOTIFICATIONS()
```  
  
### <a name="remarks"></a>备注  
 指定此宏作为父窗口的消息映射的一部分。  
  
### <a name="requirements"></a>要求  
 **标头︰** atlwin.h   
  
##  <a name="reflected_command_code_handler"></a>REFLECTED_COMMAND_CODE_HANDLER  
 类似于[COMMAND_CODE_HANDLER](#command_code_handler)，但将反映来自父窗口的命令映射。  
  
```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```  
  
### <a name="parameters"></a>参数  
 `code`  
 [in]通知代码中。  
  
 `func`  
 [in]消息处理程序函数的名称。  

### <a name="requirements"></a>要求  
 **标头︰** atlwin.h  
   
##  <a name="reflected_command_handler"></a>REFLECTED_COMMAND_HANDLER  
 类似于[COMMAND_HANDLER](#command_handler)，但将反映来自父窗口的命令映射。  
  
```
REFLECTED_COMMAND_HANDLER( id, code, func )
```  
  
### <a name="parameters"></a>参数  
 `id`  
 [in]菜单项、 控件或加速器的标识符。  
  
 `code`  
 [in]通知代码中。  
  
 `func`  
 [in]消息处理程序函数的名称。  

### <a name="requirements"></a>要求  
 **标头︰** atlwin.h  

##  <a name="reflected_command_id_handler"></a>REFLECTED_COMMAND_ID_HANDLER  
 类似于[COMMAND_ID_HANDLER](#command_id_handler)，但将反映来自父窗口的命令映射。  
  
```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```  
  
### <a name="parameters"></a>参数  
 `id`  
 [in]菜单项、 控件或加速器的标识符。  
  
 `func`  
 [in]消息处理程序函数的名称。  

### <a name="requirements"></a>要求  
 **标头︰** atlwin.h  

##  <a name="reflected_command_range_code_handler"></a>REFLECTED_COMMAND_RANGE_CODE_HANDLER  
 类似于[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)，但将反映来自父窗口的命令映射。  
  
```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```  
  
### <a name="parameters"></a>参数  
 `idFirst`  
 [in]标记一个连续控件标识符的范围的开始。  
  
 `idLast`  
 [in]标记一个连续控件标识符的范围的末尾。  
  
 `code`  
 [in]通知代码中。  
  
 `func`  
 [in]消息处理程序函数的名称。  

### <a name="requirements"></a>要求  
 **标头︰** atlwin.h  

##  <a name="reflected_command_range_handler"></a>REFLECTED_COMMAND_RANGE_HANDLER  
 类似于[COMMAND_RANGE_HANDLER](#command_range_handler)，但将反映来自父窗口的命令映射。  
  
```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```  
  
### <a name="parameters"></a>参数  
 `idFirst`  
 [in]标记一个连续控件标识符的范围的开始。  
  
 `idLast`  
 [in]标记一个连续控件标识符的范围的末尾。  
  
 `func`  
 [in]消息处理程序函数的名称。  

### <a name="requirements"></a>要求  
 **标头︰** atlwin.h  

##  <a name="reflected_notify_code_handler"></a>REFLECTED_NOTIFY_CODE_HANDLER  
 类似于[NOTIFY_CODE_HANDLER](#notify_code_handler)，但映射反映来自父窗口的通知。  
  
```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```  
  
### <a name="parameters"></a>参数  
 `cd`  
 [in]通知代码中。  
  
 `func`  
 [in]消息处理程序函数的名称。  

### <a name="requirements"></a>要求  
 **标头︰** atlwin.h  

##  <a name="reflected_notify_handler"></a>REFLECTED_NOTIFY_HANDLER  
 类似于[NOTIFY_HANDLER](#notify_handler)，但映射反映来自父窗口的通知。  
  
```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```  
  
### <a name="parameters"></a>参数  
 `id`  
 [in]菜单项、 控件或加速器的标识符。  
  
 `cd`  
 [in]通知代码中。  
  
 `func`  
 [in]消息处理程序函数的名称。  

### <a name="requirements"></a>要求  
 **标头︰** atlwin.h  

##  <a name="reflected_notify_id_handler"></a>REFLECTED_NOTIFY_ID_HANDLER  
 类似于[NOTIFY_ID_HANDLER](#notify_id_handler)，但映射反映来自父窗口的通知。  
  
```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```  
  
### <a name="parameters"></a>参数  
 `id`  
 [in]菜单项、 控件或加速器的标识符。  
  
 `func`  
 [in]消息处理程序函数的名称。  

### <a name="requirements"></a>要求  
 **标头︰** atlwin.h  

##  <a name="reflected_notify_range_code_handler"></a>REFLECTED_NOTIFY_RANGE_CODE_HANDLER  
 类似于[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)，但映射反映来自父窗口的通知。  
  
```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```    
  
### <a name="parameters"></a>参数  
 `idFirst`  
 [in]标记一个连续控件标识符的范围的开始。  
  
 `idLast`  
 [in]标记一个连续控件标识符的范围的末尾。  
  
 `cd`  
 [in]通知代码中。  
  
 `func`  
 [in]消息处理程序函数的名称。  
  
### <a name="requirements"></a>要求  
 **标头︰** atlwin.h   
  
##  <a name="reflected_notify_range_handler"></a>REFLECTED_NOTIFY_RANGE_HANDLER  
 类似于[NOTIFY_RANGE_HANDLER](#notify_range_handler)，但映射反映来自父窗口的通知。  
  
```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```  
  
### <a name="parameters"></a>参数  
 `idFirst`  
 [in]标记一个连续控件标识符的范围的开始。  
  
 `idLast`  
 [in]标记一个连续控件标识符的范围的末尾。  
  
 `func`  
 [in]消息处理程序函数的名称。  
  
## <a name="see-also"></a>另请参阅  
 [宏](../../atl/reference/atl-macros.md)

