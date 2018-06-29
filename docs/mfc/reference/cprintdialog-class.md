---
title: CPrintDialog 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPrintDialog
- AFXDLGS/CPrintDialog
- AFXDLGS/CPrintDialog::CPrintDialog
- AFXDLGS/CPrintDialog::CreatePrinterDC
- AFXDLGS/CPrintDialog::DoModal
- AFXDLGS/CPrintDialog::GetCopies
- AFXDLGS/CPrintDialog::GetDefaults
- AFXDLGS/CPrintDialog::GetDeviceName
- AFXDLGS/CPrintDialog::GetDevMode
- AFXDLGS/CPrintDialog::GetDriverName
- AFXDLGS/CPrintDialog::GetFromPage
- AFXDLGS/CPrintDialog::GetPortName
- AFXDLGS/CPrintDialog::GetPrinterDC
- AFXDLGS/CPrintDialog::GetToPage
- AFXDLGS/CPrintDialog::PrintAll
- AFXDLGS/CPrintDialog::PrintCollate
- AFXDLGS/CPrintDialog::PrintRange
- AFXDLGS/CPrintDialog::PrintSelection
- AFXDLGS/CPrintDialog::m_pd
dev_langs:
- C++
helpviewer_keywords:
- CPrintDialog [MFC], CPrintDialog
- CPrintDialog [MFC], CreatePrinterDC
- CPrintDialog [MFC], DoModal
- CPrintDialog [MFC], GetCopies
- CPrintDialog [MFC], GetDefaults
- CPrintDialog [MFC], GetDeviceName
- CPrintDialog [MFC], GetDevMode
- CPrintDialog [MFC], GetDriverName
- CPrintDialog [MFC], GetFromPage
- CPrintDialog [MFC], GetPortName
- CPrintDialog [MFC], GetPrinterDC
- CPrintDialog [MFC], GetToPage
- CPrintDialog [MFC], PrintAll
- CPrintDialog [MFC], PrintCollate
- CPrintDialog [MFC], PrintRange
- CPrintDialog [MFC], PrintSelection
- CPrintDialog [MFC], m_pd
ms.assetid: 5bdb2424-adf8-433d-a97c-df11a83bc4e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d72b96e0be786aab18903e95f346eccd5364dd4b
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079641"
---
# <a name="cprintdialog-class"></a>CPrintDialog 类
封装由 Windows 公共对话框提供的打印服务。  
  
## <a name="syntax"></a>语法  
  
