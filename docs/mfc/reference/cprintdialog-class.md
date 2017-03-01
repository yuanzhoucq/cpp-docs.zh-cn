---
title: "CPrintDialog 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPrintDialog
dev_langs:
- C++
helpviewer_keywords:
- Print Setup dialog box
- Print dialog box
- CPrintDialog class
ms.assetid: 5bdb2424-adf8-433d-a97c-df11a83bc4e4
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: fe8b5a899169bf9dfd463278100384fde900a6a0
ms.lasthandoff: 02/24/2017

---
# <a name="cprintdialog-class"></a>CPrintDialog 类
封装由 Windows 公共对话框提供的打印服务。  
  
## <a name="syntax"></a>语法  
  
```  
class CPrintDialog : public CCommonDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CPrintDialog::CPrintDialog](#cprintdialog)|构造 `CPrintDialog` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CPrintDialog::CreatePrinterDC](#createprinterdc)|创建打印机设备上下文而不会显示打印对话框。|  
|[CPrintDialog::DoModal](#domodal)|显示对话框中，并允许用户进行选择。|  
|[CPrintDialog::GetCopies](#getcopies)|检索请求的副本数目。|  
|[CPrintDialog::GetDefaults](#getdefaults)|检索设备默认值而不会显示一个对话框。|  
|[CPrintDialog::GetDeviceName](#getdevicename)|检索当前所选的打印机设备的名称。|  
|[CPrintDialog::GetDevMode](#getdevmode)|检索`DEVMODE`结构。|  
|[CPrintDialog::GetDriverName](#getdrivername)|检索当前所选的打印机驱动程序的名称。|  
|[CPrintDialog::GetFromPage](#getfrompage)|检索的打印范围的起始页。|  
|[CPrintDialog::GetPortName](#getportname)|检索当前所选的打印机端口的名称。|  
|[CPrintDialog::GetPrinterDC](#getprinterdc)|检索打印机设备上下文的句柄。|  
|[CPrintDialog::GetToPage](#gettopage)|检索的打印范围的结束页。|  
|[CPrintDialog::PrintAll](#printall)|确定是否可以打印文档的所有页面。|  
|[CPrintDialog::PrintCollate](#printcollate)|确定是否逐份打印副本，将申请。|  
|[CPrintDialog::PrintRange](#printrange)|确定是否打印指定的范围的页。|  
|[CPrintDialog::PrintSelection](#printselection)|确定是否可以打印当前选定的项。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CPrintDialog::m_pd](#m_pd)|用于自定义的结构`CPrintDialog`对象。|  
  
## <a name="remarks"></a>备注  
 常见打印对话框提供了在与 Windows 标准一致的方式实现打印和打印设置对话框的简单方法。  
  
> [!NOTE]
>  `CPrintDialogEx`类封装由 Windows 2000 打印属性表提供的服务。 有关详细信息请参阅[CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md)概述。  
  
 `CPrintDialog`功能被取代的[CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)，它旨在提供通用对话框中，为同时打印设置和页面设置。  
  
 您可以依赖框架来处理您的应用程序打印过程的许多方面。 在这种情况下，框架会自动显示 Windows 公共对话框进行打印。 您还可以具有打印您的应用程序的框架句柄，但重写您自己的打印对话框常见打印对话框。 有关使用该框架来处理打印任务的详细信息，请参阅文章[打印](../../mfc/printing.md)。  
  
 如果您希望应用程序处理打印而不需要的框架的参与，则可以使用`CPrintDialog`类"按原样"提供，该构造函数也可以派生您自己的对话框类从`CPrintDialog`并编写一个构造函数来满足您的需要。 在任一情况下，这些对话框的行为将类似标准 MFC 对话框类派生因为`CCommonDialog`。  
  
 若要使用`CPrintDialog`对象，请首先创建对象使用`CPrintDialog`构造函数。 一旦构造的对话框中，您可以设置或修改中的任何值[m_pd](#m_pd)结构来初始化对话框的控件的值。 `m_pd`结构属于类型[PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843)。 此结构的详细信息，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如果没有提供您自己句柄`m_pd`为**hDevMode**和**hDevNames**成员，一定要调用 Windows 函数**GlobalFree**的对话框中完成后这些句柄。 在使用所提供的框架的打印设置实现`CWinApp::OnFilePrintSetup`，不需要释放这些句柄。 句柄由维护`CWinApp`并在释放`CWinApp`的析构函数。 它只是用来在使用时释放这些句柄`CPrintDialog`独立。  
  
 初始化后对话框控件，调用`DoModal`成员函数以显示对话框中，并让用户选择打印选项。 `DoModal`返回用户是否选择了确定 ( **IDOK**) 或取消 ( **IDCANCEL**) 按钮。  
  
 如果`DoModal`返回**IDOK**，您可以使用其中一个`CPrintDialog`的成员函数来检索用户输入的信息。  
  
 `CPrintDialog::GetDefaults`成员函数可用于检索当前打印机默认值而不会显示一个对话框。 此成员函数不需要用户交互。  
  
 您可以使用 Windows **CommDlgExtendedError**函数来确定在对话框中的初始化过程中是否发生了错误，以及若要了解有关错误的详细信息。 此函数的详细信息，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `CPrintDialog`依赖于 COMMDLG。随 Windows 3.1 及更高版本一起提供的 DLL 文件。  
  
 要自定义对话框中，从派生类`CPrintDialog`，提供自定义对话框模板上，并添加一个消息映射来处理来自扩展控件的通知消息。 任何未处理的消息应传递到基类上。 不需要自定义挂钩函数。  
  
 若要处理同一消息以不同的方式根据对话框中是否打印或打印设置，必须派生一个类，用于每个对话框。 此外必须重写 Windows **AttachOnSetup**函数，它在打印对话框中选择打印设置按钮时处理新的对话框中的创建。  
  
 有关详细信息使用`CPrintDialog`，请参阅[通用对话框类](../../mfc/common-dialog-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CPrintDialog`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdlgs.h  
  
