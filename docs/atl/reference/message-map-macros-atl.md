---
title: 消息映射宏 (ATL)
ms.date: 11/04/2016
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
ms.assetid: eefdd546-8934-4a30-b263-9c06a8addcbd
ms.openlocfilehash: 157812fa6625869c86dd8a27156a2970a3dc8d4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326219"
---
# <a name="message-map-macros-atl"></a>消息映射宏 (ATL)

这些宏定义消息映射和条目。

|||
|-|-|
|[ALT_MSG_MAP](#alt_msg_map)|标记备用消息映射的开头。|
|[BEGIN_MSG_MAP](#begin_msg_map)|标记默认消息映射的开头。|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|链到基类中的备用消息映射。|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|链到类的数据成员中的备用消息映射。|
|[CHAIN_MSG_MAP](#chain_msg_map)|链到基类中的默认消息映射。|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|在运行时将消息映射链到另一个类中的消息映射。|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|链到类的数据成员中的默认消息映射。|
|[COMMAND_CODE_HANDLER](#command_code_handler)|根据通知代码将WM_COMMAND消息映射到处理程序函数。|
|[COMMAND_HANDLER](#command_handler)|根据通知代码和菜单项、控件或快捷键的标识符将WM_COMMAND消息映射到处理程序函数。|
|[COMMAND_ID_HANDLER](#command_id_handler)|根据菜单项、控件或快捷键的标识符将WM_COMMAND消息映射到处理程序函数。|
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|根据通知代码和连续的控制标识符范围将WM_COMMAND消息映射到处理程序函数。|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|根据连续的控制标识符范围将WM_COMMAND消息映射到处理程序函数。|
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|实现空消息映射。|
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|为未以其他方式处理的反射消息提供默认处理程序。|
|[END_MSG_MAP](#end_msg_map)|标记消息映射的末尾。|
|[FORWARD_NOTIFICATIONS](#forward_notifications)|将通知消息转发到父窗口。|
|[MESSAGE_HANDLER](#message_handler)|将 Windows 消息映射到处理程序函数。|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|将连续范围的 Windows 消息映射到处理程序函数。|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|根据通知代码将WM_NOTIFY消息映射到处理程序函数。|
|[NOTIFY_HANDLER](#notify_handler)|根据通知代码和控制标识符将WM_NOTIFY消息映射到处理程序函数。|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|根据控件标识符将WM_NOTIFY消息映射到处理程序函数。|
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|根据通知代码和连续的控制标识符范围将WM_NOTIFY消息映射到处理程序函数。|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|根据连续的控制标识符范围将WM_NOTIFY消息映射到处理程序函数。|
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|将通知消息反射回发送通知的消息。|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|根据通知代码将反射WM_COMMAND消息映射到处理程序函数。|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|根据通知代码和菜单项、控件或快捷键的标识符将反映WM_COMMAND消息映射到处理程序函数。|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|根据菜单项、控件或快捷键的标识符将反射WM_COMMAND消息映射到处理程序函数。|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|根据通知代码和连续的控制标识符范围将反映WM_COMMAND消息映射到处理程序函数。|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|根据连续的控制标识符范围将反射WM_COMMAND消息映射到处理程序函数。|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|根据通知代码将反射WM_NOTIFY消息映射到处理程序函数。|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|根据通知代码和控制标识符将反射WM_NOTIFY消息映射到处理程序函数。|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|根据控件标识符将反射WM_NOTIFY消息映射到处理程序函数。|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|根据通知代码和连续的控制标识符范围将反射WM_NOTIFY消息映射到处理程序函数。|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|根据连续的控制标识符范围将反映WM_NOTIFY消息映射到处理程序函数。|

## <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="alt_msg_map"></a><a name="alt_msg_map"></a>ALT_MSG_MAP

标记备用消息映射的开头。

```
ALT_MSG_MAP(msgMapID)
```

### <a name="parameters"></a>参数

*msgMapID*<br/>
[在]消息映射标识符。

### <a name="remarks"></a>备注

ATL 通过数字标识每个消息映射。 默认消息映射（使用BEGIN_MSG_MAP宏声明）由 0 标识。 *msgMapID*标识了备用消息映射。

消息映射用于处理发送到窗口的消息。 例如[，CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)允许您在包含对象中指定消息映射的标识符。 [然后，CContainedWindow：windowProc](ccontainedwindowt-class.md#windowproc)使用此消息映射将包含的窗口的消息定向到相应的处理程序函数或其他消息映射。 有关声明处理程序函数的宏列表，请参阅[BEGIN_MSG_MAP](#begin_msg_map)。

始终以BEGIN_MSG_MAP开始消息映射。 然后，您可以声明后续的备用消息映射。

[END_MSG_MAP](#end_msg_map)宏标记消息映射的结尾。 请注意，始终有一个BEGIN_MSG_MAP和END_MSG_MAP实例。

有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。

### <a name="example"></a>示例

下面的示例显示默认消息映射和一个备用消息映射，每个消息映射包含一个处理程序函数：

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

下一个示例显示两个备用消息映射。 默认消息映射为空。

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="begin_msg_map"></a><a name="begin_msg_map"></a>BEGIN_MSG_MAP

标记默认消息映射的开头。

```
BEGIN_MSG_MAP(theClass)
```

### <a name="parameters"></a>参数

*类*<br/>
[在]包含消息映射的类的名称。

### <a name="remarks"></a>备注

[CWindowImpl：：WindowProc](cwindowimpl-class.md#windowproc)使用默认消息映射来处理发送到窗口的消息。 消息映射将消息定向到相应的处理程序函数或其他消息映射。

以下宏将消息映射到处理程序函数。 此函数必须在*类*中定义。

|宏|说明|
|-----------|-----------------|
|[MESSAGE_HANDLER](#message_handler)|将 Windows 消息映射到处理程序函数。|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|将连续范围的 Windows 消息映射到处理程序函数。|
|[COMMAND_HANDLER](#command_handler)|根据通知代码和菜单项、控件或快捷键的标识符将WM_COMMAND消息映射到处理程序函数。|
|[COMMAND_ID_HANDLER](#command_id_handler)|根据菜单项、控件或快捷键的标识符将WM_COMMAND消息映射到处理程序函数。|
|[COMMAND_CODE_HANDLER](#command_handler)|根据通知代码将WM_COMMAND消息映射到处理程序函数。|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|根据菜单项、控件或快捷键的标识符将WM_COMMAND消息的连续范围映射到处理程序函数。|
|[NOTIFY_HANDLER](#notify_handler)|根据通知代码和控制标识符将WM_NOTIFY消息映射到处理程序函数。|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|根据控件标识符将WM_NOTIFY消息映射到处理程序函数。|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|根据通知代码将WM_NOTIFY消息映射到处理程序函数。|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|根据控件标识符将WM_NOTIFY消息的连续范围映射到处理程序函数。|

以下宏将消息定向到另一个消息映射。 此过程称为"链接"。

|宏|说明|
|-----------|-----------------|
|[CHAIN_MSG_MAP](#chain_msg_map)|链到基类中的默认消息映射。|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|链到类的数据成员中的默认消息映射。|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|链到基类中的备用消息映射。|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|链到类的数据成员中的备用消息映射。|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|在运行时将默认消息映射链到另一个类中。|

以下宏直接从父窗口"反射"消息。 例如，控件通常向其父窗口发送通知消息进行处理，但父窗口可以将消息反射回控件。

|宏|说明|
|-----------|-----------------|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|根据通知代码和菜单项、控件或快捷键的标识符将反映WM_COMMAND消息映射到处理程序函数。|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|根据菜单项、控件或快捷键的标识符将反射WM_COMMAND消息映射到处理程序函数。|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|根据通知代码将反射WM_COMMAND消息映射到处理程序函数。|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|根据连续的控制标识符范围将反射WM_COMMAND消息映射到处理程序函数。|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|根据通知代码和连续的控制标识符范围将反映WM_COMMAND消息映射到处理程序函数。|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|根据通知代码和控制标识符将反射WM_NOTIFY消息映射到处理程序函数。|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|根据控件标识符将反射WM_NOTIFY消息映射到处理程序函数。|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|根据通知代码将反射WM_NOTIFY消息映射到处理程序函数。|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|根据连续的控制标识符范围将反映WM_NOTIFY消息映射到处理程序函数。|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|根据通知代码和连续的控制标识符范围将反射WM_NOTIFY消息映射到处理程序函数。|

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#102](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]

当`CMyExtWindow`对象收到WM_PAINT消息时，消息将定向到`CMyExtWindow::OnPaint`进行实际处理。 如果`OnPaint`指示邮件需要进一步处理，则消息将定向到 中的`CMyBaseWindow`默认消息映射。

除了默认消息映射之外，还可以使用[ALT_MSG_MAP](#alt_msg_map)定义备用消息映射。 始终以BEGIN_MSG_MAP开始消息映射。 然后，您可以声明后续的备用消息映射。 下面的示例显示默认消息映射和一个备用消息映射，每个消息映射包含一个处理程序函数：

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

下一个示例显示两个备用消息映射。 默认消息映射为空。

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

[END_MSG_MAP](#end_msg_map)宏标记消息映射的结尾。 请注意，始终有一个BEGIN_MSG_MAP和END_MSG_MAP实例。

有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="chain_msg_map_alt"></a><a name="chain_msg_map_alt"></a>CHAIN_MSG_MAP_ALT

定义消息映射中的条目。

```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```

### <a name="parameters"></a>参数

*链类*<br/>
[在]包含消息映射的基类的名称。

*msgMapID*<br/>
[在]消息映射标识符。

### <a name="remarks"></a>备注

CHAIN_MSG_MAP_ALT将消息定向到基类中的备用消息映射。 您必须已使用[ALT_MSG_MAP （msgMapID）](#alt_msg_map)声明此备用消息映射。 要将消息定向到基类的默认消息映射（使用[BEGIN_MSG_MAP](#begin_msg_map)声明），请使用CHAIN_MSG_MAP。 例如，请参阅[CHAIN_MSG_MAP](#chain_msg_map)。

> [!NOTE]
> 始终以BEGIN_MSG_MAP开始消息映射。 然后，您可以使用ALT_MSG_MAP声明后续备用消息映射。 [END_MSG_MAP](#end_msg_map)宏标记消息映射的结尾。 每个消息映射必须具有BEGIN_MSG_MAP和END_MSG_MAP的一个实例。

有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="chain_msg_map_alt_member"></a><a name="chain_msg_map_alt_member"></a>CHAIN_MSG_MAP_ALT_MEMBER

定义消息映射中的条目。

```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```

### <a name="parameters"></a>参数

*链会员*<br/>
[在]包含消息映射的数据成员的名称。

*msgMapID*<br/>
[在]消息映射标识符。

### <a name="remarks"></a>备注

CHAIN_MSG_MAP_ALT_MEMBER将消息定向到数据成员中的备用消息映射。 您必须已使用[ALT_MSG_MAP （msgMapID）](#alt_msg_map)声明此备用消息映射。 要将消息定向到数据成员的默认消息映射（使用[BEGIN_MSG_MAP](#begin_msg_map)声明），请使用CHAIN_MSG_MAP_MEMBER。 例如，请参阅[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)。

> [!NOTE]
> 始终以BEGIN_MSG_MAP开始消息映射。 然后，您可以使用ALT_MSG_MAP声明后续备用消息映射。 [END_MSG_MAP](#end_msg_map)宏标记消息映射的结尾。 每个消息映射必须具有BEGIN_MSG_MAP和END_MSG_MAP的一个实例。

有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="chain_msg_map"></a><a name="chain_msg_map"></a>CHAIN_MSG_MAP

定义消息映射中的条目。

```
CHAIN_MSG_MAP(theChainClass)
```

### <a name="parameters"></a>参数

*链类*<br/>
[在]包含消息映射的基类的名称。

### <a name="remarks"></a>备注

CHAIN_MSG_MAP将消息定向到基类的默认消息映射（用[BEGIN_MSG_MAP](#begin_msg_map)声明）。 要将消息定向到基类的备用消息映射（用[ALT_MSG_MAP](#alt_msg_map)声明），请使用[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)。

> [!NOTE]
> 始终以BEGIN_MSG_MAP开始消息映射。 然后，您可以使用ALT_MSG_MAP声明后续备用消息映射。 [END_MSG_MAP](#end_msg_map)宏标记消息映射的结尾。 每个消息映射必须具有BEGIN_MSG_MAP和END_MSG_MAP的一个实例。

有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#107](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]

此示例说明了以下内容：

- 如果窗口过程使用`CMyClass`''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''' `OnPaint` `CMyBaseClass`

- 如果窗口过程使用 中`CMyClass`的第一个备用消息映射，则所有消息都定向`CMyBaseClass`到 默认消息映射。

- 如果窗口过程使用`CMyClass`的第二个备用消息映射，并且`OnChar`不处理消息，则消息将定向到 中的`CMyBaseClass`指定备用消息映射。 `CMyBaseClass`必须已用 ALT_MSG_MAP （1） 声明此消息映射。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="chain_msg_map_dynamic"></a><a name="chain_msg_map_dynamic"></a>CHAIN_MSG_MAP_DYNAMIC

定义消息映射中的条目。

```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```

### <a name="parameters"></a>参数

*迪纳链ID*<br/>
[在]对象的消息映射的唯一标识符。

### <a name="remarks"></a>备注

CHAIN_MSG_MAP_DYNAMIC在运行时将消息定向到另一个对象的默认消息映射。 对象及其消息映射与*dynaChainID*相关联，通过[CDynamicChain：setChainEntry](cdynamicchain-class.md#setchainentry)进行定义。 为了使用CHAIN_MSG_MAP_DYNAMIC，必须派生`CDynamicChain`类。 例如，请参阅[CDynamicChain](../../atl/reference/cdynamicchain-class.md)概述。

> [!NOTE]
> 始终以[BEGIN_MSG_MAP](#begin_msg_map)开始消息映射。 然后，您可以使用ALT_MSG_MAP声明后续备用消息映射。 [END_MSG_MAP](#end_msg_map)宏标记消息映射的结尾。 每个消息映射必须具有BEGIN_MSG_MAP和END_MSG_MAP的一个实例。

有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="chain_msg_map_member"></a><a name="chain_msg_map_member"></a>CHAIN_MSG_MAP_MEMBER

定义消息映射中的条目。

```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```

### <a name="parameters"></a>参数

*链会员*<br/>
[在]包含消息映射的数据成员的名称。

### <a name="remarks"></a>备注

CHAIN_MSG_MAP_MEMBER将消息定向到数据成员的默认消息映射（使用[BEGIN_MSG_MAP](#begin_msg_map)声明）。 要将消息定向到数据成员的备用消息映射（用[ALT_MSG_MAP](#alt_msg_map)声明），请使用[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)。

> [!NOTE]
> 始终以BEGIN_MSG_MAP开始消息映射。 然后，您可以使用ALT_MSG_MAP声明后续备用消息映射。 [END_MSG_MAP](#end_msg_map)宏标记消息映射的结尾。 每个消息映射必须具有BEGIN_MSG_MAP和END_MSG_MAP的一个实例。

有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#108](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]

此示例说明了以下内容：

- 如果窗口过程使用`CMyClass`''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''' `OnPaint` `m_obj`

- 如果窗口过程使用 中`CMyClass`的第一个备用消息映射，则所有消息都定向`m_obj`到 默认消息映射。

- 如果窗口过程使用`CMyClass`的第二个备用消息映射，并且`OnChar`不处理消息，则消息将定向到`m_obj`指定的备用消息映射。 类`CMyContainedClass`必须用ALT_MSG_MAP（1）声明此消息映射。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="command_code_handler"></a><a name="command_code_handler"></a>COMMAND_CODE_HANDLER

与[COMMAND_HANDLER](#command_handler)类似 ，但仅根据通知代码映射[WM_COMMAND](/windows/win32/menurc/wm-command)消息。

```
COMMAND_CODE_HANDLER(code, func)
```

### <a name="parameters"></a>参数

*代码*<br/>
[在]通知代码。

*func*<br/>
[在]消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="command_handler"></a><a name="command_handler"></a>COMMAND_HANDLER

定义消息映射中的条目。

```
COMMAND_HANDLER(id, code, func)
```

### <a name="parameters"></a>参数

*id*<br/>
[在]菜单项、控件或快捷键的标识符。

*代码*<br/>
[在]通知代码。

*func*<br/>
[在]消息处理程序函数的名称。

### <a name="remarks"></a>备注

COMMAND_HANDLER根据通知代码和控制标识符将[WM_COMMAND](/windows/win32/menurc/wm-command)消息映射到指定的处理程序函数。 例如：

[!code-cpp[NVC_ATL_Windowing#119](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]

COMMAND_HANDLER宏中指定的任何函数必须定义如下：

`LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`

在调用之前`CommandHandler`，`bHandled`消息映射集到 TRUE。 如果未`CommandHandler`完全处理消息，则应将其设置为`bHandled`FALSE 以指示邮件需要进一步处理。

> [!NOTE]
> 始终以[BEGIN_MSG_MAP](#begin_msg_map)开始消息映射。 然后，您可以使用[ALT_MSG_MAP](#alt_msg_map)声明后续备用消息映射。 [END_MSG_MAP](#end_msg_map)宏标记消息映射的结尾。 每个消息映射必须具有BEGIN_MSG_MAP和END_MSG_MAP的一个实例。

除了COMMAND_HANDLER之外，您还可以使用[MESSAGE_HANDLER](#message_handler)来映射WM_COMMAND消息，而不考虑标识符或代码。 在这种情况下，`MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)`将所有WM_COMMAND消息定向到`OnHandlerFunction`。

有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="command_id_handler"></a><a name="command_id_handler"></a>COMMAND_ID_HANDLER

与[COMMAND_HANDLER](#command_handler)类似，但仅根据菜单项、控件或快捷键的标识符映射[WM_COMMAND](/windows/win32/menurc/wm-command)消息。

```
COMMAND_ID_HANDLER(id, func)
```

### <a name="parameters"></a>参数

*id*<br/>
[在]发送消息的菜单项、控件或快捷键的标识符。

*func*<br/>
[在]消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="command_range_code_handler"></a><a name="command_range_code_handler"></a>COMMAND_RANGE_CODE_HANDLER

与[COMMAND_RANGE_HANDLER](#command_range_handler)类似，但使用具有特定通知代码[的消息WM_COMMAND](/windows/win32/menurc/wm-command)消息从一系列控件映射到单个处理程序函数。

```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```

### <a name="parameters"></a>参数

*idFirst*<br/>
[在]标记连续控制标识符范围的开始。

*idLast*<br/>
[在]标记连续控制标识符范围的结束。

*代码*<br/>
[在]通知代码。

*func*<br/>
[在]消息处理程序函数的名称。

### <a name="remarks"></a>备注

此范围基于发送消息的菜单项、控件或快捷键的标识符。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="command_range_handler"></a><a name="command_range_handler"></a>COMMAND_RANGE_HANDLER

与[COMMAND_HANDLER](#command_handler)类似，但将[WM_COMMAND](/windows/win32/menurc/wm-command)消息从一系列控件映射到单个处理程序函数。

```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```

### <a name="parameters"></a>参数

*idFirst*<br/>
[在]标记连续控制标识符范围的开始。

*idLast*<br/>
[在]标记连续控制标识符范围的结束。

*func*<br/>
[在]消息处理程序函数的名称。

### <a name="remarks"></a>备注

此范围基于发送消息的菜单项、控件或快捷键的标识符。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="declare_empty_msg_map"></a><a name="declare_empty_msg_map"></a>DECLARE_EMPTY_MSG_MAP

声明空消息映射。

```
DECLARE_EMPTY_MSG_MAP()
```

### <a name="remarks"></a>备注

DECLARE_EMPTY_MSG_MAP是一个方便的宏，用于调用宏[BEGIN_MSG_MAP，](#begin_msg_map)[并END_MSG_MAP](#end_msg_map)创建空消息映射：

[!code-cpp[NVC_ATL_Windowing#122](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]

## <a name="default_reflection_handler"></a><a name="default_reflection_handler"></a>DEFAULT_REFLECTION_HANDLER

为将接收反射消息的子窗口（控件）提供默认处理程序;处理程序将正确将未处理的消息传递给`DefWindowProc`。

```
DEFAULT_REFLECTION_HANDLER()
```

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="end_msg_map"></a><a name="end_msg_map"></a>END_MSG_MAP

标记消息映射的末尾。

```
END_MSG_MAP()
```

### <a name="remarks"></a>备注

始终使用[BEGIN_MSG_MAP](#begin_msg_map)宏来标记消息映射的开头。 使用[ALT_MSG_MAP](#alt_msg_map)声明后续备用消息映射。

请注意，始终有一个BEGIN_MSG_MAP和END_MSG_MAP实例。

有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。

### <a name="example"></a>示例

下面的示例显示默认消息映射和一个备用消息映射，每个消息映射包含一个处理程序函数：

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

下一个示例显示两个备用消息映射。 默认消息映射为空。

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="forward_notifications"></a><a name="forward_notifications"></a>FORWARD_NOTIFICATIONS

将通知消息转发到父窗口。

```
FORWARD_NOTIFICATIONS()
```

### <a name="remarks"></a>备注

将此宏指定为消息映射的一部分。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="message_handler"></a><a name="message_handler"></a>MESSAGE_HANDLER

定义消息映射中的条目。

```
MESSAGE_HANDLER( msg, func )
```

### <a name="parameters"></a>参数

*味精*<br/>
[在]"窗口"消息。

*func*<br/>
[在]消息处理程序函数的名称。

### <a name="remarks"></a>备注

MESSAGE_HANDLER将 Windows 消息映射到指定的处理程序函数。

MESSAGE_HANDLER宏中指定的任何函数必须定义如下：

`LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`

在调用之前`MessageHandler`，`bHandled`消息映射集到 TRUE。 如果未`MessageHandler`完全处理消息，则应将其设置为`bHandled`FALSE 以指示邮件需要进一步处理。

> [!NOTE]
> 始终以[BEGIN_MSG_MAP](#begin_msg_map)开始消息映射。 然后，您可以使用[ALT_MSG_MAP](#alt_msg_map)声明后续备用消息映射。 [END_MSG_MAP](#end_msg_map)宏标记消息映射的结尾。 每个消息映射必须具有BEGIN_MSG_MAP和END_MSG_MAP的一个实例。

除了MESSAGE_HANDLER之外，您还可以使用[COMMAND_HANDLER](#command_handler)和[NOTIFY_HANDLER](#notify_handler)分别映射[WM_COMMAND](/windows/win32/menurc/wm-command)和[WM_NOTIFY](/windows/win32/controls/wm-notify)消息。

有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#129](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="message_range_handler"></a><a name="message_range_handler"></a>MESSAGE_RANGE_HANDLER

与[MESSAGE_HANDLER](#message_handler)类似，但将一系列 Windows 消息映射到单个处理程序函数。

```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```

### <a name="parameters"></a>参数

*msgFirst*<br/>
[在]标记连续消息范围的开始。

*msgLast*<br/>
[在]标记连续消息范围的结束。

*func*<br/>
[在]消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="notify_code_handler"></a><a name="notify_code_handler"></a>NOTIFY_CODE_HANDLER

与[NOTIFY_HANDLER](#notify_handler)类似，但仅根据通知代码映射[WM_NOTIFY](/windows/win32/controls/wm-notify)消息。

```
NOTIFY_CODE_HANDLER(cd, func)
```

### <a name="parameters"></a>参数

*Cd*<br/>
[在]通知代码。

*func*<br/>
[在]消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="notify_handler"></a><a name="notify_handler"></a>NOTIFY_HANDLER

定义消息映射中的条目。

```
NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>参数

*id*<br/>
[在]发送消息的控件的标识符。

*Cd*<br/>
[在]通知代码。

*func*<br/>
[在]消息处理程序函数的名称。

### <a name="remarks"></a>备注

NOTIFY_HANDLER根据通知代码和控制标识符将[WM_NOTIFY](/windows/win32/controls/wm-notify)消息映射到指定的处理程序函数。

NOTIFY_HANDLER宏中指定的任何函数必须定义如下：

`LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`

在调用之前`NotifyHandler`，`bHandled`消息映射集到 TRUE。 如果未`NotifyHandler`完全处理消息，则应将其设置为`bHandled`FALSE 以指示邮件需要进一步处理。

> [!NOTE]
> 始终以[BEGIN_MSG_MAP](#begin_msg_map)开始消息映射。 然后，您可以使用[ALT_MSG_MAP](#alt_msg_map)声明后续备用消息映射。 [END_MSG_MAP](#end_msg_map)宏标记消息映射的结尾。 每个消息映射必须具有BEGIN_MSG_MAP和END_MSG_MAP的一个实例。

除了NOTIFY_HANDLER之外，您还可以使用[MESSAGE_HANDLER](#message_handler)映射WM_NOTIFY消息，而不考虑标识符或代码。 在这种情况下，`MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)`将所有WM_NOTIFY消息定向到`OnHandlerFunction`。

有关在 ATL 中使用消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#130](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="notify_id_handler"></a><a name="notify_id_handler"></a>NOTIFY_ID_HANDLER

与[NOTIFY_HANDLER](#notify_handler)类似，但仅根据控件标识符映射[WM_NOTIFY](/windows/win32/controls/wm-notify)消息。

```
NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>参数

*id*<br/>
[在]发送消息的控件的标识符。

*func*<br/>
[在]消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="notify_range_code_handler"></a><a name="notify_range_code_handler"></a>NOTIFY_RANGE_CODE_HANDLER

与[NOTIFY_RANGE_HANDLER](#notify_range_handler)类似 ，但将具有特定通知代码[WM_NOTIFY](/windows/win32/controls/wm-notify)消息从一系列控件映射到单个处理程序函数。

```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>参数

*idFirst*<br/>
[在]标记连续控制标识符范围的开始。

*idLast*<br/>
[在]标记连续控制标识符范围的结束。

*Cd*<br/>
[在]通知代码。

*func*<br/>
[在]消息处理程序函数的名称。

### <a name="remarks"></a>备注

此范围基于发送消息的控件的标识符。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="notify_range_handler"></a><a name="notify_range_handler"></a>NOTIFY_RANGE_HANDLER

与[NOTIFY_HANDLER](#notify_handler)类似，但将[WM_NOTIFY](/windows/win32/controls/wm-notify)消息从一系列控件映射到单个处理程序函数。

```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>参数

*idFirst*<br/>
[在]标记连续控制标识符范围的开始。

*idLast*<br/>
[在]标记连续控制标识符范围的结束。

*func*<br/>
[在]消息处理程序函数的名称。

### <a name="remarks"></a>备注

此范围基于发送消息的控件的标识符。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="reflect_notifications"></a><a name="reflect_notifications"></a>REFLECT_NOTIFICATIONS

将通知消息反射回发送它们的子窗口（控件）。

```
REFLECT_NOTIFICATIONS()
```

### <a name="remarks"></a>备注

将此宏指定为父窗口的消息映射的一部分。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="reflected_command_code_handler"></a><a name="reflected_command_code_handler"></a>REFLECTED_COMMAND_CODE_HANDLER

与[COMMAND_CODE_HANDLER](#command_code_handler)类似，但映射从父窗口反射的命令。

```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```

### <a name="parameters"></a>参数

*代码*<br/>
[在]通知代码。

*func*<br/>
[在]消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="reflected_command_handler"></a><a name="reflected_command_handler"></a>REFLECTED_COMMAND_HANDLER

与[COMMAND_HANDLER](#command_handler)类似，但映射从父窗口反射的命令。

```
REFLECTED_COMMAND_HANDLER( id, code, func )
```

### <a name="parameters"></a>参数

*id*<br/>
[在]菜单项、控件或快捷键的标识符。

*代码*<br/>
[在]通知代码。

*func*<br/>
[在]消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="reflected_command_id_handler"></a><a name="reflected_command_id_handler"></a>REFLECTED_COMMAND_ID_HANDLER

与[COMMAND_ID_HANDLER](#command_id_handler)类似，但映射从父窗口反射的命令。

```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```

### <a name="parameters"></a>参数

*id*<br/>
[在]菜单项、控件或快捷键的标识符。

*func*<br/>
[在]消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="reflected_command_range_code_handler"></a><a name="reflected_command_range_code_handler"></a>REFLECTED_COMMAND_RANGE_CODE_HANDLER

与[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)类似，但映射从父窗口反射的命令。

```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```

### <a name="parameters"></a>参数

*idFirst*<br/>
[在]标记连续控制标识符范围的开始。

*idLast*<br/>
[在]标记连续控制标识符范围的结束。

*代码*<br/>
[在]通知代码。

*func*<br/>
[在]消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="reflected_command_range_handler"></a><a name="reflected_command_range_handler"></a>REFLECTED_COMMAND_RANGE_HANDLER

与[COMMAND_RANGE_HANDLER](#command_range_handler)类似，但映射从父窗口反射的命令。

```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>参数

*idFirst*<br/>
[在]标记连续控制标识符范围的开始。

*idLast*<br/>
[在]标记连续控制标识符范围的结束。

*func*<br/>
[在]消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="reflected_notify_code_handler"></a><a name="reflected_notify_code_handler"></a>REFLECTED_NOTIFY_CODE_HANDLER

与[NOTIFY_CODE_HANDLER](#notify_code_handler)类似，但映射从父窗口反映的通知。

```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```

### <a name="parameters"></a>参数

*Cd*<br/>
[在]通知代码。

*func*<br/>
[在]消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="reflected_notify_handler"></a><a name="reflected_notify_handler"></a>REFLECTED_NOTIFY_HANDLER

与[NOTIFY_HANDLER](#notify_handler)类似，但映射从父窗口反映的通知。

```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>参数

*id*<br/>
[在]菜单项、控件或快捷键的标识符。

*Cd*<br/>
[在]通知代码。

*func*<br/>
[在]消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="reflected_notify_id_handler"></a><a name="reflected_notify_id_handler"></a>REFLECTED_NOTIFY_ID_HANDLER

与[NOTIFY_ID_HANDLER](#notify_id_handler)类似，但映射从父窗口反映的通知。

```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>参数

*id*<br/>
[在]菜单项、控件或快捷键的标识符。

*func*<br/>
[在]消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="reflected_notify_range_code_handler"></a><a name="reflected_notify_range_code_handler"></a>REFLECTED_NOTIFY_RANGE_CODE_HANDLER

与[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)类似，但映射从父窗口反映的通知。

```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>参数

*idFirst*<br/>
[在]标记连续控制标识符范围的开始。

*idLast*<br/>
[在]标记连续控制标识符范围的结束。

*Cd*<br/>
[在]通知代码。

*func*<br/>
[在]消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="reflected_notify_range_handler"></a><a name="reflected_notify_range_handler"></a>REFLECTED_NOTIFY_RANGE_HANDLER

与[NOTIFY_RANGE_HANDLER](#notify_range_handler)类似，但映射从父窗口反映的通知。

```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>参数

*idFirst*<br/>
[在]标记连续控制标识符范围的开始。

*idLast*<br/>
[在]标记连续控制标识符范围的结束。

*func*<br/>
[在]消息处理程序函数的名称。

## <a name="see-also"></a>另请参阅

[宏](../../atl/reference/atl-macros.md)
