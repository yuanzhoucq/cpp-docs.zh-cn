---
title: 注册 OLE 控件
ms.date: 11/04/2016
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
ms.openlocfilehash: 9fcbc002913cc6cce86276796a371231ef0f32e1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856373"
---
# <a name="registering-ole-controls"></a>注册 OLE 控件

与其他 OLE 服务器对象一样，OLE 控件可由其他 OLE 感知应用程序访问。 这是通过注册控件的类型库和类来实现的。

利用下列函数，您可在 Windows 注册数据库中添加和删除控件的类、属性页和类型库：

### <a name="registering-ole-controls"></a>注册 OLE 控件

|||
|-|-|
|[AfxOleRegisterControlClass](#afxoleregistercontrolclass)|将控件的类添加到注册数据库。|
|[AfxOleRegisterPropertyPageClass](#afxoleregisterpropertypageclass)|将控件属性页添加到注册数据库。|
|[AfxOleRegisterTypeLib](#afxoleregistertypelib)|将控件的类型库添加到注册数据库。|
|[AfxOleUnregisterClass](#afxoleunregisterclass)|从注册数据库中删除控件类或属性页类。|
|[AfxOleUnregisterTypeLib](#afxoleunregistertypelib)|从注册数据库中删除控件的类型库。|

一般在控件 DLL 的 `AfxOleRegisterTypeLib` 实现中调用 `DllRegisterServer`。 同样，`AfxOleUnregisterTypeLib` 由 `DllUnregisterServer` 调用。 `AfxOleRegisterControlClass`、`AfxOleRegisterPropertyPageClass` 和 `AfxOleUnregisterClass` 一般由控件的类工厂或属性页的 `UpdateRegistry` 成员函数调用。

##  <a name="afxoleregistercontrolclass"></a>AfxOleRegisterControlClass

向 Windows 注册数据库注册 control 类。

```
BOOL AFXAPI AfxOleRegisterControlClass(
    HINSTANCE hInstance,
    REFCLSID clsid,
    LPCTSTR pszProgID,
    UINT idTypeName,
    UINT idBitmap,
    int nRegFlags,
    DWORD dwMiscStatus,
    REFGUID tlid,
    WORD wVerMajor,
    WORD wVerMinor);
```

### <a name="parameters"></a>参数

*hInstance*<br/>
与控件类关联的模块的实例句柄。

*clsid*<br/>
控件的唯一类 ID。

*pszProgID*<br/>
控件的唯一程序 ID。

*idTypeName*<br/>
包含控件的用户可读类型名称的字符串的资源 ID。

*idBitmap*<br/>
用于表示工具栏或调色板中 OLE 控件的位图的资源 ID。

*nRegFlags*<br/>
包含一个或多个以下标志：

- `afxRegInsertable` 允许控件显示在 OLE 对象的 "插入对象" 对话框中。

- `afxRegApartmentThreading` 将注册表中的线程模型设置为 ThreadingModel = 单元。

- `afxRegFreeThreading` 将注册表中的线程模型设置为 ThreadingModel = Free。

   可以结合两个标志 `afxRegApartmentThreading` 和 `afxRegFreeThreading` 设置 ThreadingModel = Both。 有关线程模型注册的详细信息，请参阅 Windows SDK 中的[InprocServer32](/windows/win32/com/inprocserver32) 。

> [!NOTE]
>  在 mfc 4.2 之前的 MFC 版本中， **int** *nRegFlags*参数是一个布尔参数*bInsertable*，该参数允许或禁止从 "插入对象" 对话框插入控件。

*dwMiscStatus*<br/>
包含一个或多个以下状态标志（有关标志的说明，请参阅 Windows SDK 中的 OLEMISC 枚举）：

- OLEMISC_RECOMPOSEONRESIZE

- OLEMISC_ONLYICONIC

- OLEMISC_INSERTNOTREPLACE

- OLEMISC_STATIC

- OLEMISC_CANTLINKINSIDE

- OLEMISC_CANLINKBYOLE1

- OLEMISC_ISLINKOBJECT

- OLEMISC_INSIDEOUT

- OLEMISC_ACTIVATEWHENVISIBLE

- OLEMISC_RENDERINGISDEVICEINDEPENDENT

- OLEMISC_INVISIBLEATRUNTIME

- OLEMISC_ALWAYSRUN

- OLEMISC_ACTSLIKEBUTTON

- OLEMISC_ACTSLIKELABEL

- OLEMISC_NOUIACTIVATE

- OLEMISC_ALIGNABLE

- OLEMISC_IMEMODE

- OLEMISC_SIMPLEFRAME

- OLEMISC_SETCLIENTSITEFIRST

*tlid*<br/>
控件类的唯一 ID。

*wVerMajor*<br/>
控件类的主版本号。

*wVerMinor*<br/>
控件类的次版本号。

### <a name="return-value"></a>返回值

如果控件类已注册，则为非零值;否则为0。

### <a name="remarks"></a>备注

这允许控件由 OLE 控件识别的容器使用。 `AfxOleRegisterControlClass` 用系统上的控件的名称和位置更新注册表，还会在注册表中设置控件支持的线程模型。 有关详细信息，请参阅[技术说明 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md)"OLE 控件中的单元模型线程处理" 和 Windows SDK 中的[进程和线程](/windows/win32/ProcThread/about-processes-and-threads)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]

上面的示例演示如何通过用于可插入的标志来调用 `AfxOleRegisterControlClass`，并将单元模型运算的标志一起用于创建第六个参数：

[!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]

控件将显示在启用的容器的 "插入对象" 对话框中，它将是单元模型感知。 单元模型感知控件必须确保静态类数据受到锁保护，这样，在一个单元中的控件访问静态数据时，计划程序不会在它完成之前禁用该数据，并且使用同一类的另一个实例开始使用相同的静态数据。 对静态数据的任何访问都将用关键部分代码括起来。

### <a name="requirements"></a>要求

  **标头**afxctl。h

##  <a name="afxoleregisterpropertypageclass"></a>AfxOleRegisterPropertyPageClass

向 Windows 注册数据库注册属性页类。

```
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,
   REFCLSID  clsid,
   UINT idTypeName,
   int nRegFlags);
```

### <a name="parameters"></a>参数

*hInstance*<br/>
与属性页类关联的模块的实例句柄。

*clsid*<br/>
属性页的唯一类 ID。

*idTypeName*<br/>
包含属性页的用户可读名称的字符串的资源 ID。

*nRegFlags*<br/>
可能包含标志：

- `afxRegApartmentThreading` 将注册表中的线程模型设置为 ThreadingModel = 单元。

> [!NOTE]
>  在 MFC 4.2 之前的 MFC 版本中， **int** *nRegFlags*参数不可用。 另请注意，`afxRegInsertable` 标志不是属性页的有效选项，如果已设置，则将在 MFC 中引发断言。

### <a name="return-value"></a>返回值

如果控件类已注册，则为非零值;否则为0。

### <a name="remarks"></a>备注

这允许由 OLE 控件识别的容器使用属性页。 `AfxOleRegisterPropertyPageClass` 用属性页名称及其在系统上的位置来更新注册表，还会在注册表中设置控件支持的线程模型。 有关详细信息，请参阅[技术说明 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md)"OLE 控件中的单元模型线程处理" 和 Windows SDK 中的[进程和线程](/windows/win32/ProcThread/about-processes-and-threads)。

### <a name="requirements"></a>要求

  **标头**afxctl。h

##  <a name="afxoleregistertypelib"></a>AfxOleRegisterTypeLib

将类型库注册到 Windows 数据库并允许类型库由 OLE 控件可识别的其他容器使用。

```
BOOL AfxOleRegisterTypeLib(
    HINSTANCE hInstance,
    REFGUID tlid,
    LPCTSTR pszFileName = NULL,
    LPCTSTR pszHelpDir  = NULL);
```

### <a name="parameters"></a>参数

*hInstance*<br/>
与类型库关联的应用程序的实例句柄。

*tlid*<br/>
类型库的唯一 ID。

*pszFileName*<br/>
指向控件的本地化类型库 (.TLB) 文件的可选文件名的指针。

*pszHelpDir*<br/>
可从中找到类型库的帮助文件的名称的目录。 如果为 NULL，则假定帮助文件与类型库本身位于同一目录中。

### <a name="return-value"></a>返回值

如果已注册类型库，则为非零；否则为 0。

### <a name="remarks"></a>备注

此函数将在注册表中更新类型库名称及其在系统中的位置。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCAutomation#7](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]

[!code-cpp[NVC_MFCAutomation#8](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]

### <a name="requirements"></a>要求

  **标头**afxdisp.h&gt

##  <a name="afxoleunregisterclass"></a>AfxOleUnregisterClass

从 Windows 注册数据库中删除控件或属性页类项。

```
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID);
```

### <a name="parameters"></a>参数

*clsID*<br/>
控件或属性页的唯一类 ID。

*pszProgID*<br/>
控件或属性页的唯一程序 ID。

### <a name="return-value"></a>返回值

如果控件或属性页类已成功注销，则为非零值;否则为0。

### <a name="requirements"></a>要求

  **标头**afxctl。h

##  <a name="afxoleunregistertypelib"></a>AfxOleUnregisterTypeLib

调用此函数可从 Windows 注册数据库中删除类型库条目。

```
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID);
```

### <a name="parameters"></a>参数

*tlID*<br/>
类型库的唯一 ID。

### <a name="return-value"></a>返回值

如果类型库注册成功，则为非零值;否则为0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]

### <a name="requirements"></a>要求

  **标头**afxdisp.h&gt

## <a name="see-also"></a>另请参阅

[宏和全局](../../mfc/reference/mfc-macros-and-globals.md)