```  
class CPrintDialog : public CCommonDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CPrintDialog::CPrintDialog](#cprintdialog)|构造 `CPrintDialog` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CPrintDialog::CreatePrinterDC](#createprinterdc)|创建打印机设备上下文而不显示打印对话框。|  
|[CPrintDialog::DoModal](#domodal)|显示对话框中，并允许用户进行选择。|  
|[CPrintDialog::GetCopies](#getcopies)|检索请求的副本数目。|  
|[CPrintDialog::GetDefaults](#getdefaults)|检索设备默认设置，而不显示一个对话框。|  
|[CPrintDialog::GetDeviceName](#getdevicename)|检索当前所选的打印机设备的名称。|  
|[CPrintDialog::GetDevMode](#getdevmode)|检索`DEVMODE`结构。|  
|[CPrintDialog::GetDriverName](#getdrivername)|检索当前所选的打印机驱动程序的名称。|  
|[CPrintDialog::GetFromPage](#getfrompage)|检索打印范围的起始页。|  
|[CPrintDialog::GetPortName](#getportname)|检索当前所选的打印机端口的名称。|  
|[CPrintDialog::GetPrinterDC](#getprinterdc)|检索打印机设备上下文的句柄。|  
|[CPrintDialog::GetToPage](#gettopage)|检索打印范围的结束页。|  
|[CPrintDialog::PrintAll](#printall)|确定是否打印文档的所有页面。|  
|[CPrintDialog::PrintCollate](#printcollate)|确定是否逐份打印副本请求。|  
|[CPrintDialog::PrintRange](#printrange)|确定是否打印指定的范围的页面。|  
|[CPrintDialog::PrintSelection](#printselection)|确定是否打印当前选定的项。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CPrintDialog::m_pd](#m_pd)|用于自定义的结构`CPrintDialog`对象。|  
  
## <a name="remarks"></a>备注  
 通用打印对话框提供与 Windows 标准一致的方式实现打印和打印设置对话框的简单办法。  
  
> [!NOTE]
>  `CPrintDialogEx`类封装由 Windows 打印属性表提供的服务。 有关详细信息请参阅[CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md)概述。  
  
 `CPrintDialog`功能被取代的[CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)，该方法旨在提供通用对话框中，为同时打印设置和页面设置。  
  
 你可以依赖于框架，以处理你的应用程序的打印过程方面的诸多工作。 在这种情况下，框架会自动显示 Windows 公共对话框进行打印。 也可具有你的应用程序打印的 framework 句柄，但重写通用的打印对话框，使用你自己的打印对话框。 有关使用框架来处理打印作业的详细信息，请参阅文章[打印](../../mfc/printing.md)。  
  
 如果你希望应用程序处理打印而不需要的框架的参与，则可以使用`CPrintDialog`类"按原样"使用构造函数提供，或可以派生您自己的对话框类从`CPrintDialog`和写入以满足你需求的构造函数。 在任一情况下，这些对话框将行为类似于标准 MFC 对话框类派生因为`CCommonDialog`。  
  
 若要使用`CPrintDialog`对象，请首先创建对象使用`CPrintDialog`构造函数。 一旦构造的对话框中，你可以设置或修改中的任何值[m_pd](#m_pd)结构初始化对话框的控件的值。 `m_pd`结构属于类型[PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843)。 此结构的详细信息，请参阅 Windows SDK。  
  
 如果未提供你自己句柄`m_pd`为**hDevMode**和**hDevNames**成员，一定要调用 Windows 函数**GlobalFree**这些句柄当你已完成的对话框中。 使用由提供的框架的打印设置实现时`CWinApp::OnFilePrintSetup`，则不需要释放这些句柄。 句柄由维护`CWinApp`并且在释放`CWinApp`的析构函数。 它只是用来释放这些句柄时使用`CPrintDialog`独立。  
  
 初始化对话框控件后, 调用`DoModal`成员函数，以显示对话框中，并允许用户选择打印选项。 `DoModal` 返回用户是否选择确定 ( **IDOK**) 或取消 ( **IDCANCEL**) 按钮。  
  
 如果`DoModal`返回**IDOK**，你可以使用之一`CPrintDialog`的成员函数以检索用户输入的信息。  
  
 `CPrintDialog::GetDefaults`成员函数可用于检索当前打印机默认值而不显示一个对话框。 此成员函数不需要用户交互。  
  
 你可以使用 Windows **CommDlgExtendedError**函数可确定在对话框中的初始化过程中是否发生了错误并了解有关错误的详细信息。 此函数的详细信息，请参阅 Windows SDK。  
  
 `CPrintDialog` 依赖于 COMMDLG。随 Windows 版本 3.1 和更高版本一起提供的 DLL 文件。  
  
 要自定义对话框中，从派生类`CPrintDialog`，提供自定义对话框模板，并添加一个消息映射来处理来自扩展控件的通知消息。 任何未处理的消息应传递到基类上。 自定义挂钩函数不是必需的。  
  
 若要处理同一消息以不同的方式根据对话框中是否打印或打印设置，必须派生每个对话框中的类。 此外必须重写 Windows **AttachOnSetup**函数，在打印对话框中选中打印设置按钮时处理新的对话框中的创建。  
  
 有关详细信息使用`CPrintDialog`，请参阅[通用对话框类](../../mfc/common-dialog-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CPrintDialog`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdlgs.h  
  
##  <a name="cprintdialog"></a>  CPrintDialog::CPrintDialog  
 构造 Windows 打印或打印设置对话框对象。  
  
