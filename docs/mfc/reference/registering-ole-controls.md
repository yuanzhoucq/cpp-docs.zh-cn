---
title: 注册 OLE 控件
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.ole
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
ms.openlocfilehash: 9c480696bdec3591f0509cbad04051a2b3af4070
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57262150"
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

##  <a name="afxoleregistercontrolclass"></a>  AfxOleRegisterControlClass

使用 Windows 注册数据库注册控件类。

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
与控件类相关联的模块实例句柄。

*clsid*<br/>
控件的唯一类 ID。

*pszProgID*<br/>
控件的唯一程序 ID。

*idTypeName*<br/>
包含控件的用户可读类型名称的字符串资源 ID。

*idBitmap*<br/>
用于表示 OLE 控件在工具栏或调色板中的位图资源 ID。

*nRegFlags*<br/>
包含一个或多个下列标志：

- `afxRegInsertable` 允许要在 OLE 对象的插入对象对话框中显示的控件。

- `afxRegApartmentThreading` ThreadingModel 注册表中设置线程模型 = 单元。

- `afxRegFreeThreading` ThreadingModel 注册表中设置线程模型 = 免费。

   你可以组合两个标志`afxRegApartmentThreading`和`afxRegFreeThreading`设置 ThreadingModel = Both。 请参阅[InprocServer32](/windows/desktop/com/inprocserver32) Windows SDK for 线程处理模型注册的详细信息中。

> [!NOTE]
>  在 MFC 4.2 之前的 MFC 版本**int** *nRegFlags*参数是一个 BOOL 参数*bInsertable*的允许或不允许插入进行插入的控件对象对话框。

*dwMiscStatus*<br/>
包含一个或多个以下的状态标志 （对于标志，请参阅 Windows SDK 中的 OLEMISC 枚举的说明）：

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

如果已注册的控件类; 非零值否则为 0。

### <a name="remarks"></a>备注

这样，要使用的是 OLE 控件可识别的容器的控件。 `AfxOleRegisterControlClass` 使用控件的名称和位置在系统上的更新注册表，并还会设置该控件支持在注册表中的线程模型。 有关详细信息，请参阅[技术说明 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md)，"单元模型线程处理中 OLE 控件"和[有关进程和线程](/windows/desktop/ProcThread/about-processes-and-threads)Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]

上面的示例演示如何`AfxOleRegisterControlClass`调用时所使用的标志可插入和单元的标志的模型或运算在一起以创建第六个参数：

[!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]

该控件将显示在已启用容器的插入对象对话框，它将模型可识别单元。 单元模型识别控件，以便一个单元中的控件访问的静态数据，而它未被禁用的计划程序完成后，并使用同一个类的另一个实例启动之前必须确保数据保护的锁，该静态类相同的静态数据。 对静态数据的任何访问将括关键部分代码。

### <a name="requirements"></a>要求

  **标头**afxctl.h

##  <a name="afxoleregisterpropertypageclass"></a>  AfxOleRegisterPropertyPageClass

使用 Windows 注册数据库注册属性页类。

```
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,
   REFCLSID  clsid,
   UINT idTypeName,
   int nRegFlags);
```

### <a name="parameters"></a>参数

*hInstance*<br/>
与属性页类相关联的模块实例句柄。

*clsid*<br/>
属性页的唯一类 ID。

*idTypeName*<br/>
包含属性页的用户可读名称的字符串资源 ID。

*nRegFlags*<br/>
可能包含标志：

- `afxRegApartmentThreading` ThreadingModel 注册表中设置线程模型 = 单元。

> [!NOTE]
>  在 MFC 4.2 之前的 MFC 版本**int** *nRegFlags*参数不可用。 另请注意，`afxRegInsertable`标志不是属性页的有效选项，如果将其设置将导致在 MFC 中的断言

### <a name="return-value"></a>返回值

如果已注册的控件类; 非零值否则为 0。

### <a name="remarks"></a>备注

这允许属性页可由 OLE 控件可识别的容器。 `AfxOleRegisterPropertyPageClass` 使用属性页名称和其位置在系统上的更新注册表，并还会设置该控件支持在注册表中的线程模型。 有关详细信息，请参阅[技术说明 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md)，"单元模型线程处理中 OLE 控件"和[有关进程和线程](/windows/desktop/ProcThread/about-processes-and-threads)Windows SDK 中。

### <a name="requirements"></a>要求

  **标头**afxctl.h

##  <a name="afxoleregistertypelib"></a>  AfxOleRegisterTypeLib

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
可从中找到类型库的帮助文件的名称的目录。 如果为 NULL，被假定的帮助文件可在类型库本身所在的同一目录中。

### <a name="return-value"></a>返回值

如果已注册类型库，则为非零；否则为 0。

### <a name="remarks"></a>备注

此函数将在注册表中更新类型库名称及其在系统中的位置。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCAutomation#7](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]

[!code-cpp[NVC_MFCAutomation#8](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]

### <a name="requirements"></a>要求

  **标头**afxdisp.h

##  <a name="afxoleunregisterclass"></a>  AfxOleUnregisterClass

从 Windows 注册数据库中删除控件或属性页类条目。

```
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID);
```

### <a name="parameters"></a>参数

*clsID*<br/>
控件或属性页的唯一类 ID。

*pszProgID*<br/>
控件或属性页的唯一程序 ID。

### <a name="return-value"></a>返回值

如果控件或属性页类已成功注销; 非零值否则为 0。

### <a name="requirements"></a>要求

  **标头**afxctl.h

##  <a name="afxoleunregistertypelib"></a>  AfxOleUnregisterTypeLib

调用此函数可从 Windows 注册数据库中删除类型库项。

```
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID);
```

### <a name="parameters"></a>参数

*tlID*<br/>
类型库的唯一 ID。

### <a name="return-value"></a>返回值

如果类型库已成功注销; 非零值否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]

### <a name="requirements"></a>要求

  **标头**afxdisp.h

## <a name="see-also"></a>请参阅

[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
