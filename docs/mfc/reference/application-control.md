---
title: 应用程序控件
ms.date: 11/04/2016
helpviewer_keywords:
- application control [MFC]
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
ms.openlocfilehash: cb4ad19dfad06b793f226324d8e28c37c084ad67
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855679"
---
# <a name="application-control"></a>应用程序控件

OLE 需要对应用程序及其对象进行大量控制。 OLE 系统 Dll 必须能够自动启动和发布应用程序，协调它们的生产和修改对象等。 本主题中的函数满足这些要求。 除了由 OLE 系统 Dll 调用以外，这些函数有时还必须由应用程序调用。

### <a name="application-control"></a>应用程序控件

|||
|-|-|
|[AfxOleCanExitApp](#afxolecanexitapp)|指示应用程序是否可以终止。|
|[AfxOleGetMessageFilter](#afxolegetmessagefilter)|检索应用程序的当前消息筛选器。|
|[AfxOleGetUserCtrl](#afxolegetuserctrl)|检索当前用户控件标志。|
|[AfxOleSetUserCtrl](#afxolesetuserctrl)|设置或清除用户控件标志。|
|[AfxOleLockApp](#afxolelockapp)|在应用程序中递增框架的活动对象数的全局计数。|
|[AfxOleLockControl](#afxolelockcontrol)| 锁定指定控件的类工厂。 |
|[AfxOleUnlockApp](#afxoleunlockapp)|减少应用程序中活动对象数目的框架计数。|
|[AfxOleUnlockControl](#afxoleunlockcontrol)| 解锁指定控件的类工厂。 |
|[AfxOleRegisterServerClass](#afxoleregisterserverclass)|在 OLE 系统注册表中注册服务器。|
|[AfxOleSetEditMenu](#afxoleseteditmenu)|实现*typename* Object 命令的用户界面。|

##  <a name="afxolecanexitapp"></a>AfxOleCanExitApp

指示应用程序是否可以终止。

```
BOOL AFXAPI AfxOleCanExitApp();
```

### <a name="return-value"></a>返回值

如果应用程序退出，则为非零；否则为 0。

### <a name="remarks"></a>备注

如果存在对应用程序的对象的未处理引用，则应用程序不应终止。 全局函数 `AfxOleLockApp` 和 `AfxOleUnlockApp` 分别对应用程序对象引用计数器进行递增和递减。 当此计数器为非零时，应用程序不应终止。 如果计数器为非零，当用户从系统菜单选择“关闭”或从“文件”菜单选择“退出”时，应用程序的主窗口将会隐藏（不销毁）。 框架在 `CFrameWnd::OnClose`中调用此函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCAutomation#2](../../mfc/codesnippet/cpp/application-control_1.cpp)]

## <a name="requirements"></a>要求

**标头**： afxdisp.h&gt

##  <a name="afxolegetmessagefilter"></a>AfxOleGetMessageFilter

检索应用程序的当前消息筛选器。

```
COleMessageFilter* AFXAPI AfxOleGetMessageFilter();
```

### <a name="return-value"></a>返回值

指向当前消息筛选器的指针。

### <a name="remarks"></a>备注

调用此函数可访问当前 `COleMessageFilter` 派生的对象，这与调用 `AfxGetApp` 来访问当前应用程序对象一样。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCAutomation#3](../../mfc/codesnippet/cpp/application-control_2.cpp)]

[!code-cpp[NVC_MFCAutomation#4](../../mfc/codesnippet/cpp/application-control_3.cpp)]

### <a name="requirements"></a>要求

**标头**： afxwin。h

##  <a name="afxolegetuserctrl"></a>AfxOleGetUserCtrl

检索当前用户控件标志。

```
BOOL AFXAPI AfxOleGetUserCtrl();
```

### <a name="return-value"></a>返回值

如果用户位于应用程序控件内，则不为零；否则为 0。

### <a name="remarks"></a>备注

如果用户已显式打开或创建新文档，则用户将位于应用程序控件内。 如果应用程序不是由 OLE 系统 DLL 启动的 - 换句话说，如果用户使用系统 Shell 启动了应用程序，则用户也将位于控件内。

### <a name="requirements"></a>要求

**标头**： afxdisp.h&gt

##  <a name="afxolesetuserctrl"></a>AfxOleSetUserCtrl

设置或清除用户控制标志，该标志在 `AfxOleGetUserCtrl`的引用中进行了介绍。

```
void AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl);
```

### <a name="parameters"></a>参数

*bUserCtrl*<br/>
指定是否要设置或清除用户控制标志。

### <a name="remarks"></a>备注

当用户创建或加载文档时，框架会调用此函数，但在通过间接操作（如从容器应用程序加载嵌入的对象）加载或创建文档时，框架将调用此函数。

如果应用程序中的其他操作应使用户控制应用程序，则调用此函数。

### <a name="requirements"></a>要求

**标头**： afxdisp.h&gt

##  <a name="afxolelockapp"></a>AfxOleLockApp

在应用程序中递增框架的活动对象数的全局计数。

```
void AFXAPI AfxOleLockApp();
```

### <a name="remarks"></a>备注

框架将保留应用程序中处于活动状态的对象数。 `AfxOleLockApp` 和 `AfxOleUnlockApp` 函数分别递增和递减此计数。

当用户尝试关闭具有活动对象的应用程序（活动对象计数不为零的应用程序）时，框架会从用户的视图中隐藏该应用程序，而不是完全将其关闭。 `AfxOleCanExitApp` 函数指示应用程序是否可以终止。

如果要在客户端应用程序仍然使用的同时销毁该对象，则从任何公开 OLE 接口的对象调用 `AfxOleLockApp`。 还应在调用构造函数中 `AfxOleLockApp` 的任何对象的析构函数中调用 `AfxOleUnlockApp`。 默认情况下，`COleDocument` （和派生类）自动锁定和解锁应用程序。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCAutomation#5](../../mfc/codesnippet/cpp/application-control_4.cpp)]

### <a name="requirements"></a>要求

**标头**： afxdisp.h&gt

##  <a name="afxoleunlockapp"></a>AfxOleUnlockApp

减少应用程序中的框架活动对象的计数。

```
void AFXAPI AfxOleUnlockApp();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅 `AfxOleLockApp`。

当活动对象数达到零时，将调用 `AfxOleOnReleaseAllObjects`。

### <a name="example"></a>示例

请参阅[AfxOleLockApp](#afxolelockapp)的示例。

### <a name="requirements"></a>要求

**标头**： afxdisp.h&gt

## <a name="afxolelockcontrol"></a>AfxOleLockControl

锁定指定控件的类工厂，以便与此控件关联的动态创建的数据保留在内存中。

### <a name="syntax"></a>语法

```
BOOL AFXAPI AfxOleLockControl(  REFCLSID clsid  );
BOOL AFXAPI AfxOleLockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>参数

*clsid*<br/>
控件的唯一类 ID。

*lpszProgID*<br/>
控件的唯一程序 ID。

### <a name="return-value"></a>返回值

如果控件的类工厂成功锁定，则不为零；否则为 0。

### <a name="remarks"></a>备注

这可以明显加速控件的显示。 例如，一旦在对话框中创建控件并使用 `AfxOleLockControl` 锁定控件，则无需在每次显示或销毁对话框时创建和删除它。 如果用户反复打开并关闭对话框，则锁定控件可以显著提高性能。 准备销毁控件时，请调用 `AfxOleUnlockControl`。

### <a name="example"></a>示例

```cpp
// Starts and locks control's (Microsoft Calendar) class factory.
// Control will remain in memory for lifetime of
// application or until AfxOleUnlockControl() is called.

AfxOleLockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="afxoleregisterserverclass"></a>AfxOleRegisterServerClass

此函数允许您在 OLE 系统注册表中注册您的服务器。

```
BOOL AFXAPI AfxOleRegisterServerClass(
    REFCLSID clsid,
    LPCTSTR lpszClassName,
    LPCTSTR lpszShortTypeName,
    LPCTSTR lpszLongTypeName,
    OLE_APPTYPE nAppType = OAT_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL);
```

### <a name="parameters"></a>参数

*clsid*<br/>
对服务器的 OLE 类 ID 的引用。

*lpszClassName*<br/>
指向字符串的指针，该字符串包含服务器的对象的类名。

*lpszShortTypeName*<br/>
指向字符串的指针，该字符串包含服务器的对象类型的短名称，如 "Chart"。

*lpszLongTypeName*<br/>
指向字符串的指针，该字符串包含服务器的对象类型的长名称，如 "Microsoft Excel 5.0 图表"。

*nAppType*<br/>
从 OLE_APPTYPE 枚举获取的值，指定 OLE 应用程序的类型。 可能的值如下：

- OAT_INPLACE_SERVER Server 具有完全服务器用户界面。

- OAT_SERVER Server 仅支持嵌入。

- OAT_CONTAINER 容器支持指向嵌入的链接。

- OAT_DISPATCH_OBJECT 支持 `IDispatch`的对象。

*rglpszRegister*<br/>
指向字符串的指针的数组，这些字符串表示当找不到键的现有值时要添加到 OLE 系统注册表中的键和值。

*rglpszOverwrite*<br/>
指向字符串的指针的数组，这些字符串表示在注册表包含给定键的现有值时要添加到 OLE 系统注册表中的键和值。

### <a name="return-value"></a>返回值

如果成功注册服务器类，则为非零值;否则为0。

### <a name="remarks"></a>备注

大多数应用程序都可以使用 `COleTemplateServer::Register` 来注册应用程序的文档类型。 如果你的应用程序的系统注册表格式不符合典型模式，则可以使用 `AfxOleRegisterServerClass` 进行更多的控制。

注册表由一组键和值组成。 *RglpszRegister*和*rglpszOverwrite*参数是指向字符串的指针的数组，其中每个都包含一个键和一个由**NULL**字符分隔的值（`'\0'`）。 其中每个字符串都可以具有可替换参数，其位置由字符序列 *%1*到 *%5*标记。

符号填写如下：

|符号|值|
|------------|-----------|
|%1|类 ID，格式为字符串|
|%2|类名|
|%3|可执行文件的路径|
|%4|Short 类型名称|
|%5|Long 类型名称|

### <a name="requirements"></a>要求

**标头**： afxdisp.h&gt

##  <a name="afxoleseteditmenu"></a>AfxOleSetEditMenu

实现*typename* Object 命令的用户界面。

```
void AFXAPI AfxOleSetEditMenu(
    COleClientItem* pClient,
    CMenu* pMenu,
    UINT iMenuItem,
    UINT nIDVerbMin,
    UINT nIDVerbMax = 0,
    UINT nIDConvert = 0);
```

### <a name="parameters"></a>参数

*pClient*<br/>
指向客户端 OLE 项的指针。

*pMenu*<br/>
指向要更新的菜单对象的指针。

*iMenuItem*<br/>
要更新的菜单项的索引。

*nIDVerbMin*<br/>
与主谓词相对应的命令 ID。

*nIDVerbMax*<br/>
对应于最后一个谓词的命令 ID。

*nIDConvert*<br/>
转换菜单项的 ID。

### <a name="remarks"></a>备注

如果服务器仅识别主谓词，则菜单项将变为 "verb *typename* Object"，并在用户选择命令时发送*nIDVerbMin*命令。 如果服务器识别多个谓词，则该菜单项将变为 " *typename* Object"，并在用户选择命令时，将显示一个子菜单，其中列出了所有谓词。 当用户从子菜单中选择谓词时，如果选择第一个谓词，则将发送*nIDVerbMin* ，如果选择第二个谓词，则发送*nIDVerbMin* + 1，依此类推。 默认 `COleDocument` 实现会自动处理此功能。

你必须在客户端的应用程序资源脚本（。RC）文件：

**#include \<afxolecl >**

### <a name="requirements"></a>要求

**标头**： afxole

## <a name="afxoleunlockcontrol"></a>AfxOleUnlockControl

解锁指定控件的类工厂。

### <a name="syntax"></a>语法

```
BOOL AFXAPI AfxOleUnlockControl( REFCLSID clsid );
BOOL AFXAPI AfxOleUnlockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>参数

*clsid*<br/>
控件的唯一类 ID。

*lpszProgID*<br/>
控件的唯一程序 ID。

### <a name="return-value"></a>返回值

如果成功解锁控件的类工厂，则为非零值;否则为0。

### <a name="remarks"></a>备注

控件已使用 `AfxOleLockControl`锁定，因此与该控件关联的动态创建的数据仍保留在内存中。 这可以显著提高控件的显示速度，因为无需在每次显示控件时都创建和销毁控件。 准备销毁控件时，请调用 `AfxOleUnlockControl`。

### <a name="example"></a>示例

```cpp
// Unlock control's (Microsoft Calendar Control) class factory.

AfxOleUnlockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="see-also"></a>另请参阅

[宏和全局](mfc-macros-and-globals.md)<br/>
