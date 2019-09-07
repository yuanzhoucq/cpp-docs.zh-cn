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
ms.openlocfilehash: 76c3968b20a66e9653fd769339e23ede2a756bbd
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741326"
---
# <a name="cprintdialogex-class"></a>CPrintDialogEx 类

封装由 Windows 打印属性表提供的服务。

## <a name="syntax"></a>语法

```
class CPrintDialogEx : public CCommonDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CPrintDialogEx::CPrintDialogEx](#cprintdialogex)|构造 `CPrintDialogEx` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CPrintDialogEx::CreatePrinterDC](#createprinterdc)|在不显示 "打印" 对话框的情况下创建打印机设备上下文。|
|[CPrintDialogEx::DoModal](#domodal)|显示对话框并允许用户进行选择。|
|[CPrintDialogEx::GetCopies](#getcopies)|检索请求的副本数。|
|[CPrintDialogEx::GetDefaults](#getdefaults)|在不显示对话框的情况下检索设备默认值。|
|[CPrintDialogEx::GetDeviceName](#getdevicename)|检索当前所选打印机设备的名称。|
|[CPrintDialogEx::GetDevMode](#getdevmode)|`DEVMODE`检索结构。|
|[CPrintDialogEx::GetDriverName](#getdrivername)|检索系统定义的打印机设备驱动程序的名称。|
|[CPrintDialogEx::GetPortName](#getportname)|检索当前选定的打印机端口的名称。|
|[CPrintDialogEx::GetPrinterDC](#getprinterdc)|检索打印机设备上下文的句柄。|
|[CPrintDialogEx::PrintAll](#printall)|确定是否打印文档的所有页。|
|[CPrintDialogEx::PrintCollate](#printcollate)|确定是否请求逐份打印副本。|
|[CPrintDialogEx::PrintCurrentPage](#printcurrentpage)|确定是否打印文档的当前页。|
|[CPrintDialogEx::PrintRange](#printrange)|确定是否仅打印指定范围的页面。|
|[CPrintDialogEx::PrintSelection](#printselection)|确定是否仅打印当前选定的项。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CPrintDialogEx::m_pdex](#m_pdex)|用于自定义`CPrintDialogEx`对象的结构。|

## <a name="remarks"></a>备注

您可以依赖于框架来处理应用程序打印过程的许多方面。 有关使用框架来处理打印任务的详细信息，请参阅文章[打印](../../mfc/printing.md)。

如果希望应用程序在不使用框架的情况下处理打印，则可以使用提供`CPrintDialogEx`的构造函数的 "按原样" 类，也可以从`CPrintDialogEx`派生您自己的对话类，并编写一个构造函数来满足您的需求。 在这两种情况下，这些对话框的行为类似于标准 MFC 对话框，因为它们是`CCommonDialog`从类派生的。

若要使用`CPrintDialogEx`对象，请先`CPrintDialogEx`使用构造函数创建对象。 构造该对话框后，您可以设置或修改[m_pdex](#m_pdex)结构中的任何值以初始化对话框控件的值。 结构的类型为[PRINTDLGEX。](/windows/win32/api/commdlg/ns-commdlg-printdlgexw) `m_pdex` 有关此结构的详细信息，请参阅 Windows SDK。

如果没有`m_pdex` `GlobalFree`为和成员`hDevNames`提供自己的句柄，请确保在完成该对话框后，为这些句柄调用 Windows 函数。 `hDevMode`

初始化对话框控件后，调用`DoModal`成员函数以显示对话框，并允许用户选择打印选项。 返回`DoModal`时，可以确定用户是否选择了 "确定"、"应用" 或 "取消" 按钮。

如果用户按 "确定"，则可以`CPrintDialogEx`使用的成员函数来检索用户输入的信息。

此`CPrintDialogEx::GetDefaults`成员函数可用于检索当前打印机默认值，而不会显示对话框。 此方法无需用户交互。

您可以使用 Windows `CommDlgExtendedError`函数来确定初始化对话框期间是否发生了错误，并了解有关该错误的详细信息。 有关此函数的详细信息，请参阅 Windows SDK。

有关使用`CPrintDialogEx`的详细信息，请参阅[通用对话框类](../../mfc/common-dialog-classes.md)。

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

**标头：** afxdlgs

##  <a name="cprintdialogex"></a>  CPrintDialogEx::CPrintDialogEx

构造 Windows 打印属性表。

```
CPrintDialogEx(
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS       | PD_HIDEPRINTTOFILE | PD_NOSELECTION | PD_NOCURRENTPAGE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*dwFlags*<br/>
可用于自定义对话框的设置的一个或多个标志，使用按位 "或" 运算符组合在一起。 例如，PD_ALLPAGES 标志将默认打印范围设置为文档的所有页。 有关这些标志的详细信息，请参阅 Windows SDK 中的[PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw)结构。

*pParentWnd*<br/>
指向对话框的父窗口或所有者窗口的指针。

### <a name="remarks"></a>备注

此成员函数仅构造对象。 `DoModal`使用成员函数来显示对话框。

##  <a name="createprinterdc"></a>  CPrintDialogEx::CreatePrinterDC

从[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)和[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)结构创建打印机设备上下文（DC）。

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>返回值

新创建的打印机设备上下文的句柄。

### <a name="remarks"></a>备注

返回的 DC 还会存储在`hDC` [m_pdex](#m_pdex)的成员中。

此 DC 被假定为当前打印机 DC，并且必须删除任何其他以前获得的打印机 Dc。 可以调用此函数，并使用生成的 DC，无需显示 "打印" 对话框。

##  <a name="domodal"></a>  CPrintDialogEx::DoModal

调用此函数以显示 Windows Print 属性表，并允许用户选择各种打印选项，如副本数、页面范围以及是否应逐份打印副本。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

INT_PTR 返回值实际上是 HRESULT。 请参阅 Windows SDK 中[PrintDlgEx](/previous-versions/windows/desktop/legacy/ms646942\(v=vs.85\))的返回值部分。

### <a name="remarks"></a>备注

如果希望通过设置`m_pdex`结构的成员来初始化各种打印对话框选项，应在调用`DoModal`之前执行此操作，但在构造对话框对象之后。

调用`DoModal`后，可以调用其他成员函数来检索用户在对话框中输入的设置或信息。

如果在调用`DoModal`时使用了 PD_RETURNDC 标志，则将`hDC`在[m_pdex](#m_pdex)的成员中返回打印机 DC。 必须通过调用方`CPrintDialogEx`调用[DELETEDC](/windows/win32/api/wingdi/nf-wingdi-deletedc)来释放此 DC。

##  <a name="getcopies"></a>  CPrintDialogEx::GetCopies

在调用`DoModal`以检索请求的副本数后调用此函数。

```
int GetCopies() const;
```

### <a name="return-value"></a>返回值

请求的副本数。

##  <a name="getdefaults"></a>  CPrintDialogEx::GetDefaults

调用此函数可检索默认打印机的设备默认值，而不会显示对话框。

```
BOOL GetDefaults();
```

### <a name="return-value"></a>返回值

如果成功，则为 TRUE; 否则为 FALSE。

### <a name="remarks"></a>备注

从[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)和[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)结构创建打印机设备上下文（DC）。

`GetDefaults`不显示打印属性页。 相反`hDevNames` ，它将[m_pdex](#m_pdex)的`hDevMode`和成员设置为处理系统默认打印机的[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)和[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)结构。 `GetDefaults`和`hDevNames` 都`hDevMode`必须为 NULL 或失败。

如果设置了 PD_RETURNDC 标志，则此函数将不会只`hDevNames`返回`hDevMode`调用方的`m_pdex.hDevNames`和`m_pdex.hDevMode`（位于和中），但也将在中`m_pdex.hDC`返回打印机 DC。 当您完成`CPrintDialogEx`对象时，调用方负责删除打印机 DC 并在句柄上调用 Windows [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree)函数。

##  <a name="getdevicename"></a>  CPrintDialogEx::GetDeviceName

在调用[DoModal](#domodal)以检索当前所选打印机的名称后，或在调用[GetDefaults](#getdefaults)检索默认打印机的名称后，调用此函数。

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>返回值

当前选定的打印机的名称。

### <a name="remarks"></a>备注

在对[CDC：： CreateDC](../../mfc/reference/cdc-class.md#createdc)的调用`GetDeviceName`中，使用指向`lpszDeviceName` `CString`返回的对象的指针作为的值。

##  <a name="getdevmode"></a>  CPrintDialogEx::GetDevMode

在调用[DoModal](#domodal)或[GetDefaults](#getdefaults)后调用此函数可检索有关打印设备的信息。

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>返回值

[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)数据结构，其中包含有关打印机驱动程序的设备初始化和环境的信息。 必须使用 Windows SDK 中描述的 Windows [GlobalUnlock](/windows/win32/api/winbase/nf-winbase-globalunlock)函数来解锁此结构使用的内存。

##  <a name="getdrivername"></a>  CPrintDialogEx::GetDriverName

在调用[DoModal](#domodal)或[GetDefaults](#getdefaults)后调用此函数可检索系统定义的打印机设备驱动程序的名称。

```
CString GetDriverName() const;
```

### <a name="return-value"></a>返回值

一个`CString` ，指定系统定义的驱动程序名称。

### <a name="remarks"></a>备注

在对[CDC：： CreateDC](../../mfc/reference/cdc-class.md#createdc)的调用`GetDriverName`中，使用指向`CString`作为*lpszDriverName*值返回的对象的指针。

##  <a name="getportname"></a>  CPrintDialogEx::GetPortName

调用[DoModal](#domodal)或[GetDefaults](#getdefaults)后调用此函数可检索当前选定的打印机端口的名称。

```
CString GetPortName() const;
```

### <a name="return-value"></a>返回值

当前选定的打印机端口的名称。

##  <a name="getprinterdc"></a>  CPrintDialogEx::GetPrinterDC

返回打印机设备上下文的句柄。

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>返回值

打印机设备上下文的句柄。

### <a name="remarks"></a>备注

使用 Windows [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc)函数时，必须调用该函数以删除设备上下文。

##  <a name="m_pdex"></a>  CPrintDialogEx::m_pdex

一个 PRINTDLGEX 结构，其成员存储对话框对象的特征。

```
PRINTDLGEX m_pdex;
```

### <a name="remarks"></a>备注

构造`CPrintDialogEx`对象之后，您可以使用`m_pdex`在调用[DoModal](#domodal)成员函数之前设置对话框的各个方面。 有关`m_pdex`结构的详细信息，请参阅 Windows SDK 中的[PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw) 。

如果直接修改`m_pdex`数据成员，将重写任何默认行为。

##  <a name="printall"></a>  CPrintDialogEx::PrintAll

调用`DoModal`后调用此函数可确定是否要打印文档中的所有页。

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>返回值

如果文档中的所有页面都要打印，则为 TRUE;否则为 FALSE。

##  <a name="printcollate"></a>  CPrintDialogEx::PrintCollate

调用`DoModal`后调用此函数可确定打印机是否应逐份打印文档的所有打印副本。

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>返回值

如果用户在对话框中选中了 "逐份打印" 复选框，则为 TRUE;否则为 FALSE。

##  <a name="printcurrentpage"></a>  CPrintDialogEx::PrintCurrentPage

在调用`DoModal`后调用此函数可确定是否在文档中打印当前页。

```
BOOL PrintCurrentPage() const;
```

### <a name="return-value"></a>返回值

如果在 "打印" 对话框中选择了 "**打印当前页**"，则为 TRUE;否则为 FALSE。

##  <a name="printrange"></a>  CPrintDialogEx::PrintRange

调用`DoModal`后调用此函数可确定是否仅打印文档中的一系列页面。

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>返回值

如果仅打印文档中的一系列页面，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

指定的页范围可以从[m_pdex](#m_pdex)确定（请参阅`nPageRanges`、 `nMaxPageRanges`和`lpPageRanges` ，在[PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw)结构的 Windows SDK）中。

##  <a name="printselection"></a>  CPrintDialogEx::PrintSelection

调用`DoModal`后调用此函数可确定是否仅打印当前选定的项。

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>返回值

如果仅打印选定项，则为 TRUE;否则为 FALSE。

## <a name="see-also"></a>请参阅

[CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo 结构](../../mfc/reference/cprintinfo-structure.md)