```  
CPrintDialog(
    BOOL bPrintSetupOnly,  
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 *bPrintSetupOnly*  
 指定是否显示的标准 Windows 打印对话框中或打印设置对话框。 将此参数设置为**TRUE**以显示标准的 Windows 打印设置对话框。 将其设置为**FALSE**以显示 Windows 打印对话框。 如果*bPrintSetupOnly*是**FALSE**，打印设置选项按钮仍显示在打印对话框中。  
  
 *dwFlags*  
 可以使用自定义设置对话框中，使用按位 OR 运算符组合在一起的一个或多个标志。 例如， **PD_ALLPAGES**标志将默认打印范围设置为文档的所有页面。 请参阅[PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843)这些标志的详细信息的 Windows SDK 中的结构。  
  
 *pParentWnd*  
 指向对话框的父或所有者窗口的指针。  
  
### <a name="remarks"></a>备注  
 此成员函数仅构造对象。 使用`DoModal`成员函数来显示对话框。  
  
 请注意，当你调用具有构造函数`bPrintSetupOnly`设置为**FALSE**、 **PD_RETURNDC**标志会自动使用。 在调用`DoModal`， `GetDefaults`，或`GetPrinterDC`，会在返回打印机 DC `m_pd.hDC`。 必须通过调用释放此 DC [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533)由调用方的`CPrintDialog`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#174](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]  
  
##  <a name="createprinterdc"></a>  CPrintDialog::CreatePrinterDC  
 从创建打印机设备上下文 (DC) [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)和[DEVNAMES](../../mfc/reference/devnames-structure.md)结构。  
  
```  
HDC CreatePrinterDC();
```  
  
### <a name="return-value"></a>返回值  
 新创建的打印机设备上下文的句柄。  
  
### <a name="remarks"></a>备注  
 此 DC 被假定为当前打印机 DC，和任何其他以前获取 Dc 必须由用户删除的打印机。 可以调用此函数，并生成 DC 使用，而无曾经显示打印对话框。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#106](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]  
  
##  <a name="domodal"></a>  CPrintDialog::DoModal  
 显示 Windows 公共打印对话框，并允许用户选择各种打印选项，如副本，页范围的数量和副本是否应进行分页。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 **IDOK**或**IDCANCEL**。 如果**IDCANCEL**是返回，调用 Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916)函数来确定是否发生了错误。  
  
 **IDOK**和**IDCANCEL**是指示用户是否选中确定或取消按钮的常量。  
  
### <a name="remarks"></a>备注  
 如果你想要通过设置的成员初始化的各种打印对话框选项`m_pd`结构，应执行此操作，然后再调`DoModal`，但在构造对话框对象之后。  
  
 在调用`DoModal`，您可以调用其他成员函数检索的设置或用户的信息输入到对话框。  
  
 请注意，当你调用具有构造函数*bPrintSetupOnly*设置为**FALSE**、 **PD_RETURNDC**标志会自动使用。 在调用`DoModal`， `GetDefaults`，或`GetPrinterDC`，会在返回打印机 DC `m_pd.hDC`。 必须通过调用释放此 DC [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533)由调用方的`CPrintDialog`。  
  
### <a name="example"></a>示例  
  请参阅示例[CPrintDialog::CreatePrinterDC](#createprinterdc)。  
  
##  <a name="getcopies"></a>  CPrintDialog::GetCopies  
 检索请求的副本数目。  
  
```  
int GetCopies() const;  
```  
  
### <a name="return-value"></a>返回值  
 请求的副本数目。  
  
### <a name="remarks"></a>备注  
 调用此函数在调用`DoModal`检索请求的副本数目。  
  
### <a name="example"></a>示例  
  请参阅示例[CPrintDialog::PrintCollate](#printcollate)。  
  
##  <a name="getdefaults"></a>  CPrintDialog::GetDefaults  
 检索默认打印机的设备默认值而不显示一个对话框。  
  
```  
BOOL GetDefaults();
```  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则为 0。  
  
### <a name="remarks"></a>备注  
 检索到的值都将置于`m_pd`结构。  
  
 在某些情况下，对此函数的调用将调用[构造函数](#cprintdialog)为`CPrintDialog`与*bPrintSetupOnly*设置为**FALSE**。 在这些情况下，打印机 DC 和**hDevNames**和**hDevMode** (两个控点位于`m_pd`数据成员) 自动分配。  
  
 如果的构造函数`CPrintDialog`调用时使用`bPrintSetupOnly`设置为**FALSE**，此函数不会只返回**hDevNames**和**hDevMode** （位于**m_pd.hDevNames**和**m_pd.hDevMode**) 向调用方，但也将返回中的打印机 DC **m_pd.hDC**。 它负责调用方删除打印机 DC 并调用 Windows [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579)函数在完成的句柄`CPrintDialog`对象。  
  
### <a name="example"></a>示例  
 此代码段获取默认打印机设备上下文，并向用户报告以每英寸点数打印机的分辨率。 （此属性的打印机的功能通常称为 DPI。）  
  
 [!code-cpp[NVC_MFCDocView#107](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]  
  
##  <a name="getdevicename"></a>  CPrintDialog::GetDeviceName  
 检索当前所选的打印机设备的名称。  
  
```  
CString GetDeviceName() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前选定的打印机的名称。  
  
