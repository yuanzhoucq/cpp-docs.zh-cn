---
title: CPrintDialogEx 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f511eb1414a5cd5e22b9a3e05f81caef15b908e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cprintdialogex-class"></a>CPrintDialogEx 类
封装由 Windows 打印属性表提供的服务。  
  
## <a name="syntax"></a>语法  
  
```  
class CPrintDialogEx : public CCommonDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CPrintDialogEx::CPrintDialogEx](#cprintdialogex)|构造 `CPrintDialogEx` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CPrintDialogEx::CreatePrinterDC](#createprinterdc)|创建打印机设备上下文而不显示打印对话框。|  
|[CPrintDialogEx::DoModal](#domodal)|显示对话框中，并允许用户进行选择。|  
|[CPrintDialogEx::GetCopies](#getcopies)|检索请求的副本数目。|  
|[CPrintDialogEx::GetDefaults](#getdefaults)|检索设备默认设置，而不显示一个对话框。|  
|[CPrintDialogEx::GetDeviceName](#getdevicename)|检索当前所选的打印机设备的名称。|  
|[CPrintDialogEx::GetDevMode](#getdevmode)|检索`DEVMODE`结构。|  
|[CPrintDialogEx::GetDriverName](#getdrivername)|检索系统定义的打印机设备驱动程序的名称。|  
|[CPrintDialogEx::GetPortName](#getportname)|检索当前所选的打印机端口的名称。|  
|[CPrintDialogEx::GetPrinterDC](#getprinterdc)|检索打印机设备上下文的句柄。|  
|[CPrintDialogEx::PrintAll](#printall)|确定是否打印文档的所有页面。|  
|[CPrintDialogEx::PrintCollate](#printcollate)|确定是否逐份打印副本请求。|  
|[CPrintDialogEx::PrintCurrentPage](#printcurrentpage)|确定是否打印文档的当前页。|  
|[CPrintDialogEx::PrintRange](#printrange)|确定是否打印指定的范围的页面。|  
|[CPrintDialogEx::PrintSelection](#printselection)|确定是否打印当前选定的项。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CPrintDialogEx::m_pdex](#m_pdex)|用于自定义的结构`CPrintDialogEx`对象。|  
  
## <a name="remarks"></a>备注  
 你可以依赖于框架，以处理你的应用程序的打印过程方面的诸多工作。 有关使用框架来处理打印作业的详细信息，请参阅文章[打印](../../mfc/printing.md)。  
  
 如果你希望应用程序处理打印而不需要的框架的参与，则可以使用`CPrintDialogEx`类"按原样"使用构造函数提供，或可以派生您自己的对话框类从`CPrintDialogEx`和写入以满足你需求的构造函数。 在任一情况下，这些对话框将行为类似于标准 MFC 对话框类派生因为`CCommonDialog`。  
  
 若要使用`CPrintDialogEx`对象，请首先创建对象使用`CPrintDialogEx`构造函数。 一旦构造的对话框中，你可以设置或修改中的任何值[m_pdex](#m_pdex)结构初始化对话框的控件的值。 `m_pdex`结构属于类型[PRINTDLGEX](http://msdn.microsoft.com/library/windows/desktop/ms646844)。 此结构的详细信息，请参阅 Windows SDK。  
  
 如果未提供你自己句柄`m_pdex`为**hDevMode**和**hDevNames**成员，一定要调用 Windows 函数**GlobalFree**这些句柄当你已完成的对话框中。  
  
 初始化对话框控件后, 调用`DoModal`成员函数，以显示对话框中，并允许用户选择打印选项。 当`DoModal`返回时，你可以确定用户是否选择确定、 应用或取消按钮。  
  
 如果用户按下确定，则可以使用`CPrintDialogEx`的成员函数以检索用户输入的信息。  
  
 `CPrintDialogEx::GetDefaults`成员函数可用于检索当前打印机默认值而不显示一个对话框。 此方法不需要用户交互。  
  
 你可以使用 Windows **CommDlgExtendedError**函数可确定在对话框中的初始化过程中是否发生了错误并了解有关错误的详细信息。 此函数的详细信息，请参阅 Windows SDK。  
  
 有关详细信息使用`CPrintDialogEx`，请参阅[通用对话框类](../../mfc/common-dialog-classes.md)。  
  
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
 `dwFlags`  
 可以使用自定义设置对话框中，使用按位 OR 运算符组合在一起的一个或多个标志。 例如， **PD_ALLPAGES**标志将默认打印范围设置为文档的所有页面。 请参阅[PRINTDLGEX](http://msdn.microsoft.com/library/windows/desktop/ms646844)这些标志的详细信息的 Windows SDK 中的结构。  
  
 `pParentWnd`  
 指向对话框的父或所有者窗口的指针。  
  
### <a name="remarks"></a>备注  
 此成员函数仅构造对象。 使用`DoModal`成员函数来显示对话框。  
  
##  <a name="createprinterdc"></a>  CPrintDialogEx::CreatePrinterDC  
 从创建打印机设备上下文 (DC) [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)和[DEVNAMES](../../mfc/reference/devnames-structure.md)结构。  
  
```  
HDC CreatePrinterDC();
```  
  
### <a name="return-value"></a>返回值  
 新创建的打印机设备上下文的句柄。  
  
### <a name="remarks"></a>备注  
 返回的 DC 也存储在**hDC**的成员[m_pdex](#m_pdex)。  
  
 此 DC 被假定为当前打印机 DC，和任何其他以前获取 Dc 必须删除的打印机。 可以调用此函数，并生成 DC 使用，而无曾经显示打印对话框。  
  
##  <a name="domodal"></a>  CPrintDialogEx::DoModal  
 调用此函数可显示 Windows 打印属性表，并让用户选择各种打印选项，如副本，页范围的数量和副本是否应进行分页。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 INT_PTR 的返回值是实际的 HRESULT。 请参阅中的返回值部分[PrintDlgEx](http://msdn.microsoft.com/library/windows/desktop/ms646942) Windows SDK 中。  
  
### <a name="remarks"></a>备注  
 如果你想要通过设置的成员初始化的各种打印对话框选项`m_pdex`结构，应执行此操作，然后再调`DoModal`，但在构造对话框对象之后。  
  
 在调用`DoModal`，您可以调用其他成员函数检索的设置或用户的信息输入到对话框。  
  
 如果**PD_RETURNDC**标志在调用时使用`DoModal`，会在返回打印机 DC **hDC**的成员[m_pdex](#m_pdex)。 必须通过调用释放此 DC [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533)由调用方的`CPrintDialogEx`。  
  
##  <a name="getcopies"></a>  CPrintDialogEx::GetCopies  
 调用此函数在调用`DoModal`检索请求的副本数目。  
  
```  
int GetCopies() const;  
```  
  
### <a name="return-value"></a>返回值  
 请求的副本数目。  
  
##  <a name="getdefaults"></a>  CPrintDialogEx::GetDefaults  
 调用此函数可检索默认打印机设备默认设置，而不显示一个对话框。  
  
```  
BOOL GetDefaults();
```  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果成功，否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 从创建打印机设备上下文 (DC) [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)和[DEVNAMES](../../mfc/reference/devnames-structure.md)结构。  
  
 `GetDefaults` 不显示打印属性表。 相反，它将设置**hDevNames**和**hDevMode**的成员[m_pdex](#m_pdex)句柄到[DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)和[DEVNAMES](../../mfc/reference/devnames-structure.md)的系统的默认打印机初始化的结构。 同时**hDevNames**和**hDevMode**必须为 NULL，或`GetDefaults`失败。  
  
 如果**PD_RETURNDC**设置标志，此函数不会只返回**hDevNames**和**hDevMode** (位于**m_pdex.hDevNames**和**m_pdex.hDevMode**) 向调用方，但也将返回中的打印机 DC **m_pdex.hDC**。 它负责调用方删除打印机 DC 并调用 Windows [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579)函数在完成的句柄`CPrintDialogEx`对象。  
  
##  <a name="getdevicename"></a>  CPrintDialogEx::GetDeviceName  
 调用此函数在调用[DoModal](#domodal)要检索其名称的当前选定的打印机，或在调用[GetDefaults](#getdefaults)检索默认打印机的名称。  
  
```  
CString GetDeviceName() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前选定的打印机的名称。  
  