##  <a name="a-namecprintdialoga--cprintdialogcprintdialog"></a><a name="cprintdialog"></a>CPrintDialog::CPrintDialog  
 构造的 Windows 打印或打印设置对话框对象。  
  
```  
CPrintDialog(
    BOOL bPrintSetupOnly,  
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 `bPrintSetupOnly`  
 指定是否显示标准的 Windows 打印对话框中或打印设置对话框。 此参数设置为**TRUE**以显示标准的 Windows 打印设置对话框。 将其设置为**FALSE**以显示 Windows 打印对话框。 如果`bPrintSetupOnly`是**FALSE**，打印设置选项按钮仍显示在打印对话框中。  
  
 `dwFlags`  
 可以使用自定义设置对话框中，使用按位 OR 运算符组合在一起的一个或多个标志。 例如， **PD_ALLPAGES**标志将默认的打印范围设置为文档的所有页面。 请参阅[PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关这些标志的详细信息。  
  
 `pParentWnd`  
 指向对话框中的父窗口或所有者窗口的指针。  
  
### <a name="remarks"></a>备注  
 此成员函数仅构造对象。 使用`DoModal`成员函数以显示该对话框。  
  
 请注意，当您调用的构造函数与`bPrintSetupOnly`设置为**FALSE**、 **PD_RETURNDC**标志会自动使用。 在调用`DoModal`， `GetDefaults`，或`GetPrinterDC`中, 将返回打印机 DC `m_pd.hDC`。 通过调用，必须释放此 DC [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533)的调用方`CPrintDialog`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&174; 行](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]  
  
##  <a name="a-namecreateprinterdca--cprintdialogcreateprinterdc"></a><a name="createprinterdc"></a>CPrintDialog::CreatePrinterDC  
 从创建打印机设备上下文 (DC) [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)和[DEVNAMES](../../mfc/reference/devnames-structure.md)结构。  
  
```  
HDC CreatePrinterDC();
```  
  
### <a name="return-value"></a>返回值  
 新创建的打印机设备上下文的句柄。  
  
### <a name="remarks"></a>备注  
 该 DC 将假定为当前打印机 DC，和任何其他以前获得的用户必须删除域控制器的打印机。 可以调用此函数，并且生成 DC 使用，而不会过显示打印对话框。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&106;](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]  
  
##  <a name="a-namedomodala--cprintdialogdomodal"></a><a name="domodal"></a>CPrintDialog::DoModal  
 显示 Windows 标准打印对话框中，并允许用户选择各种打印选项，如副本，页范围的数目和副本是否应进行分页。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 **IDOK**或**IDCANCEL**。 如果**IDCANCEL**是返回，调用 Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916)函数来确定是否发生了错误。  
  
 **IDOK**和**IDCANCEL**是常数，指示用户是否选择了确定或取消按钮。  
  
### <a name="remarks"></a>备注  
 如果您想要通过设置的成员初始化的各种打印对话框选项`m_pd`结构中，应执行此操作，然后再调`DoModal`，但在构造对话框对象之后。  
  
 在调用`DoModal`，可调用其他成员函数来检索设置或用户的信息输入到对话框。  
  
 请注意，当您调用的构造函数与`bPrintSetupOnly`设置为**FALSE**、 **PD_RETURNDC**标志会自动使用。 在调用`DoModal`， `GetDefaults`，或`GetPrinterDC`中, 将返回打印机 DC `m_pd.hDC`。 通过调用，必须释放此 DC [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533)的调用方`CPrintDialog`。  
  
### <a name="example"></a>示例  
  请参阅示例[CPrintDialog::CreatePrinterDC](#createprinterdc)。  
  
##  <a name="a-namegetcopiesa--cprintdialoggetcopies"></a><a name="getcopies"></a>CPrintDialog::GetCopies  
 检索请求的副本数目。  
  
```  
int GetCopies() const;  
```  
  
### <a name="return-value"></a>返回值  
 请求的副本数目。  
  
### <a name="remarks"></a>备注  
 在调用后调用此函数`DoModal`来检索请求的副本数目。  
  
### <a name="example"></a>示例  
  请参阅示例[CPrintDialog::PrintCollate](#printcollate)。  
  
##  <a name="a-namegetdefaultsa--cprintdialoggetdefaults"></a><a name="getdefaults"></a>CPrintDialog::GetDefaults  
 检索默认打印机设备默认值而不会显示一个对话框。  
  
```  
BOOL GetDefaults();
```  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 检索到的值被放置在`m_pd`结构。  
  
 在某些情况下，对此函数的调用将调用[构造函数](#cprintdialog)为`CPrintDialog`与`bPrintSetupOnly`设置为**FALSE**。 在这些情况下，打印机 DC 和**hDevNames**和**hDevMode** (两个控点位于`m_pd`数据成员) 会自动分配。  
  
 如果的构造函数`CPrintDialog`调用时使用的`bPrintSetupOnly`设置为**FALSE**，此函数不会只返回**hDevNames**和**hDevMode** (位于**m_pd.hDevNames**和**m_pd.hDevMode**) 到调用方，但也返回中的打印机 DC **m_pd.hDC**。 若要删除打印机 DC 并调用 Windows 的调用方负责[GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579)函数在完成时的句柄`CPrintDialog`对象。  
  
### <a name="example"></a>示例  
 此代码片段获取默认打印机设备上下文，并向用户报告以每英寸点数打印机分辨率。 （此属性的打印机的功能通常称为 DPI。）  
  
 [!code-cpp[NVC_MFCDocView #&107; 页](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]  
  
##  <a name="a-namegetdevicenamea--cprintdialoggetdevicename"></a><a name="getdevicename"></a>CPrintDialog::GetDeviceName  
 检索当前所选的打印机设备的名称。  
  
```  
CString GetDeviceName() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前所选打印机的名称。  
  
