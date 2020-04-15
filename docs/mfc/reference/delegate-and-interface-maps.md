---
title: 委托和接口映射宏 （MFC）
ms.date: 03/30/2017
helpviewer_keywords:
- delegate map macros [MFC]
- event map macros [MFC]
- interface map macros [MFC]
ms.assetid: 3840e642-ff7d-4bdc-998b-c7d8fc50890e
ms.openlocfilehash: e08597d024f5e3a74dcf47363ad3de0aa60cf6c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365825"
---
# <a name="delegate-and-interface-map-macros"></a>委托和接口映射宏

MFC 支持这些宏进行委托和接口映射：

|||
|-|-|
|[BEGIN_DELEGATE_MAP](#begin_delegate_map)|开始委托映射。|
|[BEGIN_INTERFACE_MAP](#begin_interface_map)|开始定义接口映射。|
|[命令处理程序委托](#commandhandler)|向命令源注册回调方法。  |
|[END_DELEGATE_MAP](#end_delegate_map)|结束委托映射。|
|[END_INTERFACE_MAP](#end_interface_map)|终止实现文件中的接口映射。 |
|[EVENT_DELEGATE_ENTRY](#event_delegate_entry)|在委托映射中创建条目。|
|[INTERFACE_PART](#interface_part)|在BEGIN_INTERFACE_MAP宏和END_INTERFACE_MAP宏之间使用，用于对象将支持的每个接口。|
|[MAKE_DELEGATE](#make_delegate)|将事件处理程序附加到托管控件。|

## <a name="begin_delegate_map"></a><a name="begin_delegate_map"></a>BEGIN_DELEGATE_MAP

开始委托映射。

### <a name="syntax"></a>语法

```
BEGIN_DELEGATE_MAP(  CLASS );
```

### <a name="parameters"></a>参数

*类*<br/>
托管控件的类。

### <a name="remarks"></a>备注

此宏标记委托条目列表的开头，该列表组成委托映射。 有关如何使用此宏的示例，请参阅[EVENT_DELEGATE_ENTRY](#event_delegate_entry)。

### <a name="requirements"></a>要求

**标题：** msclr_event.h

## <a name="begin_interface_map"></a><a name="begin_interface_map"></a>BEGIN_INTERFACE_MAP

在实现文件中使用时开始定义接口映射。

### <a name="syntax"></a>语法

```
BEGIN_INTERFACE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>参数

*类*<br/>
要在其中定义接口映射的类

*基类*<br/>
类派生自*的*类。

### <a name="remarks"></a>备注

对于实现的每个接口，有一个或多个INTERFACE_PART宏调用。 对于类使用的每个聚合，有一个INTERFACE_AGGREGATE宏调用。

有关界面地图的详细信息，请参阅[技术说明 38](../tn038-mfc-ole-iunknown-implementation.md)。

### <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="commandhandler-delegate"></a><a name="commandhandler"></a>命令处理程序委托

向命令源注册回调方法。

### <a name="syntax"></a>语法

```
delegate void CommandHandler(  UINT^ cmdID  );
```

### <a name="parameters"></a>参数

*cmdID*<br/>
命令 ID。

### <a name="remarks"></a>备注

此委托将向命令源注册回调方法。 当您将一个委托添加到命令源对象时，回调方法将成为来自指定源的命令的处理程序。

有关详细信息，请参阅[：将命令路由添加到 Windows 窗体控件](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)。

有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

### <a name="requirements"></a>要求

**标题**：afxwinforms.h（在程序集 atlmfc_lib_mfcmc80.dll 中定义）

## <a name="commanduihandler"></a><a name="commanduihandler"></a>命令UIHandler

使用用户界面更新命令消息注册回调方法。

### <a name="syntax"></a>语法

```
delegate void CommandUIHandler(  unsigned int cmdID, ICommandUI^ cmdUI);
```

### <a name="parameters"></a>参数

*cmdID*<br/>
命令 ID。

*cmdUI*<br/>
命令消息 ID。

### <a name="remarks"></a>备注

此委托使用用户界面更新命令消息注册回调方法。 `CommandUIHandler`与[CommandHandler](#commandhandler)类似，只不过此委托与用户界面对象更新命令一起使用。 用户界面更新命令应使用消息处理程序方法一对一映射。

有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

### <a name="requirements"></a>要求

**标题**：afxwinforms.h（在程序集 atlmfc_lib_mfcmc80.dll 中定义）

## <a name="end_delegate_map"></a><a name="end_delegate_map"></a>END_DELEGATE_MAP

结束委托映射。

### <a name="syntax"></a>语法

```
END_DELEGATE_MAP();
```

### <a name="remarks"></a>备注

此宏标记委托条目列表的末尾，该列表组成委托映射。 有关如何使用此宏的示例，请参阅[EVENT_DELEGATE_ENTRY](#event_delegate_entry)。

### <a name="requirements"></a>要求

**标题：** msclr_event.h

## <a name="end_interface_map"></a><a name="end_interface_map"></a>END_INTERFACE_MAP

终止实现文件中的接口映射。

### <a name="syntax"></a>语法

```
END_INTERFACE_MAP( )
```

### <a name="remarks"></a>备注

有关界面映射的详细信息，请参阅[技术说明 38](../tn038-mfc-ole-iunknown-implementation.md)。

### <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="event_delegate_entry"></a><a name="event_delegate_entry"></a>EVENT_DELEGATE_ENTRY

在委托映射中创建条目。

### <a name="syntax"></a>语法

```
EVENT_DELEGATE_ENTRY(MEMBER, ARG0, ARG1);
```

### <a name="parameters"></a>参数

*MEMBER*<br/>
要附加到控件的事件处理程序方法。

*ARG0*<br/>
托管事件处理程序方法的第一个参数，如`Object^`。

*ARG1*<br/>
托管事件处理程序方法的第二个参数，如`EventArgs^`。

### <a name="remarks"></a>备注

委托映射中的每个条目对应于[由MAKE_DELEGATE](#make_delegate)创建的托管事件处理程序委托。

### <a name="example"></a>示例

以下代码示例演示如何使用EVENT_DELEGATE_ENTRY在`OnClick`事件处理程序的授权映射中创建条目;另请参阅MAKE_DELEGATE中的代码示例。 有关详细信息，请参阅[：从本机C++类下沉 Windows 窗体事件](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)。

```cpp
BEGIN_DELEGATE_MAP(CMyView)
   EVENT_DELEGATE_ENTRY(OnClick, System::Object^, System::EventArgs^)
END_DELEGATE_MAP()
```

### <a name="requirements"></a>要求

**标题：** msclr_event.h

## <a name="interface_part"></a><a name="interface_part"></a>INTERFACE_PART

在BEGIN_INTERFACE_MAP宏和END_INTERFACE_MAP宏之间使用，用于对象将支持的每个接口。

### <a name="syntax"></a>语法

```
INTERFACE_PART( theClass, iid, localClass)
```

### <a name="parameters"></a>参数

*类*<br/>
包含接口映射的类的名称。
*Iid*<br/>
要映射到嵌入类的 IID。
*localClass*<br/>
本地类的名称。

### <a name="remarks"></a>备注

它允许您将 IID 映射到*类*和*localClass*指示的类的成员。

有关界面地图的详细信息，请参阅[技术说明 38](../tn038-mfc-ole-iunknown-implementation.md)。

### <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="make_delegate"></a><a name="make_delegate"></a>MAKE_DELEGATE

将事件处理程序附加到托管控件。

### <a name="syntax"></a>语法

```
MAKE_DELEGATE( DELEGATE,  MEMBER) ;
```

### <a name="parameters"></a>参数

*委托*<br/>
托管事件处理程序委托的类型，如[事件处理程序](/dotnet/api/system.eventhandler)。

*MEMBER*<br/>
要附加到控件的事件处理程序方法的名称。

### <a name="remarks"></a>备注

此宏创建类型 *"代表"* 和"*成员*"名称的托管事件处理程序委托。 托管事件处理程序委托允许本机类处理托管事件。

### <a name="example"></a>示例

以下代码示例演示如何调用`MAKE_DELEGATE`将`OnClick`事件处理程序附加到 MFC 控件。 `MyControl` 有关此宏在 MFC 应用程序中工作方式的更广泛说明，请参阅[：从本机C++类沉陷 Windows 窗体事件](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)。

```cpp
// CMyView derives from CWinFormsView.
void CMyView::OnInitialUpdate()
{
   CWinFormsView::OnInitialUpdate();

   GetControl()->Click += MAKE_DELEGATE(System::EventHandler, OnClick);
}
```

### <a name="requirements"></a>要求

**标题：** msclr_event.h

## <a name="see-also"></a>另请参阅

[如何：接收来自本机 C++ 类的 Windows 窗体事件](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)<br/>
[如何：向 Windows 窗体控件添加命令传送](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[MFC 宏和全局函数](mfc-macros-and-globals.md)<br/>