### <a name="remarks"></a>备注  
 使用指向指针`CString`返回对象`GetDeviceName`的值作为`lpszDeviceName`对的调用中[CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc)。  
  
##  <a name="getdevmode"></a>  CPrintDialogEx::GetDevMode  
 调用此函数在调用[DoModal](#domodal)或[GetDefaults](#getdefaults)检索有关打印设备的信息。  
  
```  
LPDEVMODE GetDevMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)数据结构，其中包含有关设备初始化和打印驱动程序的环境的信息。 你必须首先解锁执行使用 Windows 此结构的内存[GlobalUnlock](http://msdn.microsoft.com/library/windows/desktop/aa366595)函数，Windows SDK 中所述。  
  
##  <a name="getdrivername"></a>  CPrintDialogEx::GetDriverName  
 调用此函数在调用[DoModal](#domodal)或[GetDefaults](#getdefaults)检索系统定义的打印机设备驱动程序的名称。  
  
```  
CString GetDriverName() const;  
```  
  
### <a name="return-value"></a>返回值  
 A`CString`指定系统定义的驱动程序名称。  
  
### <a name="remarks"></a>备注  
 使用指向指针`CString`返回对象`GetDriverName`的值作为`lpszDriverName`对的调用中[CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc)。  
  
##  <a name="getportname"></a>  CPrintDialogEx::GetPortName  
 调用此函数在调用[DoModal](#domodal)或[GetDefaults](#getdefaults)检索当前所选的打印机端口的名称。  
  
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
 必须调用 Windows [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533)可用于完成后删除的设备上下文函数使用它。  
  
##  <a name="m_pdex"></a>  CPrintDialogEx::m_pdex  
 其成员存储对话框对象的特征 PRINTDLGEX 结构。  
  
```  
PRINTDLGEX m_pdex;  
```  
  
### <a name="remarks"></a>备注  
 后构造`CPrintDialogEx`对象时，可以使用`m_pdex`设置对话框之前调用的各个方面[DoModal](#domodal)成员函数。 有关详细信息`m_pdex`结构，请参阅[PRINTDLGEX](http://msdn.microsoft.com/library/windows/desktop/ms646844) Windows SDK 中。  
  
 如果你修改`m_pdex`数据成员直接，您将重写任何默认行为。  
  
##  <a name="printall"></a>  CPrintDialogEx::PrintAll  
 调用此函数在调用`DoModal`确定是否要打印的文档中的所有页面。  
  
```  
BOOL PrintAll() const;  
```  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果文档中的所有页打印; 否则为**FALSE**。  
  
##  <a name="printcollate"></a>  CPrintDialogEx::PrintCollate  
 调用此函数在调用`DoModal`以确定打印机是否应 collate 所有打印的文档副本。  
  
```  
BOOL PrintCollate() const;  
```  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果用户选择 collate 复选框，在对话框中; 否则为**FALSE**。  
  
##  <a name="printcurrentpage"></a>  CPrintDialogEx::PrintCurrentPage  
 调用此函数在调用`DoModal`来确定是否打印文档中的当前页面。  
  
```  
BOOL PrintCurrentPage() const;  
```  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果**打印当前页**打印对话框中选定; 否则为**FALSE**。  
  
##  <a name="printrange"></a>  CPrintDialogEx::PrintRange  
 调用此函数在调用`DoModal`来确定是否打印仅范围内的文档中的页面。  
  
```  
BOOL PrintRange() const;  
```  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果只有一定范围的文档中的页打印; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 可以从确定指定的页范围[m_pdex](#m_pdex) (请参阅**nPageRanges**， **nMaxPageRanges**，和**lpPageRanges** 中[PRINTDLGEX](http://msdn.microsoft.com/library/windows/desktop/ms646844) Windows SDK 中的结构)。  
  
##  <a name="printselection"></a>  CPrintDialogEx::PrintSelection  
 调用此函数在调用`DoModal`来确定是否打印当前选定的项。  
  
```  
BOOL PrintSelection() const;  
```  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果只有所选的项目，则为打印; 否则为**FALSE**。  
  
## <a name="see-also"></a>另请参阅  
 [CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CPrintInfo 结构](../../mfc/reference/cprintinfo-structure.md)