### <a name="remarks"></a>备注  
 调用此函数在调用[DoModal](#domodal)要检索其名称的当前选定的打印机，或在调用[GetDefaults](#getdefaults)检索当前设备默认设置的默认打印机。 使用指向指针`CString`返回对象`GetDeviceName`的值作为`lpszDeviceName`对的调用中[CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc)。  
  
### <a name="example"></a>示例  
 此代码片段演示用户的默认打印机名称和连接，以及打印机使用的后台处理程序名称的端口。 该代码可能会显示一个消息框，显示"默认打印机位于 HP LaserJet IIIP \\\server\share 使用 winspool。"，例如。  
  
 [!code-cpp[NVC_MFCDocView#108](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]  
  
##  <a name="getdevmode"></a>  CPrintDialog::GetDevMode  
 检索`DEVMODE`结构。  
  
```  
LPDEVMODE GetDevMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)数据结构，其中包含有关设备初始化和打印驱动程序的环境的信息。 你必须首先解锁执行使用 Windows 此结构的内存[GlobalUnlock](http://msdn.microsoft.com/library/windows/desktop/aa366595)函数，Windows SDK 中所述。  
  
### <a name="remarks"></a>备注  
 调用此函数在调用[DoModal](#domodal)或[GetDefaults](#getdefaults)检索有关打印设备的信息。  
  
### <a name="example"></a>示例  
  请参阅示例[CPrintDialog::PrintCollate](#printcollate)。  
  
##  <a name="getdrivername"></a>  CPrintDialog::GetDriverName  
 检索当前所选的打印机驱动程序的名称。  
  
```  
CString GetDriverName() const;  
```  
  
### <a name="return-value"></a>返回值  
 A`CString`指定系统定义的驱动程序名称。  
  
### <a name="remarks"></a>备注  
 调用此函数在调用[DoModal](#domodal)或[GetDefaults](#getdefaults)检索系统定义的打印机设备驱动程序的名称。 使用指向指针`CString`返回对象`GetDriverName`的值作为`lpszDriverName`对的调用中[CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc)。  
  
### <a name="example"></a>示例  
  请参阅示例[CPrintDialog::GetDeviceName](#getdevicename)。  
  
##  <a name="getfrompage"></a>  CPrintDialog::GetFromPage  
 检索打印范围的起始页。  
  
```  
int GetFromPage() const;  
```  
  
### <a name="return-value"></a>返回值  
 起始页码的范围中要打印的页。  
  
### <a name="remarks"></a>备注  
 调用此函数在调用`DoModal`以检索要打印的页范围中的起始页号。  
  
### <a name="example"></a>示例  
  请参阅示例[CPrintDialog::m_pd](#m_pd)。  
  
##  <a name="getportname"></a>  CPrintDialog::GetPortName  
 检索当前所选的打印机端口的名称。  
  
```  
CString GetPortName() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前选定的打印机端口的名称。  
  
### <a name="remarks"></a>备注  
 调用此函数在调用[DoModal](#domodal)或[GetDefaults](#getdefaults)检索当前所选的打印机端口的名称。  
  
### <a name="example"></a>示例  
  请参阅示例[CPrintDialog::GetDeviceName](#getdevicename)。  
  
##  <a name="getprinterdc"></a>  CPrintDialog::GetPrinterDC  
 检索打印机设备上下文的句柄。  
  
```  
HDC GetPrinterDC() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则打印机设备上下文的句柄否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 如果*bPrintSetupOnly*参数`CPrintDialog`构造函数已**FALSE** （指示显示打印对话框中），然后`GetPrinterDC`打印机设备返回的句柄上下文。 必须调用 Windows [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533)可用于完成后删除的设备上下文函数使用它。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#109](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]  
  
##  <a name="gettopage"></a>  CPrintDialog::GetToPage  
 检索打印范围的结束页。  
  
```  
int GetToPage() const;  
```  
  
### <a name="return-value"></a>返回值  
 结束页码的范围中要打印的页数。  
  
### <a name="remarks"></a>备注  
 调用此函数在调用`DoModal`检索结束页范围中要打印的页的次数。  
  
### <a name="example"></a>示例  
  请参阅示例[CPrintDialog::m_pd](#m_pd)。  
  
##  <a name="m_pd"></a>  CPrintDialog::m_pd  
 一个其成员存储对话框对象的特征的结构。  
  
```  
PRINTDLG& m_pd;  
```  
  
### <a name="remarks"></a>备注  
 后构造`CPrintDialog`对象时，可以使用`m_pd`设置对话框之前调用的各个方面[DoModal](#domodal)成员函数。 有关详细信息`m_pd`结构，请参阅[PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843) Windows SDK 中。  
  
 如果你修改`m_pd`数据成员直接，您将重写任何默认行为。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#111](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]  
  
##  <a name="printall"></a>  CPrintDialog::PrintAll  
 确定是否打印文档的所有页面。  
  
```  
BOOL PrintAll() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果在文档中的所有页面都都要打印; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 调用此函数在调用`DoModal`确定是否要打印的文档中的所有页面。  
  
### <a name="example"></a>示例  
  请参阅示例[CPrintDialog::m_pd](#m_pd)。  
  
##  <a name="printcollate"></a>  CPrintDialog::PrintCollate  
 确定是否逐份打印副本请求。  
  
```  
BOOL PrintCollate() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果用户在对话框中; 选择 collate 复选框则不为否则为 0。  
  
### <a name="remarks"></a>备注  
 调用此函数在调用`DoModal`以确定打印机是否应 collate 所有打印的文档副本。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#110](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]  
  
##  <a name="printrange"></a>  CPrintDialog::PrintRange  
 确定是否打印指定的范围的页面。  
  
```  
BOOL PrintRange() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果仅在文档中的页范围是要打印; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 调用此函数在调用`DoModal`来确定是否打印仅范围内的文档中的页面。  
  
### <a name="example"></a>示例  
  请参阅示例[CPrintDialog::m_pd](#m_pd)。  
  
##  <a name="printselection"></a>  CPrintDialog::PrintSelection  
 确定是否打印当前选定的项。  
  
```  
BOOL PrintSelection() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果只有所选的项目是要打印; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 调用此函数在调用`DoModal`来确定是否打印当前选定的项。  
  
### <a name="example"></a>示例  
  请参阅示例[CPrintDialog::m_pd](#m_pd)。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 DIBLOOK](../../visual-cpp-samples.md)   
 [CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CPrintInfo 结构](../../mfc/reference/cprintinfo-structure.md)
