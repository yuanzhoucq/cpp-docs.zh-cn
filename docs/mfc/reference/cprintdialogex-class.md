---
title: CPrintDialogEx 类
ms.date: 11/04/2016
f1_keywords:
- CPrintDialogEx
- AFXDLGS/CPrintDialogEx
- AFXDLGS/CPrintDialogEx::CPrintDialogEx
- AFXDLGS/CPrintDialogEx::CreatePrinterDC
- AFXDLGS/CPrintDialogEx::DoModal
- AFXDLGS/CPrintDialogEx::GetCopies
- AFXDLGS/CPrintDialogEx::GetDefaults
- AFXDLGS/CPrintDialogEx::GetDeviceName
- AFXDLGS/CPrintDialogEx::GetDevMode
- AFXDLGS/CPrintDialogEx::GetDriverName
- AFXDLGS/CPrintDialogEx::GetPortName
- AFXDLGS/CPrintDialogEx::GetPrinterDC
- AFXDLGS/CPrintDialogEx::PrintAll
- AFXDLGS/CPrintDialogEx::PrintCollate
- AFXDLGS/CPrintDialogEx::PrintCurrentPage
- AFXDLGS/CPrintDialogEx::PrintRange
- AFXDLGS/CPrintDialogEx::PrintSelection
- AFXDLGS/CPrintDialogEx::m_pdex
helpviewer_keywords:
- CPrintDialogEx [MFC], CPrintDialogEx
- CPrintDialogEx [MFC], CreatePrinterDC
- CPrintDialogEx [MFC], DoModal
- CPrintDialogEx [MFC], GetCopies
- CPrintDialogEx [MFC], GetDefaults
- CPrintDialogEx [MFC], GetDeviceName
- CPrintDialogEx [MFC], GetDevMode
- CPrintDialogEx [MFC], GetDriverName
- CPrintDialogEx [MFC], GetPortName
- CPrintDialogEx [MFC], GetPrinterDC
- CPrintDialogEx [MFC], PrintAll
- CPrintDialogEx [MFC], PrintCollate
- CPrintDialogEx [MFC], PrintCurrentPage
- CPrintDialogEx [MFC], PrintRange
- CPrintDialogEx [MFC], PrintSelection
- CPrintDialogEx [MFC], m_pdex
ms.assetid: 1d506703-ee1c-44cc-b4ce-4e778fec26b8
ms.openlocfilehash: 52e992cf021a592198daeddf0a4321fcea487f72
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364033"
---
# <a name="cprintdialogex-class"></a>CPrintDialogEx 类

封装 Windows 打印属性表提供的服务。

## <a name="syntax"></a>语法

```
class CPrintDialogEx : public CCommonDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CPrint对话Ex：CPrintDialogEx](#cprintdialogex)|构造 `CPrintDialogEx` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CPrint对话Ex：创建打印机DC](#createprinterdc)|创建打印机设备上下文而不显示"打印"对话框。|
|[CPrintDialogEx：:Do模态](#domodal)|显示对话框，并允许用户进行选择。|
|[CPrint对话Ex：获取副本](#getcopies)|检索请求的副本数。|
|[CPrint对话Ex：获取默认](#getdefaults)|检索设备默认值而不显示对话框。|
|[CPrint对话Ex：获取设备名称](#getdevicename)|检索当前选定的打印机设备的名称。|
|[CPrint对话前：获取DevMode](#getdevmode)|检索`DEVMODE`结构。|
|[CPrint对话Ex：获取驱动程序名称](#getdrivername)|检索系统定义的打印机设备驱动程序的名称。|
|[CPrint对话Ex：获取端口名称](#getportname)|检索当前选定的打印机端口的名称。|
|[CPrint对话Ex：获取打印机DC](#getprinterdc)|检索打印机设备上下文的句柄。|
|[CPrintDialogEx：:PrintAll](#printall)|确定是否打印文档的所有页面。|
|[CPrintDialogEx：:Printcollate](#printcollate)|确定是否请求整理副本。|
|[CPrintDialogEx：:PrintCurrentPage](#printcurrentpage)|确定是否打印文档的当前页面。|
|[CPrintDialogEx：:PrintRange](#printrange)|确定是否仅打印指定的页面范围。|
|[CPrintDialogEx：:Print选择](#printselection)|确定是否仅打印当前选定的项目。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CPrint对话Ex：：m_pdex](#m_pdex)|用于自定义对象的结构`CPrintDialogEx`。|

## <a name="remarks"></a>备注

您可以依赖框架来处理应用程序的打印过程的许多方面。 有关使用框架处理打印任务的详细信息，请参阅文章["打印](../../mfc/printing.md)"。

如果希望应用程序在没有框架参与的情况下处理打印，则可以将`CPrintDialogEx`类"按照"与提供的构造函数一起使用，也可以从`CPrintDialogEx`派生自己的对话框类并编写构造函数以满足您的需要。 在这两种情况下，这些对话框将类似于标准 MFC 对话框，因为它们派生自类`CCommonDialog`。

要使用`CPrintDialogEx`对象，请首先使用`CPrintDialogEx`构造函数创建对象。 构造对话框后，可以设置或修改[m_pdex](#m_pdex)结构中的任何值，以初始化对话框控件的值。 结构`m_pdex`为[PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw)型。 有关此结构的详细信息，请参阅 Windows SDK。

如果不`m_pdex`为`hDevMode`和`hDevNames`成员提供自己的句柄，请确保在使用对话框后调用这些句柄的 Windows`GlobalFree`函数。

初始化对话框控件后，调用`DoModal`成员函数以显示对话框，并允许用户选择打印选项。 返回`DoModal`时，您可以确定用户是否选择了"确定"、"应用"或"取消"按钮。

如果用户按"确定"，则可以使用`CPrintDialogEx`的成员函数检索用户输入的信息。

成员`CPrintDialogEx::GetDefaults`函数可用于检索当前打印机默认值，而不显示对话框。 此方法不需要用户交互。

可以使用 Windows`CommDlgExtendedError`函数确定在对话框初始化期间是否发生了错误，并了解有关该错误的详细信息。 有关此功能的详细信息，请参阅 Windows SDK。

有关 使用`CPrintDialogEx`的详细信息，请参阅[通用对话框类](../../mfc/common-dialog-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`IObjectWithSite`

`IPrintDialogCallback`

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialogEx`