### <a name="remarks"></a>备注  
 在调用后调用此函数[DoModal](#domodal)要检索其名称在当前所选打印机或之后调用[GetDefaults](#getdefaults)来检索当前设备的默认打印机的默认值。 使用指向指针`CString`舱ン`GetDeviceName`的值作为`lpszDeviceName`对的调用中[CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc)。  
  
### <a name="example"></a>示例  
 此代码片段演示用户的默认打印机名称和连接，以及后台处理程序名称打印机使用的端口。 该代码可能会显示一个消息框，指出:"默认打印机上为 HP LaserJet IIIP \\\server\share 使用 winspool。"，例如。  
  
 [!code-cpp[NVC_MFCDocView #&108;](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]  
  
##  <a name="a-namegetdevmodea--cprintdialoggetdevmode"></a><a name="getdevmode"></a>CPrintDialog::GetDevMode  
 检索`DEVMODE`结构。  
  
```  
LPDEVMODE GetDevMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)数据结构，其中包含有关设备初始化和打印驱动程序的环境的信息。 您必须解除锁定此结构与 Windows 所占用的内存[GlobalUnlock](http://msdn.microsoft.com/library/windows/desktop/aa366595)函数中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 在调用后调用此函数[DoModal](#domodal)或[GetDefaults](#getdefaults)来检索有关打印设备的信息。  
  
### <a name="example"></a>示例  
  请参阅示例[CPrintDialog::PrintCollate](#printcollate)。  
  
##  <a name="a-namegetdrivernamea--cprintdialoggetdrivername"></a><a name="getdrivername"></a>CPrintDialog::GetDriverName  
 检索当前所选的打印机驱动程序的名称。  
  
```  
CString GetDriverName() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个`CString`指定系统定义的驱动程序的名称。  
  
### <a name="remarks"></a>备注  
 在调用后调用此函数[DoModal](#domodal)或[GetDefaults](#getdefaults)检索系统定义的打印机设备驱动程序的名称。 使用指向指针`CString`舱ン`GetDriverName`的值作为`lpszDriverName`对的调用中[CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc)。  
  
### <a name="example"></a>示例  
  请参阅示例[CPrintDialog::GetDeviceName](#getdevicename)。  
  
##  <a name="a-namegetfrompagea--cprintdialoggetfrompage"></a><a name="getfrompage"></a>CPrintDialog::GetFromPage  
 检索的打印范围的起始页。  
  
```  
int GetFromPage() const;  
```  
  
### <a name="return-value"></a>返回值  
 起始页号范围中要打印的页数。  
  
### <a name="remarks"></a>备注  
 在调用后调用此函数`DoModal`来检索要打印的页范围中的起始页号。  
  
### <a name="example"></a>示例  
  请参阅示例[CPrintDialog::m_pd](#m_pd)。  
  
##  <a name="a-namegetportnamea--cprintdialoggetportname"></a><a name="getportname"></a>CPrintDialog::GetPortName  
 检索当前所选的打印机端口的名称。  
  
```  
CString GetPortName() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前所选的打印机端口的名称。  
  
### <a name="remarks"></a>备注  
 在调用后调用此函数[DoModal](#domodal)或[GetDefaults](#getdefaults)来检索当前所选的打印机端口的名称。  
  
### <a name="example"></a>示例  
  请参阅示例[CPrintDialog::GetDeviceName](#getdevicename)。  
  
##  <a name="a-namegetprinterdca--cprintdialoggetprinterdc"></a><a name="getprinterdc"></a>CPrintDialog::GetPrinterDC  
 检索打印机设备上下文的句柄。  
  
```  
HDC GetPrinterDC() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则打印机设备上下文的句柄否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 如果`bPrintSetupOnly`参数`CPrintDialog`构造函数是**FALSE** （指示将显示打印对话框中），然后`GetPrinterDC`打印机设备上下文中返回的句柄。 必须调用 Windows [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533)函数完成后删除的设备上下文使用它。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&109;](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]  
  
##  <a name="a-namegettopagea--cprintdialoggettopage"></a><a name="gettopage"></a>CPrintDialog::GetToPage  
 检索的打印范围的结束页。  
  
```  
int GetToPage() const;  
```  
  
### <a name="return-value"></a>返回值  
 结束页码范围中要打印的页数。  
  
### <a name="remarks"></a>备注  
 在调用后调用此函数`DoModal`来检索要打印的页范围中结束的页号。  
  
### <a name="example"></a>示例  
  请参阅示例[CPrintDialog::m_pd](#m_pd)。  
  
##  <a name="a-namempda--cprintdialogmpd"></a><a name="m_pd"></a>CPrintDialog::m_pd  
 一种结构，其成员存储对话框对象的特征。  
  
```  
PRINTDLG& m_pd;  
```  
  
### <a name="remarks"></a>备注  
 在构造之后`CPrintDialog`对象，可以使用`m_pd`设置之前，先调用对话框中的各个方面[DoModal](#domodal)成员函数。 有关详细信息`m_pd`结构，请参阅[PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如果您修改`m_pd`数据成员，直接将覆盖任何默认行为。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&111;](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]  
  
##  <a name="a-nameprintalla--cprintdialogprintall"></a><a name="printall"></a>CPrintDialog::PrintAll  
 确定是否可以打印文档的所有页面。  
  
```  
BOOL PrintAll() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果在文档中的所有页面都都要打印; 则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 在调用后调用此函数`DoModal`来确定是否打印在文档中的所有页面。  
  
### <a name="example"></a>示例  
  请参阅示例[CPrintDialog::m_pd](#m_pd)。  
  
##  <a name="a-nameprintcollatea--cprintdialogprintcollate"></a><a name="printcollate"></a>CPrintDialog::PrintCollate  
 确定是否逐份打印副本，将申请。  
  
```  
BOOL PrintCollate() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果用户在对话框中，选择逐份打印复选框，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 在调用后调用此函数`DoModal`来确定打印机是否应逐份打印文档的所有打印的副本。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&110;](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]  
  
##  <a name="a-nameprintrangea--cprintdialogprintrange"></a><a name="printrange"></a>CPrintDialog::PrintRange  
 确定是否打印指定的范围的页。  
  
```  
BOOL PrintRange() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果只有一定范围的文档中的页面的打印;否则为 0。  
  
### <a name="remarks"></a>备注  
 在调用后调用此函数`DoModal`来确定是否仅打印范围的文档中的页面。  
  
### <a name="example"></a>示例  
  请参阅示例[CPrintDialog::m_pd](#m_pd)。  
  
##  <a name="a-nameprintselectiona--cprintdialogprintselection"></a><a name="printselection"></a>CPrintDialog::PrintSelection  
 确定是否可以打印当前选定的项。  
  
```  
BOOL PrintSelection() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果只有所选的项目要打印;否则为 0。  
  
### <a name="remarks"></a>备注  
 在调用后调用此函数`DoModal`来确定是否可以打印当前选定的项。  
  
### <a name="example"></a>示例  
  请参阅示例[CPrintDialog::m_pd](#m_pd)。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 DIBLOOK](../../visual-cpp-samples.md)   
 [CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CPrintInfo 结构](../../mfc/reference/cprintinfo-structure.md)

