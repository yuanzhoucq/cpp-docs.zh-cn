---
title: 消息映射宏 (ATL) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlwin/ATL::ALT_MSG_MAP
- atlwin/ATL::BEGIN_MSG_MAP
- atlwin/ATL::CHAIN_MSG_MAP_ALT
- atlwin/ATL::CHAIN_MSG_MAP_ALT_MEMBER
- atlwin/ATL::CHAIN_MSG_MAP
- atlwin/ATL::CHAIN_MSG_MAP_DYNAMIC
- atlwin/ATL::CHAIN_MSG_MAP_MEMBER
- atlwin/ATL::COMMAND_CODE_HANDLER
- atlwin/ATL::COMMAND_HANDLER
- atlwin/ATL::COMMAND_ID_HANDLER
- atlwin/ATL::COMMAND_RANGE_CODE_HANDLER
- atlwin/ATL::COMMAND_RANGE_HANDLER
- atlwin/ATL::DECLARE_EMPTY_MSG_MAP
- atlwin/ATL::DEFAULT_REFLECTION_HANDLER
- atlwin/ATL::END_MSG_MAP
- atlwin/ATL::FORWARD_NOTIFICATIONS
- atlwin/ATL::MESSAGE_HANDLER
- atlwin/ATL::MESSAGE_RANGE_HANDLER
- atlwin/ATL::NOTIFY_CODE_HANDLER
- atlwin/ATL::NOTIFY_HANDLER
- atlwin/ATL::NOTIFY_ID_HANDLER
- atlwin/ATL::NOTIFY_RANGE_CODE_HANDLER
- atlwin/ATL::NOTIFY_RANGE_HANDLER
- atlwin/ATL::REFLECT_NOTIFICATIONS
- atlwin/ATL::REFLECTED_COMMAND_CODE_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_ID_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_RANGE_CODE_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_RANGE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_CODE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_ID_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_RANGE_CODE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_RANGE_HANDLER
dev_langs:
- C++
ms.assetid: eefdd546-8934-4a30-b263-9c06a8addcbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ed6e32ec0e474f901818618af662a91e3e46efed
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763693"
---
# <a name="message-map-macros-atl"></a>消息映射宏 (ATL)

这些宏定义消息映射和条目。

