---
title: 委托和接口映射宏 (MFC)
ms.date: 03/30/2017
helpviewer_keywords:
- delegate map macros [MFC]
- event map macros [MFC]
- interface map macros [MFC]
ms.assetid: 3840e642-ff7d-4bdc-998b-c7d8fc50890e
ms.openlocfilehash: 8f48b916f7130551fc8d4da5bb2ebc75d8d728d5
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55850198"
---
# <a name="delegate-and-interface-map-macros"></a>委托和接口映射宏

MFC 支持委托和接口映射这些宏：

|||
|-|-|
|[BEGIN_DELEGATE_MAP](#begin_delegate_map)|开始委托映射。|
|[BEGIN_INTERFACE_MAP](#begin_interface_map)|开始 interfaced 映射的定义。|
|[CommandHandler Delegate](#commandhandler)|向命令源注册回调方法。  |
|[END_DELEGATE_MAP](#end_delegate_map)|结束委托映射。|
|[END_INTERFACE_MAP](#end_interface_map)|终止实现文件中的接口映射。 |
|[EVENT_DELEGATE_ENTRY](#event_delegate_entry)|在委托映射中创建条目。|
|[INTERFACE_PART](#interface_part)|BEGIN_INTERFACE_MAP 宏和 END_INTERFACE_MAP 宏之间使用的每个接口将支持您的对象。|
|[MAKE_DELEGATE](#make_delegate)|将事件处理程序附加到的托管控件。|

## <a name="begin_delegate_map"></a> BEGIN_DELEGATE_MAP

开始委托映射。

### <a name="syntax"></a>语法

```
BEGIN_DELEGATE_MAP(  CLASS );
```

### <a name="parameters"></a>参数

*CLASS*<br/>
在其中承载托管的控件的类。

### <a name="remarks"></a>备注

此宏将标记的委托条目，组合委托映射列表的开头。 有关如何使用此宏的示例，请参阅[EVENT_DELEGATE_ENTRY](#event_delegate_entry)。

### <a name="requirements"></a>要求

**标头：** msclr\event.h

##  <a name="begin_interface_map"></a>BEGIN_INTERFACE_MAP

开始 interfaced 映射时实现文件中使用的定义。

### <a name="syntax"></a>语法

```
BEGIN_INTERFACE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>参数

*theClass*<br/>
要在其中定义接口映射的类

*baseClass*<br/>
从其类*类*派生。

### <a name="remarks"></a>备注

对于每个实现的接口，没有一个或多个 INTERFACE_PART 宏调用。 对于每个类使用的聚合，没有一个 INTERFACE_AGGREGATE 宏调用。

有关接口映射的详细信息，请参阅[技术说明 38](../tn038-mfc-ole-iunknown-implementation.md)。

### <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="commandhandler"></a>CommandHandler 委托

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

有关详细信息，请参阅[如何：添加命令路由到 Windows 窗体控件](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)。

有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

### <a name="requirements"></a>要求

**标头：** afxwinforms.h （在程序集 atlmfc\lib\mfcmifc80.dll 中定义）

##  <a name="commanduihandler"></a>CommandUIHandler

注册具有用户界面更新命令消息的回调方法。

### <a name="syntax"></a>语法

```
delegate void CommandUIHandler(  unsigned int cmdID, ICommandUI^ cmdUI);
```

### <a name="parameters"></a>参数

*cmdID*<br/>
命令 ID。

*cmdUI*<br/>
命令消息 id。

### <a name="remarks"></a>备注

此委托注册具有用户界面更新命令消息的回调方法。 `CommandUIHandler` 类似于[CommandHandler](#commandhandler)只不过用户界面对象更新命令将使用此委托。 用户界面更新命令应将映射一对一与消息处理程序方法。

有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

### <a name="requirements"></a>要求

**标头：** afxwinforms.h （在程序集 atlmfc\lib\mfcmifc80.dll 中定义）

##  <a name="end_delegate_map"></a>END_DELEGATE_MAP

结束委托映射。

### <a name="syntax"></a>语法

```
END_DELEGATE_MAP();
```

### <a name="remarks"></a>备注

此宏将标记的委托条目，组合委托映射列表的末尾。 有关如何使用此宏的示例，请参阅[EVENT_DELEGATE_ENTRY](#event_delegate_entry)。

### <a name="requirements"></a>要求

**标头：** msclr\event.h

##  <a name="end_interface_map"></a>END_INTERFACE_MAP

终止实现文件中的接口映射。

### <a name="syntax"></a>语法

```
END_INTERFACE_MAP( )
```

### <a name="remarks"></a>备注

有关接口映射的详细信息，请参阅[技术说明 38](../tn038-mfc-ole-iunknown-implementation.md)。

### <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="event_delegate_entry"></a>EVENT_DELEGATE_ENTRY

在委托映射中创建条目。

### <a name="syntax"></a>语法

```
EVENT_DELEGATE_ENTRY(MEMBER, ARG0, ARG1);
```

### <a name="parameters"></a>参数

*MEMBER*<br/>
要附加到控件的事件处理程序方法。

*ARG0*<br/>
第一个参数的托管的事件处理程序方法，如`Object^`。

*ARG1*<br/>
第二个参数的托管的事件处理程序方法，如`EventArgs^`。

### <a name="remarks"></a>备注

委托映射中的每个条目对应于创建的托管的事件处理程序委托[MAKE_DELEGATE](#make_delegate)。

### <a name="example"></a>示例

下面的代码示例演示如何使用 EVENT_DELEGATE_ENTRY 在委托映射中创建一个条目`OnClick`事件处理程序; 还 MAKE_DELEGATE 中的代码示例，请参阅。 有关详细信息，请参阅[如何：接收来自本机 c + + 类的 Windows 窗体事件](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)。

```cpp
BEGIN_DELEGATE_MAP(CMyView)
   EVENT_DELEGATE_ENTRY(OnClick, System::Object^, System::EventArgs^)
END_DELEGATE_MAP()
```

### <a name="requirements"></a>要求

**标头：** msclr\event.h

##  <a name="interface_part"></a>INTERFACE_PART

BEGIN_INTERFACE_MAP 宏和 END_INTERFACE_MAP 宏之间使用的每个接口将支持您的对象。

### <a name="syntax"></a>语法

```
INTERFACE_PART( theClass, iid, localClass)
```

### <a name="parameters"></a>参数

*theClass*<br/>
包含接口映射的类的名称。
*iid*<br/>
要映射到嵌入类的 IID。
*localClass*<br/>
局部类的名称。

### <a name="remarks"></a>备注

它允许您将 IID 映射到指示的类的成员*类*并*localClass*。

有关接口映射的详细信息，请参阅[技术说明 38](../tn038-mfc-ole-iunknown-implementation.md)。

### <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="make_delegate"></a>MAKE_DELEGATE

将事件处理程序附加到的托管控件。

### <a name="syntax"></a>语法

```
MAKE_DELEGATE( DELEGATE,  MEMBER) ;
```

### <a name="parameters"></a>参数

*DELEGATE*<br/>
托管的事件处理程序的委托类型，如[EventHandler](assetId:///T:System.EventHandler?qualifyHint=False&autoUpgrade=True)。

*MEMBER*<br/>
若要附加到控件的事件处理程序方法的名称。

### <a name="remarks"></a>备注

此宏创建类型的托管的事件处理程序委托*委派*和名称的*成员*。 托管的事件处理程序委托允许本机类以处理托管的事件。

### <a name="example"></a>示例

下面的代码示例演示如何调用`MAKE_DELEGATE`附加`OnClick`事件处理程序到 MFC 控件`MyControl`。 此宏的 MFC 应用程序中的工作原理的更广泛的说明，请参阅[如何：接收来自本机 c + + 类的 Windows 窗体事件](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)。

```cpp
// CMyView derives from CWinFormsView.
void CMyView::OnInitialUpdate()
{
   CWinFormsView::OnInitialUpdate();

   GetControl()->Click += MAKE_DELEGATE(System::EventHandler, OnClick);
}
```

### <a name="requirements"></a>要求

**标头：** msclr\event.h

## <a name="see-also"></a>请参阅

[如何：接收来自本机 C++ 类的 Windows 窗体事件](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)<br/>
[如何：向 Windows 窗体控件添加命令路由](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[宏和全局函数](mfc-macros-and-globals.md)<br/>