## <a name="requirements"></a>要求

**标题：** afxdlgs.h

## <a name="cprintdialogexcprintdialogex"></a><a name="cprintdialogex"></a>CPrint对话Ex：CPrintDialogEx

构造 Windows 打印属性表。

```
CPrintDialogEx(
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS       | PD_HIDEPRINTTOFILE | PD_NOSELECTION | PD_NOCURRENTPAGE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

dwFlags**<br/>
可以使用一个或多个标志自定义对话框的设置，使用位或运算符组合使用。 例如，PD_ALLPAGES标志将默认打印范围设置到文档的所有页面。 有关这些标志的详细信息，请参阅 Windows SDK 中的[PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw)结构。

*pparentwnd*<br/>
指向对话框的父窗口或所有者窗口的指针。

### <a name="remarks"></a>备注

此成员函数仅构造对象。 使用`DoModal`成员函数显示对话框。

## <a name="cprintdialogexcreateprinterdc"></a><a name="createprinterdc"></a>CPrint对话Ex：创建打印机DC

从[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)和[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)结构创建打印机设备上下文 （DC）。

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>返回值

处理新创建的打印机设备上下文。

### <a name="remarks"></a>备注

返回的 DC 也存储在`hDC`[m_pdex](#m_pdex)的成员中。

此 DC 假定为当前打印机 DC，必须删除以前获得的任何其他打印机 DC。 可以调用此功能，并使用生成的 DC，而无需显示"打印"对话框。

## <a name="cprintdialogexdomodal"></a><a name="domodal"></a>CPrintDialogEx：:Do模态

调用此函数以显示 Windows Print 属性表，并允许用户选择各种打印选项，如副本数、页面范围以及是否应整理副本。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

INT_PTR返回值实际上是一个 HRESULT。 请参阅 Windows SDK 中的[PrintDlgEx](/previous-versions/windows/desktop/legacy/ms646942\(v=vs.85\))中的"返回值"部分。

### <a name="remarks"></a>备注

如果要通过设置`m_pdex`结构成员来初始化各种打印对话框选项，则应在调用`DoModal`之前执行此操作，但在构造对话框对象之后。

调用`DoModal`后 ，可以调用其他成员函数来检索用户输入到对话框中的设置或信息。

如果在调用`DoModal`时使用PD_RETURNDC标志，则打印机 DC 将在`hDC`[m_pdex](#m_pdex)的成员中返回。 此 DC 必须通过`CPrintDialogEx`调用 的[DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc)释放。

## <a name="cprintdialogexgetcopies"></a><a name="getcopies"></a>CPrint对话Ex：获取副本

调用`DoModal`后调用此函数以检索请求的副本数。

```
int GetCopies() const;
```

### <a name="return-value"></a>返回值

请求的副本数。

## <a name="cprintdialogexgetdefaults"></a><a name="getdefaults"></a>CPrint对话Ex：获取默认

调用此函数以检索默认打印机的设备默认值，而不显示对话框。

```
BOOL GetDefaults();
```

### <a name="return-value"></a>返回值

如果成功，则为 TRUE，否则为 FALSE。

### <a name="remarks"></a>备注

从[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)和[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)结构创建打印机设备上下文 （DC）。

`GetDefaults`不显示"打印"属性表。 `hDevNames`相反，它将[m_pdex](#m_pdex) `hDevMode`和 成员设置以处理为系统默认打印机初始化的[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)和[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)结构。 和`hDevNames``hDevMode`都必须为 NULL，`GetDefaults`否则。

如果`hDevNames`设置了PD_RETURNDC标志，此函数不仅会返回和`hDevMode`（位于`m_pdex.hDevNames`和`m_pdex.hDevMode`） 到调用方，而且还将在 中`m_pdex.hDC`返回打印机 DC。 调用方负责删除打印机 DC，并在处理`CPrintDialogEx`完对象后调用句柄上的 Windows [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree)函数。

## <a name="cprintdialogexgetdevicename"></a><a name="getdevicename"></a>CPrint对话Ex：获取设备名称

在调用[DoModal](#domodal)以检索当前所选打印机的名称后，或调用[GetDefaults](#getdefaults)以检索默认打印机的名称后调用此函数。

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>返回值

当前选定的打印机的名称。

### <a name="remarks"></a>备注

`CString`使用指向 返回`GetDeviceName`的对象的指针作为 调用`lpszDeviceName`[CDC：：：createDC](../../mfc/reference/cdc-class.md#createdc)中的值。

## <a name="cprintdialogexgetdevmode"></a><a name="getdevmode"></a>CPrint对话前：获取DevMode

调用[DoModal](#domodal)或[GetDefaults](#getdefaults)后调用此功能以检索有关打印设备的信息。

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>返回值

[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)数据结构，其中包含有关打印驱动程序的设备初始化和环境的信息。 您必须使用 Windows[全局解锁](/windows/win32/api/winbase/nf-winbase-globalunlock)功能解锁此结构占用的内存，该功能在 Windows SDK 中进行了描述。

## <a name="cprintdialogexgetdrivername"></a><a name="getdrivername"></a>CPrint对话Ex：获取驱动程序名称

调用[DoModal](#domodal)或[GetDefaults](#getdefaults)后调用此功能以检索系统定义的打印机设备驱动程序的名称。

```
CString GetDriverName() const;
```

### <a name="return-value"></a>返回值

指定`CString`系统定义的驱动程序名称。

### <a name="remarks"></a>备注

在调用[CDC：：：createDC](../../mfc/reference/cdc-class.md#createdc)中，使用作为*lpszDriverName*的值返回`CString``GetDriverName`的对象的指针。

## <a name="cprintdialogexgetportname"></a><a name="getportname"></a>CPrint对话Ex：获取端口名称

调用[DoModal](#domodal)或[GetDefaults](#getdefaults)后调用此功能以检索当前选定的打印机端口的名称。

```
CString GetPortName() const;
```

### <a name="return-value"></a>返回值

当前选定的打印机端口的名称。

## <a name="cprintdialogexgetprinterdc"></a><a name="getprinterdc"></a>CPrint对话Ex：获取打印机DC

将句柄返回到打印机设备上下文。

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>返回值

打印机设备上下文的句柄。

### <a name="remarks"></a>备注

使用完 Windows [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc)函数后，必须调用该函数以删除设备上下文。

## <a name="cprintdialogexm_pdex"></a><a name="m_pdex"></a>CPrint对话Ex：：m_pdex

一个 PRINTDLGEX 结构，其成员存储对话框对象的特征。

```
PRINTDLGEX m_pdex;
```

### <a name="remarks"></a>备注

构造`CPrintDialogEx`对象后，可以使用`m_pdex`在调用[DoModal](#domodal)成员函数之前设置对话框的各个方面。 有关`m_pdex`结构的详细信息，请参阅 Windows SDK 中的[PRINTDLGEX。](/windows/win32/api/commdlg/ns-commdlg-printdlgexw)

如果直接修改`m_pdex`数据成员，将覆盖任何默认行为。

## <a name="cprintdialogexprintall"></a><a name="printall"></a>CPrintDialogEx：:PrintAll

调用`DoModal`后调用此功能以确定是否打印文档中的所有页面。

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>返回值

如果要打印文档中的所有页面，则为 TRUE;否则 FALSE。

## <a name="cprintdialogexprintcollate"></a><a name="printcollate"></a>CPrintDialogEx：:Printcollate

调用`DoModal`后调用此功能以确定打印机是否应整理文档的所有打印副本。

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>返回值

如果用户在对话框中选择"校对"复选框，则为 TRUE;否则 FALSE。

## <a name="cprintdialogexprintcurrentpage"></a><a name="printcurrentpage"></a>CPrintDialogEx：:PrintCurrentPage

调用`DoModal`后调用此函数以确定是否在文档中打印当前页面。

```
BOOL PrintCurrentPage() const;
```

### <a name="return-value"></a>返回值

如果在打印对话框中选择"打印当前页面"，则为 TRUE;如果打印对话框中选择了 **"打印当前页面**"，则为 TRUE。否则 FALSE。

## <a name="cprintdialogexprintrange"></a><a name="printrange"></a>CPrintDialogEx：:PrintRange

调用`DoModal`后调用此功能以确定是否仅打印文档中的一系列页面。

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>返回值

如果只打印文档中的一系列页面，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

指定的页面范围可以从[m_pdex（](#m_pdex)请参阅`nPageRanges`）`nMaxPageRanges`和`lpPageRanges`在 Windows SDK 中的[PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw)结构中确定。

## <a name="cprintdialogexprintselection"></a><a name="printselection"></a>CPrintDialogEx：:Print选择

调用`DoModal`后调用此函数以确定是否仅打印当前选定的项目。

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>返回值

如果只打印所选项目，则为 TRUE;否则 FALSE。

## <a name="see-also"></a>另请参阅

[CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo 结构](../../mfc/reference/cprintinfo-structure.md)