|||
|-|-|
|[ALT_MSG_MAP](#alt_msg_map)|标记替换消息映射的开头。|
|[BEGIN_MSG_MAP](#begin_msg_map)|表示默认消息映射的开头。|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|链接到一条替代消息映射中的基类。|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|链接到一条替代消息映射中的数据成员的类。|
|[CHAIN_MSG_MAP](#chain_msg_map)|链接至默认消息映射中的基类。|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|链接至另一个类在运行时中的消息映射。|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|链接至默认消息映射中的数据成员的类。|
|[COMMAND_CODE_HANDLER](#command_code_handler)|将 WM_COMMAND 消息映射到处理程序函数，基于通知代码。|
|[COMMAND_HANDLER](#command_handler)|将 WM_COMMAND 消息映射到处理程序函数，根据通知代码和菜单项、 控件或加速器的标识符。|
|[COMMAND_ID_HANDLER](#command_id_handler)|将 WM_COMMAND 消息映射到处理程序函数，根据菜单项、 控件或加速器的标识符。|
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|将 WM_COMMAND 消息映射到处理程序函数，根据通知代码和连续范围的控件标识符。|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|将 WM_COMMAND 消息映射到处理程序函数，基于连续范围的控件标识符。|
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|实现将空消息映射。|
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|有关反射否则未处理的消息提供默认处理程序。|
|[END_MSG_MAP](#end_msg_map)|表示消息映射的结尾。|
|[FORWARD_NOTIFICATIONS](#forward_notifications)|将转发到父窗口的通知消息。|
|[MESSAGE_HANDLER](#message_handler)|将 Windows 消息映射到处理程序函数。|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|将连续范围的 Windows 消息映射到处理程序函数。|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|将 WM_NOTIFY 消息映射到处理程序函数，基于通知代码。|
|[NOTIFY_HANDLER](#notify_handler)|将 WM_NOTIFY 消息映射到处理程序函数，根据通知代码和控件标识符。|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|将 WM_NOTIFY 消息映射到处理程序函数，基于的控件标识符。|
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|将 WM_NOTIFY 消息映射到处理程序函数，根据通知代码和连续范围的控件标识符。|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|将 WM_NOTIFY 消息映射到处理程序函数，基于连续范围的控件标识符。|
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|反映了返回到的窗口中向他们发送通知消息。|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|将反射的 WM_COMMAND 消息映射到处理程序函数，基于通知代码。|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|将反射的 WM_COMMAND 消息映射到处理程序函数，根据通知代码和菜单项、 控件或加速器的标识符。|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|将反射的 WM_COMMAND 消息映射到处理程序函数，根据菜单项、 控件或加速器的标识符。|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|将反射的 WM_COMMAND 消息映射到处理程序函数，根据通知代码和连续范围的控件标识符。|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|将反射的 WM_COMMAND 消息映射到处理程序函数，基于连续范围的控件标识符。|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|将反射的 WM_NOTIFY 消息映射到处理程序函数，基于通知代码。|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|将反射的 WM_NOTIFY 消息映射到处理程序函数，根据通知代码和控件标识符。|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|将反射的 WM_NOTIFY 消息映射到处理程序函数，基于的控件标识符。|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|将反射的 WM_NOTIFY 消息映射到处理程序函数，根据通知代码和连续范围的控件标识符。|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|将反射的 WM_NOTIFY 消息映射到处理程序函数，基于连续范围的控件标识符。|  

## <a name="requirements"></a>要求

**标头：** atlwin.h  

##  <a name="alt_msg_map"></a>  ALT_MSG_MAP

标记替换消息映射的开头。

```
ALT_MSG_MAP(msgMapID)
```

### <a name="parameters"></a>参数

*msgMapID*  
[in]消息映射标识符。

### <a name="remarks"></a>备注

ATL 标识由许多每个消息映射。 由 0 标识 （使用 BEGIN_MSG_MAP 宏声明） 的默认消息映射。 替换消息映射由*msgMapID*。

消息映射用于处理消息发送到的窗口。 例如， [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)允许您指定的包含对象中的消息映射的标识符。 [CContainedWindow::WindowProc](ccontainedwindowt-class.md#windowproc)然后，使用此消息映射将定向到相应的处理程序函数或另一个消息映射包含的窗口的消息。 声明处理程序函数的宏的列表，请参阅[BEGIN_MSG_MAP](#begin_msg_map)。

始终以具有 BEGIN_MSG_MAP 的消息映射。 然后，您可以声明后续的备用消息映射。

[END_MSG_MAP](#end_msg_map)宏标记消息映射的末尾。 请注意是始终 BEGIN_MSG_MAP 和 END_MSG_MAP 的一个实例。

有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。

### <a name="example"></a>示例

下面的示例显示默认消息映射和一个备用消息映射，每个都包含一个处理程序函数：

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

下面的示例演示两个备用消息映射。 默认消息映射为空。

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>要求

**标头：** atlwin.h   

##  <a name="begin_msg_map"></a>  BEGIN_MSG_MAP

表示默认消息映射的开头。

```
BEGIN_MSG_MAP(theClass)
```

### <a name="parameters"></a>参数

*类*  
[in]包含在消息映射的类的名称。

### <a name="remarks"></a>备注

[CWindowImpl::WindowProc](cwindowimpl-class.md#windowproc)使用默认消息映射来处理消息发送到的窗口。 消息映射将定向到相应的处理程序函数或另一个消息映射到的消息。  

下列宏将消息映射到处理程序函数。 必须在定义此函数*类*。

|宏|描述|
|-----------|-----------------|
|[MESSAGE_HANDLER](#message_handler)|将 Windows 消息映射到处理程序函数。|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|将连续范围的 Windows 消息映射到处理程序函数。|
|[COMMAND_HANDLER](#command_handler)|将 WM_COMMAND 消息映射到处理程序函数，根据通知代码和菜单项、 控件或加速器的标识符。|
|[COMMAND_ID_HANDLER](#command_id_handler)|将 WM_COMMAND 消息映射到处理程序函数，根据菜单项、 控件或加速器的标识符。|
|[COMMAND_CODE_HANDLER](#command_handler)|将 WM_COMMAND 消息映射到处理程序函数，基于通知代码。|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|将连续的 WM_COMMAND 消息映射到处理程序函数，根据菜单项、 控件或加速器的标识符。|
|[NOTIFY_HANDLER](#notify_handler)|将 WM_NOTIFY 消息映射到处理程序函数，根据通知代码和控件标识符。|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|将 WM_NOTIFY 消息映射到处理程序函数，基于的控件标识符。|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|将 WM_NOTIFY 消息映射到处理程序函数，基于通知代码。|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|将连续的 WM_NOTIFY 消息映射到处理程序函数，基于的控件标识符。|

下列宏将消息定向到另一个消息映射。 此过程称为"链接"。

|宏|描述|
|-----------|-----------------|
|[CHAIN_MSG_MAP](#chain_msg_map)|链接至默认消息映射中的基类。|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|链接至默认消息映射中的数据成员的类。|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|链接到一条替代消息映射中的基类。|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|链接到一条替代消息映射中的数据成员的类。|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|链接至另一个类在运行时中的默认消息映射。|

下列宏直接从父窗口的"反射"消息。 例如，控件通常将发送通知消息到其父窗口的处理，但父窗口可以反映返回到该控件的消息。

|宏|描述|
|-----------|-----------------|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|将反射的 WM_COMMAND 消息映射到处理程序函数，根据通知代码和菜单项、 控件或加速器的标识符。|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|将反射的 WM_COMMAND 消息映射到处理程序函数，根据菜单项、 控件或加速器的标识符。|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|将反射的 WM_COMMAND 消息映射到处理程序函数，基于通知代码。|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|将反射的 WM_COMMAND 消息映射到处理程序函数，基于连续范围的控件标识符。|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|将反射的 WM_COMMAND 消息映射到处理程序函数，根据通知代码和连续范围的控件标识符。|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|将反射的 WM_NOTIFY 消息映射到处理程序函数，根据通知代码和控件标识符。|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|将反射的 WM_NOTIFY 消息映射到处理程序函数，基于的控件标识符。|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|将反射的 WM_NOTIFY 消息映射到处理程序函数，基于通知代码。|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|将反射的 WM_NOTIFY 消息映射到处理程序函数，基于连续范围的控件标识符。|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|将反射的 WM_NOTIFY 消息映射到处理程序函数，根据通知代码和连续范围的控件标识符。|

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#102](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]

当`CMyExtWindow`对象收到 WM_PAINT 消息时，消息定向到`CMyExtWindow::OnPaint`实际处理。 如果`OnPaint`指示需要对消息进行进一步处理该消息将然后定向到的默认消息映射中`CMyBaseWindow`。

除了默认消息映射，你可以定义使用的替换消息映射[ALT_MSG_MAP](#alt_msg_map)。 始终以具有 BEGIN_MSG_MAP 的消息映射。 然后，您可以声明后续的备用消息映射。 下面的示例显示默认消息映射和一个备用消息映射，每个都包含一个处理程序函数：

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

下面的示例演示两个备用消息映射。 默认消息映射为空。

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

[END_MSG_MAP](#end_msg_map)宏标记消息映射的末尾。 请注意是始终 BEGIN_MSG_MAP 和 END_MSG_MAP 的一个实例。

有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="chain_msg_map_alt"></a>  CHAIN_MSG_MAP_ALT

消息映射中定义一个条目。

```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```

### <a name="parameters"></a>参数

*theChainClass*  
[in]包含在消息映射的基类的名称。

*msgMapID*  
[in]消息映射标识符。

### <a name="remarks"></a>备注

CHAIN_MSG_MAP_ALT 直接将替换消息映射到的消息传递在基类中。 必须声明与此备选的消息映射[ALT_MSG_MAP(msgMapID)](#alt_msg_map)。 若要将消息定向到基类的默认消息映射 (使用声明[BEGIN_MSG_MAP](#begin_msg_map))，使用 CHAIN_MSG_MAP。 有关示例，请参阅[CHAIN_MSG_MAP](#chain_msg_map)。

> [!NOTE]
>  始终以具有 BEGIN_MSG_MAP 的消息映射。 然后，可以声明具有 ALT_MSG_MAP 后续的备用消息映射。 [END_MSG_MAP](#end_msg_map)宏标记消息映射的末尾。 每个消息映射必须有且只有一个实例 BEGIN_MSG_MAP 和 END_MSG_MAP。

有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="chain_msg_map_alt_member"></a>  CHAIN_MSG_MAP_ALT_MEMBER

消息映射中定义一个条目。

```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```

### <a name="parameters"></a>参数

*theChainMember*  
[in]包含在消息映射的数据成员的名称。

*msgMapID*  
[in]消息映射标识符。

### <a name="remarks"></a>备注

CHAIN_MSG_MAP_ALT_MEMBER 直接将替换消息映射到的消息传递中的数据成员。 必须声明与此备选的消息映射[ALT_MSG_MAP(msgMapID)](#alt_msg_map)。 若要将消息定向到的数据成员的默认消息映射 (使用声明[BEGIN_MSG_MAP](#begin_msg_map))，使用 CHAIN_MSG_MAP_MEMBER。 有关示例，请参阅[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)。

> [!NOTE]
>  始终以具有 BEGIN_MSG_MAP 的消息映射。 然后，可以声明具有 ALT_MSG_MAP 后续的备用消息映射。 [END_MSG_MAP](#end_msg_map)宏标记消息映射的末尾。 每个消息映射必须有且只有一个实例 BEGIN_MSG_MAP 和 END_MSG_MAP。

有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="chain_msg_map"></a>  CHAIN_MSG_MAP

消息映射中定义一个条目。

```
CHAIN_MSG_MAP(theChainClass)
```

### <a name="parameters"></a>参数

*theChainClass*  
[in]包含在消息映射的基类的名称。

### <a name="remarks"></a>备注

CHAIN_MSG_MAP 将定向到基类的默认消息映射消息 (使用声明[BEGIN_MSG_MAP](#begin_msg_map))。 若要将消息定向到基类的备用消息映射 (使用声明[ALT_MSG_MAP](#alt_msg_map))，使用[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)。

> [!NOTE]
>  始终以具有 BEGIN_MSG_MAP 的消息映射。 然后，可以声明具有 ALT_MSG_MAP 后续的备用消息映射。 [END_MSG_MAP](#end_msg_map)宏标记消息映射的末尾。 每个消息映射必须有且只有一个实例 BEGIN_MSG_MAP 和 END_MSG_MAP。

有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#107](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]

此示例说明：

- 如果使用的窗口过程`CMyClass`的默认消息映射并`OnPaint`不会的处理消息，该消息定向到`CMyBaseClass`的默认消息映射以进行处理。

- 窗口过程正在使用中的第一个备选的消息映射`CMyClass`，所有消息都定向到`CMyBaseClass`的默认消息映射。

- 如果使用的窗口过程`CMyClass`的第二个备选的消息映射并`OnChar`不会的处理消息，该消息定向到指定的备用消息映射中`CMyBaseClass`。 `CMyBaseClass` 必须声明 ALT_MSG_MAP(1) 与此消息映射。

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="chain_msg_map_dynamic"></a>  CHAIN_MSG_MAP_DYNAMIC

消息映射中定义一个条目。

```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```

### <a name="parameters"></a>参数

*dynaChainID*  
[in]对象的消息映射为唯一标识符。

### <a name="remarks"></a>备注

CHAIN_MSG_MAP_DYNAMIC 定向消息，在运行时，到另一个对象中的默认消息映射。 与之关联的对象和其消息映射*dynaChainID*，通过定义[CDynamicChain::SetChainEntry](cdynamicchain-class.md#setchainentry)。 您必须派生您的类从`CDynamicChain`才能使用 CHAIN_MSG_MAP_DYNAMIC。 有关示例，请参阅[CDynamicChain](../../atl/reference/cdynamicchain-class.md)概述。  

> [!NOTE]
>  始终以使用消息映射[BEGIN_MSG_MAP](#begin_msg_map)。 然后，可以声明具有 ALT_MSG_MAP 后续的备用消息映射。 [END_MSG_MAP](#end_msg_map)宏标记消息映射的末尾。 每个消息映射必须有且只有一个实例 BEGIN_MSG_MAP 和 END_MSG_MAP。

有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="chain_msg_map_member"></a>  CHAIN_MSG_MAP_MEMBER

消息映射中定义一个条目。

```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```

### <a name="parameters"></a>参数

*theChainMember*  
[in]包含在消息映射的数据成员的名称。

### <a name="remarks"></a>备注

CHAIN_MSG_MAP_MEMBER 直接将数据成员的默认消息映射到的消息的传递 (使用声明[BEGIN_MSG_MAP](#begin_msg_map))。 若要将消息定向到的数据成员的备用消息映射 (使用声明[ALT_MSG_MAP](#alt_msg_map))，使用[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)。

> [!NOTE]
>  始终以具有 BEGIN_MSG_MAP 的消息映射。 然后，可以声明具有 ALT_MSG_MAP 后续的备用消息映射。 [END_MSG_MAP](#end_msg_map)宏标记消息映射的末尾。 每个消息映射必须有且只有一个实例 BEGIN_MSG_MAP 和 END_MSG_MAP。

有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#108](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]

此示例说明：

- 如果使用的窗口过程`CMyClass`的默认消息映射并`OnPaint`不会的处理消息，该消息定向到`m_obj`的默认消息映射以进行处理。

- 窗口过程正在使用中的第一个备选的消息映射`CMyClass`，所有消息都定向到`m_obj`的默认消息映射。

- 如果使用的窗口过程`CMyClass`的第二个备选的消息映射并`OnChar`不会的处理消息，该消息定向到指定的备用消息映射的`m_obj`。 类`CMyContainedClass`必须声明 ALT_MSG_MAP(1) 与此消息映射。

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="command_code_handler"></a>  COMMAND_CODE_HANDLER

类似于[COMMAND_HANDLER](#command_handler)，但映射[WM_COMMAND](/windows/desktop/menurc/wm-command)消息仅根据通知代码。

```
COMMAND_CODE_HANDLER(code, func)
```

### <a name="parameters"></a>参数

*代码*  
[in]通知代码。

*func*  
[in]消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="command_handler"></a>  COMMAND_HANDLER

消息映射中定义一个条目。

```
COMMAND_HANDLER(id, code, func)
```

### <a name="parameters"></a>参数

*id*  
[in]菜单项、 控件或加速器的标识符。

*代码*  
[in]通知代码。

*func*  
[in]消息处理程序函数的名称。

### <a name="remarks"></a>备注

映射 COMMAND_HANDLER [WM_COMMAND](/windows/desktop/menurc/wm-command)为指定的处理程序函数，根据通知代码和控件标识符的消息。 例如：

[!code-cpp[NVC_ATL_Windowing#119](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]

必须按如下所示定义 COMMAND_HANDLER 宏中指定任何函数：

`LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`

消息映射集`bHandled`为 TRUE，然后才能`CommandHandler`调用。 如果`CommandHandler`不完全处理该消息，应设置`bHandled`为 FALSE 以指示该消息需要进一步处理。

> [!NOTE]
>  始终以使用消息映射[BEGIN_MSG_MAP](#begin_msg_map)。 然后，您可以声明使用后续的备用消息映射[ALT_MSG_MAP](#alt_msg_map)。 [END_MSG_MAP](#end_msg_map)宏标记消息映射的末尾。 每个消息映射必须有且只有一个实例 BEGIN_MSG_MAP 和 END_MSG_MAP。

除了 COMMAND_HANDLER，可以使用[MESSAGE_HANDLER](#message_handler) WM_COMMAND 消息而不考虑标识符或代码映射。 在这种情况下，`MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)`会将定向到所有 WM_COMMAND 消息`OnHandlerFunction`。

有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="command_id_handler"></a>  COMMAND_ID_HANDLER

类似于[COMMAND_HANDLER](#command_handler)，但映射[WM_COMMAND](/windows/desktop/menurc/wm-command)消息仅根据菜单项、 控件或加速器的标识符。

```
COMMAND_ID_HANDLER(id, func)
```

### <a name="parameters"></a>参数

*id*  
[in]菜单项、 控件或加速器发送消息的标识符。

*func*  
[in]消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="command_range_code_handler"></a>  COMMAND_RANGE_CODE_HANDLER

类似于[COMMAND_RANGE_HANDLER](#command_range_handler)，但映射[WM_COMMAND](/windows/desktop/menurc/wm-command)含特定通知代码，通过一系列的控件的单个处理程序函数的消息。

```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```

### <a name="parameters"></a>参数

*idFirst*  
[in]表示连续范围的控件标识符的开头。

*idLast*  
[in]标记的末尾连续范围的控件标识符。

*代码*  
[in]通知代码。

*func*  
[in]消息处理程序函数的名称。

### <a name="remarks"></a>备注

此范围根据菜单项、 控件或加速器发送消息的标识符。

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="command_range_handler"></a>  COMMAND_RANGE_HANDLER

类似于[COMMAND_HANDLER](#command_handler)，但映射[WM_COMMAND](/windows/desktop/menurc/wm-command)消息从一系列控件到单个处理程序函数。

```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```

### <a name="parameters"></a>参数

*idFirst*  
[in]表示连续范围的控件标识符的开头。

*idLast*  
[in]标记的末尾连续范围的控件标识符。

*func*  
[in]消息处理程序函数的名称。

### <a name="remarks"></a>备注

此范围根据菜单项、 控件或加速器发送消息的标识符。

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="declare_empty_msg_map"></a>  DECLARE_EMPTY_MSG_MAP

声明将空消息映射。

```
DECLARE_EMPTY_MSG_MAP()
```

### <a name="remarks"></a>备注

DECLARE_EMPTY_MSG_MAP 就是调用宏的便利宏[BEGIN_MSG_MAP](#begin_msg_map)并[END_MSG_MAP](#end_msg_map)创建空消息映射：

[!code-cpp[NVC_ATL_Windowing#122](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]

##  <a name="default_reflection_handler"></a>  DEFAULT_REFLECTION_HANDLER

提供的默认处理程序将收到的子窗口 （控制） 反射消息;该处理程序将能正确地传递到未处理的消息`DefWindowProc`。

```
DEFAULT_REFLECTION_HANDLER()
```

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="end_msg_map"></a>  END_MSG_MAP

表示消息映射的结尾。

```
END_MSG_MAP()
```

### <a name="remarks"></a>备注

始终使用[BEGIN_MSG_MAP](#begin_msg_map)宏来标记消息映射的开头。 使用[ALT_MSG_MAP](#alt_msg_map)声明后续的备用消息映射。

请注意是始终 BEGIN_MSG_MAP 和 END_MSG_MAP 的一个实例。

有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。

### <a name="example"></a>示例

下面的示例显示默认消息映射和一个备用消息映射，每个都包含一个处理程序函数：

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

下面的示例演示两个备用消息映射。 默认消息映射为空。

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="forward_notifications"></a>  FORWARD_NOTIFICATIONS

将转发到父窗口的通知消息。

```
FORWARD_NOTIFICATIONS()
```

### <a name="remarks"></a>备注

指定此宏作为消息映射的一部分。

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="message_handler"></a>  MESSAGE_HANDLER

消息映射中定义一个条目。

```
MESSAGE_HANDLER( msg, func )
```

### <a name="parameters"></a>参数

*消息*  
[in]Windows 消息。

*func*  
[in]消息处理程序函数的名称。

### <a name="remarks"></a>备注

MESSAGE_HANDLER 将 Windows 消息映射到指定的处理程序函数。

必须按如下所示定义 MESSAGE_HANDLER 宏中指定任何函数：

`LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`

消息映射集`bHandled`为 TRUE，然后才能`MessageHandler`调用。 如果`MessageHandler`不完全处理该消息，应设置`bHandled`为 FALSE 以指示该消息需要进一步处理。

> [!NOTE]
>  始终以使用消息映射[BEGIN_MSG_MAP](#begin_msg_map)。 然后，您可以声明使用后续的备用消息映射[ALT_MSG_MAP](#alt_msg_map)。 [END_MSG_MAP](#end_msg_map)宏标记消息映射的末尾。 每个消息映射必须有且只有一个实例 BEGIN_MSG_MAP 和 END_MSG_MAP。

除了 MESSAGE_HANDLER，你可以使用[COMMAND_HANDLER](#command_handler)并[NOTIFY_HANDLER](#notify_handler)映射[WM_COMMAND](/windows/desktop/menurc/wm-command)并[WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)消息分别。

有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#129](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="message_range_handler"></a>  MESSAGE_RANGE_HANDLER

类似于[MESSAGE_HANDLER](#message_handler)，但映射到单个处理程序函数的范围的 Windows 消息。

```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```

### <a name="parameters"></a>参数

*msgFirst*  
[in]表示一组连续的消息的开头。

*msgLast*  
[in]表示一组连续的消息的结尾。

*func*  
[in]消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="notify_code_handler"></a>  NOTIFY_CODE_HANDLER

类似于[NOTIFY_HANDLER](#notify_handler)，但映射[WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)消息仅根据通知代码。

```
NOTIFY_CODE_HANDLER(cd, func)
```

### <a name="parameters"></a>参数

*cd*  
[in]通知代码。

*func*  
[in]消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="notify_handler"></a>  NOTIFY_HANDLER

消息映射中定义一个条目。

```
NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>参数

*id*  
[in]发送消息的控件的标识符。

*cd*  
[in]通知代码。

*func*  
[in]消息处理程序函数的名称。

### <a name="remarks"></a>备注

映射 NOTIFY_HANDLER [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)为指定的处理程序函数，根据通知代码和控件标识符的消息。

必须按如下所示定义 NOTIFY_HANDLER 宏中指定任何函数：

`LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`

消息映射集`bHandled`为 TRUE，然后才能`NotifyHandler`调用。 如果`NotifyHandler`不完全处理该消息，应设置`bHandled`为 FALSE 以指示该消息需要进一步处理。

> [!NOTE]
>  始终以使用消息映射[BEGIN_MSG_MAP](#begin_msg_map)。 然后，您可以声明使用后续的备用消息映射[ALT_MSG_MAP](#alt_msg_map)。 [END_MSG_MAP](#end_msg_map)宏标记消息映射的末尾。 每个消息映射必须有且只有一个实例 BEGIN_MSG_MAP 和 END_MSG_MAP。

除了 NOTIFY_HANDLER，可以使用[MESSAGE_HANDLER](#message_handler) WM_NOTIFY 消息而不考虑标识符或代码映射。 在这种情况下，`MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)`会将定向到所有 WM_NOTIFY 消息`OnHandlerFunction`。

有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#130](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="notify_id_handler"></a>  NOTIFY_ID_HANDLER

类似于[NOTIFY_HANDLER](#notify_handler)，但映射[WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)消息仅基于的控件标识符。

```
NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>参数

*id*  
[in]发送消息的控件的标识符。

*func*  
[in]消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="notify_range_code_handler"></a>  NOTIFY_RANGE_CODE_HANDLER

类似于[NOTIFY_RANGE_HANDLER](#notify_range_handler)，但映射[WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)含特定通知代码，通过一系列的控件的单个处理程序函数的消息。

```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>参数

*idFirst*  
[in]表示连续范围的控件标识符的开头。

*idLast*  
[in]标记的末尾连续范围的控件标识符。

*cd*  
[in]通知代码。

*func*  
[in]消息处理程序函数的名称。

### <a name="remarks"></a>备注

此范围基于发送消息的控件的标识符。

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="notify_range_handler"></a>  NOTIFY_RANGE_HANDLER

类似于[NOTIFY_HANDLER](#notify_handler)，但映射[WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)消息从一系列控件到单个处理程序函数。

```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>参数

*idFirst*  
[in]表示连续范围的控件标识符的开头。

*idLast*  
[in]标记的末尾连续范围的控件标识符。

*func*  
[in]消息处理程序函数的名称。

### <a name="remarks"></a>备注

此范围基于发送消息的控件的标识符。

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="reflect_notifications"></a>  REFLECT_NOTIFICATIONS

反映了返回到的子窗口 （控件） 的向他们发送通知消息。

```
REFLECT_NOTIFICATIONS()
```

### <a name="remarks"></a>备注

指定此宏作为父窗口的消息映射的一部分。

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="reflected_command_code_handler"></a>  REFLECTED_COMMAND_CODE_HANDLER

类似于[COMMAND_CODE_HANDLER](#command_code_handler)，但映射反映从父窗口的命令。

```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```

### <a name="parameters"></a>参数

*代码*  
[in]通知代码。

*func*  
[in]消息处理程序函数的名称。  

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="reflected_command_handler"></a>  REFLECTED_COMMAND_HANDLER

类似于[COMMAND_HANDLER](#command_handler)，但映射反映从父窗口的命令。

```
REFLECTED_COMMAND_HANDLER( id, code, func )
```

### <a name="parameters"></a>参数

*id*  
[in]菜单项、 控件或加速器的标识符。

*代码*  
[in]通知代码。

*func*  
[in]消息处理程序函数的名称。  

### <a name="requirements"></a>要求

**标头：** atlwin.h  

##  <a name="reflected_command_id_handler"></a>  REFLECTED_COMMAND_ID_HANDLER

类似于[COMMAND_ID_HANDLER](#command_id_handler)，但映射反映从父窗口的命令。

```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```

### <a name="parameters"></a>参数

*id*  
[in]菜单项、 控件或加速器的标识符。

*func*  
[in]消息处理程序函数的名称。  

### <a name="requirements"></a>要求

**标头：** atlwin.h  

##  <a name="reflected_command_range_code_handler"></a>  REFLECTED_COMMAND_RANGE_CODE_HANDLER

类似于[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)，但映射反映从父窗口的命令。

```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```

### <a name="parameters"></a>参数

*idFirst*  
[in]表示连续范围的控件标识符的开头。

*idLast*  
[in]标记的末尾连续范围的控件标识符。

*代码*  
[in]通知代码。

*func*  
[in]消息处理程序函数的名称。  

### <a name="requirements"></a>要求

**标头：** atlwin.h  

##  <a name="reflected_command_range_handler"></a>  REFLECTED_COMMAND_RANGE_HANDLER

类似于[COMMAND_RANGE_HANDLER](#command_range_handler)，但映射反映从父窗口的命令。

```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>参数

*idFirst*  
[in]表示连续范围的控件标识符的开头。

*idLast*  
[in]标记的末尾连续范围的控件标识符。

*func*  
[in]消息处理程序函数的名称。  

### <a name="requirements"></a>要求

**标头：** atlwin.h  

##  <a name="reflected_notify_code_handler"></a>  REFLECTED_NOTIFY_CODE_HANDLER

类似于[NOTIFY_CODE_HANDLER](#notify_code_handler)，但映射反映从父窗口的通知。

```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```

### <a name="parameters"></a>参数

*cd*  
[in]通知代码。

*func*  
[in]消息处理程序函数的名称。  

### <a name="requirements"></a>要求

**标头：** atlwin.h  

##  <a name="reflected_notify_handler"></a>  REFLECTED_NOTIFY_HANDLER

类似于[NOTIFY_HANDLER](#notify_handler)，但映射反映从父窗口的通知。

```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>参数

*id*  
[in]菜单项、 控件或加速器的标识符。

*cd*  
[in]通知代码。

*func*  
[in]消息处理程序函数的名称。  

### <a name="requirements"></a>要求

**标头：** atlwin.h  

##  <a name="reflected_notify_id_handler"></a>  REFLECTED_NOTIFY_ID_HANDLER

类似于[NOTIFY_ID_HANDLER](#notify_id_handler)，但映射反映从父窗口的通知。

```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>参数

*id*  
[in]菜单项、 控件或加速器的标识符。

*func*  
[in]消息处理程序函数的名称。  

### <a name="requirements"></a>要求

**标头：** atlwin.h  

##  <a name="reflected_notify_range_code_handler"></a>  REFLECTED_NOTIFY_RANGE_CODE_HANDLER

类似于[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)，但映射反映从父窗口的通知。

```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>参数

*idFirst*  
[in]表示连续范围的控件标识符的开头。

*idLast*  
[in]标记的末尾连续范围的控件标识符。

*cd*  
[in]通知代码。

*func*  
[in]消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="reflected_notify_range_handler"></a>  REFLECTED_NOTIFY_RANGE_HANDLER

类似于[NOTIFY_RANGE_HANDLER](#notify_range_handler)，但映射反映从父窗口的通知。

```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>参数

*idFirst*  
[in]表示连续范围的控件标识符的开头。

*idLast*  
[in]标记的末尾连续范围的控件标识符。

*func*  
[in]消息处理程序函数的名称。

## <a name="see-also"></a>请参阅

[宏](../../atl/reference/atl-macros.md)
