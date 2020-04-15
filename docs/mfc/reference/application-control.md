---
title: 应用程序控件
ms.date: 11/04/2016
helpviewer_keywords:
- application control [MFC]
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
ms.openlocfilehash: 1f438d3344e90a16def2bd4c0f9cedcd47a64203
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363560"
---
# <a name="application-control"></a>应用程序控件

OLE 要求对应用程序及其对象进行大量控制。 OLE 系统 DLL 必须能够自动启动和释放应用程序，协调对象的生成和修改，等等。 本主题中的函数满足这些要求。 除了被 OLE 系统 DLL 调用外，应用程序有时还必须调用这些函数。

### <a name="application-control"></a>应用程序控件

|||
|-|-|
|[AfxOleCanExitApp](#afxolecanexitapp)|指示应用程序是否可以终止。|
|[AfxOleGetMessageFilter](#afxolegetmessagefilter)|检索应用程序的当前消息筛选器。|
|[AfxOleGetUserCtrl](#afxolegetuserctrl)|检索当前用户控件标志。|
|[AfxOleSetUserCtrl](#afxolesetuserctrl)|设置或清除用户控制标志。|
|[AfxOleLockApp](#afxolelockapp)|增加框架在应用程序中活动对象数的全局计数。|
|[AfxOleLockControl](#afxolelockcontrol)| 锁定指定控件的类工厂。 |
|[AfxOleUnlockApp](#afxoleunlockapp)|声明框架对应用程序中活动对象数的计数。|
|[AfxOleUnlockControl](#afxoleunlockcontrol)| 解锁指定控件的类工厂。 |
|[AfxOleRegisterServerClass](#afxoleregisterserverclass)|在 OLE 系统注册表中注册服务器。|
|[AfxOleSetEditMenu](#afxoleseteditmenu)|实现*类型名称*对象命令的用户界面。|

## <a name="afxolecanexitapp"></a><a name="afxolecanexitapp"></a>AfxOleCanExitApp

指示应用程序是否可以终止。

```
BOOL AFXAPI AfxOleCanExitApp();
```

### <a name="return-value"></a>返回值

如果应用程序退出，则为非零；否则为 0。

### <a name="remarks"></a>备注

如果存在对应用程序的对象的未处理引用，则应用程序不应终止。 全局函数 `AfxOleLockApp` 和 `AfxOleUnlockApp` 分别对应用程序对象引用计数器进行递增和递减。 当此计数器为非零时，应用程序不应终止。 如果计数器为非零，当用户从系统菜单选择“关闭”或从“文件”菜单选择“退出”时，应用程序的主窗口将会隐藏（不销毁）。 框架在 中`CFrameWnd::OnClose`调用此函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCAutomation#2](../../mfc/codesnippet/cpp/application-control_1.cpp)]

## <a name="requirements"></a>要求

**标题**： afxdisp.h

## <a name="afxolegetmessagefilter"></a><a name="afxolegetmessagefilter"></a>AfxOleGet消息过滤器

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

**标题**： afxwin.h

## <a name="afxolegetuserctrl"></a><a name="afxolegetuserctrl"></a>阿福奥莱格瑟克拉尔

检索当前用户控件标志。

```
BOOL AFXAPI AfxOleGetUserCtrl();
```

### <a name="return-value"></a>返回值

如果用户位于应用程序控件内，则不为零；否则为 0。

### <a name="remarks"></a>备注

如果用户已显式打开或创建新文档，则用户将位于应用程序控件内。 如果应用程序不是由 OLE 系统 DLL 启动的 - 换句话说，如果用户使用系统 Shell 启动了应用程序，则用户也将位于控件内。

### <a name="requirements"></a>要求

**标题**： afxdisp.h

## <a name="afxolesetuserctrl"></a><a name="afxolesetuserctrl"></a>阿福奥莱塞塞瑟克拉尔

设置或清除用户控制标志，这在 引用中`AfxOleGetUserCtrl`解释。

```
void AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl);
```

### <a name="parameters"></a>参数

*bUserCtrl*<br/>
指定是设置还是清除用户控制标志。

### <a name="remarks"></a>备注

当用户创建或加载文档时，框架调用此函数，但当通过间接操作（如从容器应用程序加载嵌入对象）加载或创建文档时，框架将调用此函数。

如果应用程序中的其他操作应使用户控制应用程序，请调用此函数。

### <a name="requirements"></a>要求

**标题**： afxdisp.h

## <a name="afxolelockapp"></a><a name="afxolelockapp"></a>阿FXOlelockApp

增加框架在应用程序中活动对象数的全局计数。

```
void AFXAPI AfxOleLockApp();
```

### <a name="remarks"></a>备注

框架保留应用程序中活动对象数的计数。 和`AfxOleLockApp``AfxOleUnlockApp`函数，分别，增量和递减此计数。

当用户尝试关闭具有活动对象的应用程序（活动对象的计数为非零的应用程序）时，框架会将应用程序从用户的视图中隐藏，而不是完全关闭它。 该`AfxOleCanExitApp`函数指示应用程序是否可以终止。

从`AfxOleLockApp`公开 OLE 接口的任何对象调用，如果该对象在客户端应用程序仍在使用时销毁该对象是不可取的。 还要在`AfxOleUnlockApp`构造函数中调用`AfxOleLockApp`的任何对象的析构函数中调用。 默认情况下，（`COleDocument`和派生类）会自动锁定和解锁应用程序。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCAutomation#5](../../mfc/codesnippet/cpp/application-control_4.cpp)]

### <a name="requirements"></a>要求

**标题**： afxdisp.h

## <a name="afxoleunlockapp"></a><a name="afxoleunlockapp"></a>AfxOle解锁应用程序

声明框架在应用程序中的活动对象的计数。

```
void AFXAPI AfxOleUnlockApp();
```

### <a name="remarks"></a>备注

有关详细信息`AfxOleLockApp`，请参阅。

当活动对象数达到零时，`AfxOleOnReleaseAllObjects`将调用。

### <a name="example"></a>示例

请参阅[AfxOleLockApp](#afxolelockapp)的示例。

### <a name="requirements"></a>要求

**标题**： afxdisp.h

## <a name="afxolelockcontrol"></a>AfxOleLockControl

锁定指定控件的类工厂，以便与此控件关联的动态创建的数据保留在内存中。

### <a name="syntax"></a>语法

```
BOOL AFXAPI AfxOleLockControl(  REFCLSID clsid  );
BOOL AFXAPI AfxOleLockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>参数

*Clsid*<br/>
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

## <a name="afxoleregisterserverclass"></a><a name="afxoleregisterserverclass"></a>AfxOle注册服务器类

此功能允许您在 OLE 系统注册表中注册服务器。

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

*Clsid*<br/>
引用服务器的 OLE 类 ID。

*lpszClass名称*<br/>
指向包含服务器对象的类名的字符串的指针。

*lpsz短类型名称*<br/>
指向包含服务器对象类型的短名称的字符串的指针，如"图表"。

*lpszLongType 名称*<br/>
指向包含服务器对象类型的长名称的字符串的指针，例如"Microsoft Excel 5.0 图表"。

*nAppType*<br/>
从OLE_APPTYPE枚举中获取的值，指定 OLE 应用程序的类型。 可能的值如下：

- OAT_INPLACE_SERVER服务器具有完整的服务器用户界面。

- OAT_SERVER服务器仅支持嵌入。

- OAT_CONTAINER容器支持指向嵌入的链接。

- OAT_DISPATCH_OBJECT `IDispatch`- 支持对象。

*rglpsz注册*<br/>
如果找不到键的现有值，则指向表示要添加到 OLE 系统注册表的键和值的字符串的指针数组。

*rglpsz 覆盖*<br/>
如果注册表包含给定键的现有值，则指向表示要添加到 OLE 系统注册表的键和值的字符串的指针数组。

### <a name="return-value"></a>返回值

如果已成功注册服务器类，则非零;否则 0。

### <a name="remarks"></a>备注

大多数应用程序都可用于`COleTemplateServer::Register`注册应用程序的文档类型。 如果应用程序的系统注册表格式不符合典型模式，则可以使用`AfxOleRegisterServerClass`更多控件。

注册表由一组键和值组成。 *rglpsz注册*和*rglpszOverwrite*参数是指向字符串的指针数组，每个参数由键和由**NULL**字符 （）`'\0'`分隔的值组成。 每个字符串都可以具有可替换的参数，其位置由字符序列 *%1*到 *%5*标记。

符号填写如下：

|符号|“值”|
|------------|-----------|
|%1|类 ID，格式化为字符串|
|%2|类名称|
|%3|可执行文件的路径|
|%4|短类型名称|
|%5|长类型名称|

### <a name="requirements"></a>要求

**标题**： afxdisp.h

## <a name="afxoleseteditmenu"></a><a name="afxoleseteditmenu"></a>阿FXOleseteditMenu

实现*类型名称*对象命令的用户界面。

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

*iMenu项目*<br/>
要更新的菜单项的索引。

*nIDVerbMin*<br/>
对应于主谓词的命令 ID。

*nIDVerbMax*<br/>
对应于最后一个谓词的命令 ID。

*nIDConvert*<br/>
"转换"菜单项的 ID。

### <a name="remarks"></a>备注

如果服务器仅识别主谓词，菜单项将成为"动词*类型对象*"，当用户选择该命令时发送*nIDVerbMin*命令。 如果服务器识别多个谓词，则菜单项将成为 *"typename*对象"，并在用户选择该命令时显示列出所有谓词的子菜单。 当用户从子菜单中选择动词时，如果选择了第一个动词，则发送*nIDVerbMin;* 如果选择了第二个谓词，则发送*nIDVerbMin* = 1，依此类推。 默认`COleDocument`实现会自动处理此功能。

客户端的应用程序资源脚本 （中必须具有以下语句。RC） 文件：

**#include\<阿波诺尔克>**

### <a name="requirements"></a>要求

**标题**： afxole.h

## <a name="afxoleunlockcontrol"></a><a name="afxoleunlockcontrol"></a>AfxOle解锁控制

解锁指定控件的类工厂。

### <a name="syntax"></a>语法

```
BOOL AFXAPI AfxOleUnlockControl( REFCLSID clsid );
BOOL AFXAPI AfxOleUnlockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>参数

*Clsid*<br/>
控件的唯一类 ID。

*lpszProgID*<br/>
控件的唯一程序 ID。

### <a name="return-value"></a>返回值

如果控件的类工厂已成功解锁，则非零;否则 0。

### <a name="remarks"></a>备注

控件与`AfxOleLockControl`锁定，以便与控件关联的动态创建的数据保留在内存中。 这可以显著加快控件的显示速度，因为不必在每次显示控件时创建和销毁该控件。 准备销毁控件时，请调用 `AfxOleUnlockControl`。

### <a name="example"></a>示例

```cpp
// Unlock control's (Microsoft Calendar Control) class factory.

AfxOleUnlockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](mfc-macros-and-globals.md)<br/>
