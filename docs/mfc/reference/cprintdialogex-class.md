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
ms.openlocfilehash: e5ddb2f7b5616acc0f275ad21599abedfbd8d060
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57268951"
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
|[CPrintDialogEx::CreatePrinterDC](#createprinterdc)|创建打印机设备上下文而不会显示打印对话框。|
|[CPrintDialogEx::DoModal](#domodal)|显示对话框中，并允许用户进行的选择。|
|[CPrintDialogEx::GetCopies](#getcopies)|检索请求的副本数目。|
|[CPrintDialogEx::GetDefaults](#getdefaults)|检索设备的默认值而不会显示一个对话框。|
|[CPrintDialogEx::GetDeviceName](#getdevicename)|检索当前所选的打印机设备的名称。|
|[CPrintDialogEx::GetDevMode](#getdevmode)|检索`DEVMODE`结构。|
|[CPrintDialogEx::GetDriverName](#getdrivername)|检索系统定义的打印机设备驱动程序的名称。|
|[CPrintDialogEx::GetPortName](#getportname)|检索当前所选的打印机端口的名称。|
|[CPrintDialogEx::GetPrinterDC](#getprinterdc)|检索打印机设备上下文的句柄。|
|[CPrintDialogEx::PrintAll](#printall)|确定是否将打印该文档的所有页。|
|[CPrintDialogEx::PrintCollate](#printcollate)|确定是否逐份打印副本请求。|
|[CPrintDialogEx::PrintCurrentPage](#printcurrentpage)|确定是否可以打印当前页的文档。|
|[CPrintDialogEx::PrintRange](#printrange)|确定是否将打印指定的范围的页面。|
|[CPrintDialogEx::PrintSelection](#printselection)|确定是否将打印当前选定的项。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CPrintDialogEx::m_pdex](#m_pdex)|用于自定义的结构`CPrintDialogEx`对象。|

## <a name="remarks"></a>备注

您可以依赖于框架来处理你的应用程序的打印过程的许多方面。 有关使用框架来处理打印任务的详细信息，请参阅文章[打印](../../mfc/printing.md)。

如果你希望应用程序来处理而不需要的 framework 参与打印，则可以使用`CPrintDialogEx`类构造函数提供，"按原样"也可以派生您自己的对话框类从`CPrintDialogEx`和编写构造函数以满足你的需求。 在任一情况下，这些对话框行为将类似于标准 MFC 对话框类派生因为`CCommonDialog`。

若要使用`CPrintDialogEx`对象，请先创建对象使用`CPrintDialogEx`构造函数。 一旦对话框的构造完成后，可以设置或修改中的任何值[m_pdex](#m_pdex)结构来初始化对话框的控件的值。 `m_pdex`结构属于类型[PRINTDLGEX](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa)。 此结构的详细信息，请参阅 Windows SDK。

如果不提供你自己句柄`m_pdex`有关`hDevMode`和`hDevNames`成员，一定要调用 Windows 函数`GlobalFree`这些句柄时完成的对话框。

初始化对话框控件之后, 调用`DoModal`成员函数以显示该对话框，并允许用户选择打印选项。 当`DoModal`返回时，您可以确定用户是否选择了确定、 应用或取消按钮。

如果用户按确定，则可以使用`CPrintDialogEx`的成员函数来检索用户输入的信息。

`CPrintDialogEx::GetDefaults`成员函数可用于检索当前打印机默认值而不会显示一个对话框。 此方法不需要用户交互。

可以使用 Windows`CommDlgExtendedError`函数来确定在对话框中的初始化过程中是否发生了错误并了解有关错误的详细信息。 此函数的详细信息，请参阅 Windows SDK。

有关使用的详细信息`CPrintDialogEx`，请参阅[通用对话框类](../../mfc/common-dialog-classes.md)。

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

**标头：** afxdlgs.h

##  <a name="cprintdialogex"></a>  CPrintDialogEx::CPrintDialogEx

构造 Windows 打印属性表。

```
CPrintDialogEx(
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS       | PD_HIDEPRINTTOFILE | PD_NOSELECTION | PD_NOCURRENTPAGE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*dwFlags*<br/>
可以使用自定义对话框中，使用按位 OR 运算符组合的设置的一个或多个标志。 例如，PD_ALLPAGES 标志将设置为该文档的所有页的默认打印范围。 请参阅[PRINTDLGEX](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa)适用于这些标志的详细信息的 Windows SDK 中的结构。

*pParentWnd*<br/>
指向对话框的父级或所有者窗口的指针。

### <a name="remarks"></a>备注

此成员函数仅构造的对象。 使用`DoModal`成员函数以显示该对话框。

##  <a name="createprinterdc"></a>  CPrintDialogEx::CreatePrinterDC

从创建打印机设备上下文 (DC) [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea)并[DEVNAMES](/windows/desktop/api/commdlg/ns-commdlg-tagdevnames)结构。

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>返回值

新创建的打印机设备上下文的句柄。

### <a name="remarks"></a>备注

返回的 DC 也存储在`hDC`的成员[m_pdex](#m_pdex)。

此 DC 被假定为当前打印机 DC，和任何其他以前获取的 Dc，必须先删除的打印机。 可以调用此函数，并使用生成的 DC，而不会不断显示打印对话框。

##  <a name="domodal"></a>  CPrintDialogEx::DoModal

调用此函数可显示 Windows 打印属性表，并允许用户选择的副本，页面范围数等各种打印选项和副本是否应进行分页。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

INT_PTR 的返回值是实际的 HRESULT。 请参阅中的返回值部分[PrintDlgEx](https://msdn.microsoft.com/library/windows/desktop/ms646942) Windows SDK 中。

### <a name="remarks"></a>备注

如果你想要通过设置的成员初始化的各种打印对话框选项`m_pdex`结构，应执行此操作之前调用`DoModal`，但在构造对话框对象之后。

在调用`DoModal`，可以调用其他成员函数来检索设置或用户的信息输入到对话框。

如果调用时使用 PD_RETURNDC 标志`DoModal`，将中返回是打印机`hDC`的成员[m_pdex](#m_pdex)。 此 DC，必须释放通过调用[DeleteDC](/windows/desktop/api/wingdi/nf-wingdi-deletedc)由调用方的`CPrintDialogEx`。

##  <a name="getcopies"></a>  CPrintDialogEx::GetCopies

调用后调用此函数`DoModal`检索请求的副本数目。

```
int GetCopies() const;
```

### <a name="return-value"></a>返回值

请求的副本数目。

##  <a name="getdefaults"></a>  CPrintDialogEx::GetDefaults

调用此函数可检索默认打印机的设备默认值而不会显示一个对话框。

```
BOOL GetDefaults();
```

### <a name="return-value"></a>返回值

如果成功，否则为 FALSE，则为 TRUE。

### <a name="remarks"></a>备注

从创建打印机设备上下文 (DC) [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea)并[DEVNAMES](/windows/desktop/api/commdlg/ns-commdlg-tagdevnames)结构。

`GetDefaults` 不显示打印属性表。 相反，它会设置`hDevNames`和`hDevMode`的成员[m_pdex](#m_pdex)到句柄[DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea)并[DEVNAMES](/windows/desktop/api/commdlg/ns-commdlg-tagdevnames)为初始化的结构系统默认打印机。 这两`hDevNames`并`hDevMode`必须为 NULL，或`GetDefaults`失败。

如果设置为 PD_RETURNDC 标志，此函数不会仅返回`hDevNames`和`hDevMode`(位于`m_pdex.hDevNames`并`m_pdex.hDevMode`) 给调用方，但也会返回打印机 DC 中的`m_pdex.hDC`。 它负责的调用方删除打印机 DC 并调用 Windows [GlobalFree](/windows/desktop/api/winbase/nf-winbase-globalfree)函数对句柄在您使用完`CPrintDialogEx`对象。

##  <a name="getdevicename"></a>  CPrintDialogEx::GetDeviceName

调用此函数后调用[DoModal](#domodal)要检索其名称的当前选定的打印机，或在调用[GetDefaults](#getdefaults)检索默认打印机的名称。

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>返回值

当前所选打印机的名称。

### <a name="remarks"></a>备注

使用指向指针`CString`返回的对象`GetDeviceName`的值作为`lpszDeviceName`对的调用中[CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc)。

##  <a name="getdevmode"></a>  CPrintDialogEx::GetDevMode

调用此函数后调用[DoModal](#domodal)或[GetDefaults](#getdefaults)来检索有关打印设备的信息。

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>返回值

[DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea)数据结构，其中包含有关设备初始化和环境的打印驱动程序的信息。 您必须解除锁定此结构与 Windows 所占用的内存[GlobalUnlock](/windows/desktop/api/winbase/nf-winbase-globalunlock)函数，Windows SDK 中所述。

##  <a name="getdrivername"></a>  CPrintDialogEx::GetDriverName

调用此函数后调用[DoModal](#domodal)或[GetDefaults](#getdefaults)检索系统定义的打印机设备驱动程序的名称。

```
CString GetDriverName() const;
```

### <a name="return-value"></a>返回值

一个`CString`指定的系统定义的驱动程序名称。

### <a name="remarks"></a>备注

使用指向指针`CString`返回的对象`GetDriverName`的值作为*lpszDriverName*对的调用中[CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc)。

##  <a name="getportname"></a>  CPrintDialogEx::GetPortName

调用此函数后调用[DoModal](#domodal)或[GetDefaults](#getdefaults)来检索当前所选的打印机端口的名称。

```
CString GetPortName() const;
```

### <a name="return-value"></a>返回值

当前所选的打印机端口的名称。

##  <a name="getprinterdc"></a>  CPrintDialogEx::GetPrinterDC

返回的句柄打印机设备上下文。

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>返回值

打印机设备上下文的句柄。

### <a name="remarks"></a>备注

必须调用 Windows [DeleteDC](/windows/desktop/api/wingdi/nf-wingdi-deletedc)函数完成后删除的设备上下文使用它。

##  <a name="m_pdex"></a>  CPrintDialogEx::m_pdex

PRINTDLGEX 结构，其成员存储对话框对象的特征。

```
PRINTDLGEX m_pdex;
```

### <a name="remarks"></a>备注

构造后`CPrintDialogEx`对象，可以使用`m_pdex`若要设置之前，调用对话框中的各个方面[DoModal](#domodal)成员函数。 有关详细信息`m_pdex`结构，请参阅[PRINTDLGEX](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa) Windows SDK 中。

如果您修改`m_pdex`数据成员直接，您将重写任何默认行为。

##  <a name="printall"></a>  CPrintDialogEx::PrintAll

调用后调用此函数`DoModal`来确定是否打印在文档中的所有页。

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>返回值

如果在文档中的所有页面都都要打印; 则为 TRUE否则为 FALSE。

##  <a name="printcollate"></a>  CPrintDialogEx::PrintCollate

调用后调用此函数`DoModal`来确定打印机是否应逐份打印文档的所有打印的副本。

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>返回值

如果用户在对话框中，选择逐份打印复选框，则返回 TRUE否则为 FALSE。

##  <a name="printcurrentpage"></a>  CPrintDialogEx::PrintCurrentPage

调用后调用此函数`DoModal`来确定是否打印在文档中的当前页面。

```
BOOL PrintCurrentPage() const;
```

### <a name="return-value"></a>返回值

则为 TRUE**打印当前页**打印对话框中选定; 否则为 FALSE。

##  <a name="printrange"></a>  CPrintDialogEx::PrintRange

调用后调用此函数`DoModal`来确定是否打印仅范围内的文档中的页面。

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>返回值

如果只有一系列文档中的页面的打印; 该值为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

可以根据指定的页范围[m_pdex](#m_pdex) (请参阅`nPageRanges`， `nMaxPageRanges`，并`lpPageRanges`中[PRINTDLGEX](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa) Windows SDK 中的结构)。

##  <a name="printselection"></a>  CPrintDialogEx::PrintSelection

调用后调用此函数`DoModal`以确定是否打印当前选定的项。

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>返回值

如果只有所选的项目为要打印;，则返回 TRUE否则为 FALSE。

## <a name="see-also"></a>请参阅

[CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo 结构](../../mfc/reference/cprintinfo-structure.md)
