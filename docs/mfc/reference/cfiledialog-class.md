---
title: "CFileDialog 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFileDialog
- AFXDLGS/CFileDialog
- AFXDLGS/CFileDialog::CFileDialog
- AFXDLGS/CFileDialog::AddCheckButton
- AFXDLGS/CFileDialog::AddComboBox
- AFXDLGS/CFileDialog::AddControlItem
- AFXDLGS/CFileDialog::AddEditBox
- AFXDLGS/CFileDialog::AddMenu
- AFXDLGS/CFileDialog::AddPlace
- AFXDLGS/CFileDialog::AddPushButton
- AFXDLGS/CFileDialog::AddRadioButtonList
- AFXDLGS/CFileDialog::AddSeparator
- AFXDLGS/CFileDialog::AddText
- AFXDLGS/CFileDialog::ApplyOFNToShellDialog
- AFXDLGS/CFileDialog::DoModal
- AFXDLGS/CFileDialog::EnableOpenDropDown
- AFXDLGS/CFileDialog::EndVisualGroup
- AFXDLGS/CFileDialog::GetCheckButtonState
- AFXDLGS/CFileDialog::GetControlItemState
- AFXDLGS/CFileDialog::GetControlState
- AFXDLGS/CFileDialog::GetEditBoxText
- AFXDLGS/CFileDialog::GetFileExt
- AFXDLGS/CFileDialog::GetFileName
- AFXDLGS/CFileDialog::GetFileTitle
- AFXDLGS/CFileDialog::GetFolderPath
- AFXDLGS/CFileDialog::GetIFileDialogCustomize
- AFXDLGS/CFileDialog::GetIFileOpenDialog
- AFXDLGS/CFileDialog::GetIFileSaveDialog
- AFXDLGS/CFileDialog::GetNextPathName
- AFXDLGS/CFileDialog::GetOFN
- AFXDLGS/CFileDialog::GetPathName
- AFXDLGS/CFileDialog::GetReadOnlyPref
- AFXDLGS/CFileDialog::GetResult
- AFXDLGS/CFileDialog::GetResults
- AFXDLGS/CFileDialog::GetSelectedControlItem
- AFXDLGS/CFileDialog::GetStartPosition
- AFXDLGS/CFileDialog::HideControl
- AFXDLGS/CFileDialog::IsPickFoldersMode
- AFXDLGS/CFileDialog::MakeProminent
- AFXDLGS/CFileDialog::RemoveControlItem
- AFXDLGS/CFileDialog::SetCheckButtonState
- AFXDLGS/CFileDialog::SetControlItemState
- AFXDLGS/CFileDialog::SetControlItemText
- AFXDLGS/CFileDialog::SetControlLabel
- AFXDLGS/CFileDialog::SetControlState
- AFXDLGS/CFileDialog::SetControlText
- AFXDLGS/CFileDialog::SetDefExt
- AFXDLGS/CFileDialog::SetEditBoxText
- AFXDLGS/CFileDialog::SetProperties
- AFXDLGS/CFileDialog::SetSelectedControlItem
- AFXDLGS/CFileDialog::SetTemplate
- AFXDLGS/CFileDialog::StartVisualGroup
- AFXDLGS/CFileDialog::UpdateOFNFromShellDialog
- AFXDLGS/CFileDialog::OnButtonClicked
- AFXDLGS/CFileDialog::OnCheckButtonToggled
- AFXDLGS/CFileDialog::OnControlActivating
- AFXDLGS/CFileDialog::OnFileNameChange
- AFXDLGS/CFileDialog::OnFileNameOK
- AFXDLGS/CFileDialog::OnFolderChange
- AFXDLGS/CFileDialog::OnInitDone
- AFXDLGS/CFileDialog::OnItemSelected
- AFXDLGS/CFileDialog::OnLBSelChangedNotify
- AFXDLGS/CFileDialog::OnShareViolation
- AFXDLGS/CFileDialog::OnTypeChange
- AFXDLGS/CFileDialog::m_ofn
dev_langs: C++
helpviewer_keywords:
- CFileDialog [MFC], CFileDialog
- CFileDialog [MFC], AddCheckButton
- CFileDialog [MFC], AddComboBox
- CFileDialog [MFC], AddControlItem
- CFileDialog [MFC], AddEditBox
- CFileDialog [MFC], AddMenu
- CFileDialog [MFC], AddPlace
- CFileDialog [MFC], AddPushButton
- CFileDialog [MFC], AddRadioButtonList
- CFileDialog [MFC], AddSeparator
- CFileDialog [MFC], AddText
- CFileDialog [MFC], ApplyOFNToShellDialog
- CFileDialog [MFC], DoModal
- CFileDialog [MFC], EnableOpenDropDown
- CFileDialog [MFC], EndVisualGroup
- CFileDialog [MFC], GetCheckButtonState
- CFileDialog [MFC], GetControlItemState
- CFileDialog [MFC], GetControlState
- CFileDialog [MFC], GetEditBoxText
- CFileDialog [MFC], GetFileExt
- CFileDialog [MFC], GetFileName
- CFileDialog [MFC], GetFileTitle
- CFileDialog [MFC], GetFolderPath
- CFileDialog [MFC], GetIFileDialogCustomize
- CFileDialog [MFC], GetIFileOpenDialog
- CFileDialog [MFC], GetIFileSaveDialog
- CFileDialog [MFC], GetNextPathName
- CFileDialog [MFC], GetOFN
- CFileDialog [MFC], GetPathName
- CFileDialog [MFC], GetReadOnlyPref
- CFileDialog [MFC], GetResult
- CFileDialog [MFC], GetResults
- CFileDialog [MFC], GetSelectedControlItem
- CFileDialog [MFC], GetStartPosition
- CFileDialog [MFC], HideControl
- CFileDialog [MFC], IsPickFoldersMode
- CFileDialog [MFC], MakeProminent
- CFileDialog [MFC], RemoveControlItem
- CFileDialog [MFC], SetCheckButtonState
- CFileDialog [MFC], SetControlItemState
- CFileDialog [MFC], SetControlItemText
- CFileDialog [MFC], SetControlLabel
- CFileDialog [MFC], SetControlState
- CFileDialog [MFC], SetControlText
- CFileDialog [MFC], SetDefExt
- CFileDialog [MFC], SetEditBoxText
- CFileDialog [MFC], SetProperties
- CFileDialog [MFC], SetSelectedControlItem
- CFileDialog [MFC], SetTemplate
- CFileDialog [MFC], StartVisualGroup
- CFileDialog [MFC], UpdateOFNFromShellDialog
- CFileDialog [MFC], OnButtonClicked
- CFileDialog [MFC], OnCheckButtonToggled
- CFileDialog [MFC], OnControlActivating
- CFileDialog [MFC], OnFileNameChange
- CFileDialog [MFC], OnFileNameOK
- CFileDialog [MFC], OnFolderChange
- CFileDialog [MFC], OnInitDone
- CFileDialog [MFC], OnItemSelected
- CFileDialog [MFC], OnLBSelChangedNotify
- CFileDialog [MFC], OnShareViolation
- CFileDialog [MFC], OnTypeChange
- CFileDialog [MFC], m_ofn
ms.assetid: fda4fd3c-08b8-4ce0-8e9d-7bab23f8c6c0
caps.latest.revision: "47"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2dead08eaeb525e626e9c1f02af346b0c3998260
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cfiledialog-class"></a>CFileDialog 类
封装用于文件打开或保存操作的文件的公共对话框。  
  
## <a name="syntax"></a>语法  
  
```  
class CFileDialog : public CCommonDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CFileDialog::CFileDialog](#cfiledialog)|构造 `CFileDialog` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CFileDialog::AddCheckButton](#addcheckbutton)|向对话框添加复选按钮。|  
|[CFileDialog::AddComboBox](#addcombobox)|将组合框添加到对话框。|  
|[CFileDialog::AddControlItem](#addcontrolitem)|将项添加到对话框中的容器控件。|  
|[CFileDialog::AddEditBox](#addeditbox)|向对话框添加编辑框。|  
|[CFileDialog::AddMenu](#addmenu)|将菜单添加到对话框。|  
|[CFileDialog::AddPlace](#addplace)|已重载。 将添加到列表中的文件夹将放置可供用户打开或保存项。|  
|[CFileDialog::AddPushButton](#addpushbutton)|向对话框添加一个按钮。|  
|[CFileDialog::AddRadioButtonList](#addradiobuttonlist)|将某一选项按钮 （也称为单选按钮） 组添加到对话框。|  
|[CFileDialog::AddSeparator](#addseparator)|向对话框添加分隔符。|  
|[CFileDialog::AddText](#addtext)|将文本内容添加到对话框。|  
|[CFileDialog::ApplyOFNToShellDialog](#applyofntoshelldialog)|更新的状态`CFileDialog`以匹配的参数和标志中存储`m_ofn`成员变量。|  
|[CFileDialog::DoModal](#domodal)|显示对话框中，并使用户能够进行选择。|  
|[CFileDialog::EnableOpenDropDown](#enableopendropdown)|在上启用下拉列表**打开**或**保存**在对话框中的按钮。|  
|[CFileDialog::EndVisualGroup](#endvisualgroup)|停止添加到对话框中的 visual 组的元素。|  
|[CFileDialog::GetCheckButtonState](#getcheckbuttonstate)|获取对话框中的复选按钮 （复选框） 的当前状态。|  
|[CFileDialog::GetControlItemState](#getcontrolitemstate)|获取在对话框中找到的容器控件中的项的当前状态。|  
|[CFileDialog::GetControlState](#getcontrolstate)|获取当前的可见性，并已启用的某一给定控件的状态。|  
|[CFileDialog::GetEditBoxText](#geteditboxtext)|在编辑框控件中获取当前的文本。|  
|[CFileDialog::GetFileExt](#getfileext)|返回所选文件的扩展名。|  
|[CFileDialog::GetFileName](#getfilename)|返回所选文件的文件名称。|  
|[CFileDialog::GetFileTitle](#getfiletitle)|返回所选文件的标题。|  
|[CFileDialog::GetFolderPath](#getfolderpath)|检索当前打开的文件夹或目录的路径为资源管理器样式**打开**或**另存为**通用对话框。|  
|[CFileDialog::GetIFileDialogCustomize](#getifiledialogcustomize)|检索自定义的内部 COM 对象`CFileDialog`对象。|  
|[CFileDialog::GetIFileOpenDialog](#getifileopendialog)|检索的内部 COM 对象`CFileDialog`用作**打开**文件对话框。|  
|[CFileDialog::GetIFileSaveDialog](#getifilesavedialog)|检索的内部 COM 对象`CFileDialog`用作**保存**文件对话框。|  
|[CFileDialog::GetNextPathName](#getnextpathname)|返回下一步所选文件的完整路径。|  
|[CFileDialog::GetOFN](#getofn)|检索`OPENFILENAME`结构`CFileDialog`对象。|  
|[CFileDialog::GetPathName](#getpathname)|返回所选文件的完整路径。|  
|[CFileDialog::GetReadOnlyPref](#getreadonlypref)|返回所选文件的只读状态。|  
|[CFileDialog::GetResult](#getresult)|获取用户在对话框中所做的选择。|  
|[CFileDialog::GetResults](#getresults)|在一个对话框，允许多个所选内容中获取用户的选项。|  
|[CFileDialog::GetSelectedControlItem](#getselectedcontrolitem)|从对话框中的指定的容器控件中获取的特定项。|  
|[CFileDialog::GetStartPosition](#getstartposition)|返回的文件名称列表的第一个元素的位置。|  
|[CFileDialog::HideControl](#hidecontrol)|隐藏指定的控件中的资源管理器样式**打开**或**另存为**通用对话框。|  
|[CFileDialog::IsPickFoldersMode](#ispickfoldersmode)|确定当前对话框文件夹选取器模式下的。|  
|[CFileDialog::MakeProminent](#makeprominent)|位置对话框中的控件，以便它醒目相比其他添加控件。|  
|[CFileDialog::RemoveControlItem](#removecontrolitem)|在对话框的容器控件中移除的项。|  
|[CFileDialog::SetCheckButtonState](#setcheckbuttonstate)|在对话框中设置勾选按钮 （复选框） 的当前的状态。|  
|[CFileDialog::SetControlItemState](#setcontrolitemstate)|在对话框中找到的容器控件中设置项的当前的状态。|  
|[CFileDialog::SetControlItemText](#setcontrolitemtext)|设置控件项的文本。 例如，附带一个单选按钮或菜单中的项的文本。|  
|[CFileDialog::SetControlLabel](#setcontrollabel)|设置与控件，如按钮文本或编辑框标签关联的文本。|  
|[CFileDialog::SetControlState](#setcontrolstate)|设置当前的可见性和已启用的某一给定控件的状态。|  
|[CFileDialog::SetControlText](#setcontroltext)|资源管理器样式设置为指定的控件的文本**打开**或**另存为**通用对话框。|  
|[CFileDialog::SetDefExt](#setdefext)|设置资源管理器样式的默认文件扩展名**打开**或**另存为**通用对话框。|  
|[CFileDialog::SetEditBoxText](#seteditboxtext)|在编辑框控件中设置的当前文本。|  
|[CFileDialog::SetProperties](#setproperties)|提供一个属性存储，它定义将默认值用于正在保存的项。|  
|[CFileDialog::SetSelectedControlItem](#setselectedcontrolitem)|中的选项按钮组或在对话框中找到一个组合框设置特定项的选定的状态。|  
|[CFileDialog::SetTemplate](#settemplate)|设置为对话框模板`CFileDialog`对象。|  
|[CFileDialog::StartVisualGroup](#startvisualgroup)|声明对话框中的 visual 组。 对任何"add"方法的后续调用将这些元素添加到此组。|  
|[CFileDialog::UpdateOFNFromShellDialog](#updateofnfromshelldialog)|更新中存储的数据`m_ofn`成员变量，以匹配的文件对话框中的当前状态。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CFileDialog::OnButtonClicked](#onbuttonclicked)|单击该按钮时调用。|  
|[CFileDialog::OnCheckButtonToggled](#oncheckbuttontoggled)|当未选中/选中复选框时调用。|  
|[CFileDialog::OnControlActivating](#oncontrolactivating)|当控件处于活动状态时调用。|  
|[CFileDialog::OnFileNameChange](#onfilenamechange)|处理`WM_NOTIFY CDN_SELCHANGE`消息。|  
|[CFileDialog::OnFileNameOK](#onfilenameok)|验证在对话框中输入的文件名称。|  
|[CFileDialog::OnFolderChange](#onfolderchange)|处理`WM_NOTIFY CDN_FOLDERCHANGE`消息。|  
|[CFileDialog::OnInitDone](#oninitdone)|处理`WM_NOTIFY CDN_INITDONE`消息。|  
|[CFileDialog::OnItemSelected](#onitemselected)|当要选择容器项时调用。|  
|[CFileDialog::OnLBSelChangedNotify](#onlbselchangednotify)|允许你在文件选择更改时执行自定义操作。|  
|[CFileDialog::OnShareViolation](#onshareviolation)|句柄共享冲突。|  
|[CFileDialog::OnTypeChange](#ontypechange)|处理`WM_NOTIFY CDN_TYPECHANGE`消息。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CFileDialog::m_ofn](#m_ofn)|Windows`OPENFILENAME`结构。 提供对基本文件对话框的参数访问。|  
  
## <a name="remarks"></a>备注  
 通用文件对话框使你可以实现文件选择对话框中，例如，**打开的文件**和**另存为**，与 Windows 标准一致的方式。  
  
 你可以使用`CFileDialog`按原样提供，构造函数，或可以派生从你自己对话框类`CFileDialog`和写入以满足你需求的构造函数。 在任一情况下，这些对话框将行为类似于标准 MFC 对话框因为它们都派生自[CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)。 `CFileDialog`依赖于 COMMDLG。Windows 中包含的 DLL 文件。  
  
 外观和功能`CFileDialog`与[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]与不同，早期版本的 Windows。 默认值`CFileDialog`自动使用新[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]不如果编译程序时的代码更改和运行带样式[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。 使用`bVistaStyle`构造函数来手动重写此自动更新中的参数。 自动更新的例外是自定义的对话框。 它们将不能转换为的新样式。 有关构造函数的详细信息，请参阅[CFileDialog::CFileDialog](#cfiledialog)。  
  
> [!NOTE]
>  在不同的控件 ID 系统[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]从早期版本的 Windows 使用时`CFileDialog`。 你必须更新所有引用`CFileDialog`代码之前可以移植你的项目从早期版本的 Windows 中的控件。  
  
 某些`CFileDialog`下不支持的方法[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。 检查是否支持该方法的信息的单个方法主题。 此外，在不支持以下继承的函数[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]:  
  
- [CDialog::OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog)  
  
- [CDialog::OnSetFont](../../mfc/reference/cdialog-class.md#onsetfont)  
  
 Windows 消息的`CFileDialog`类取决于你使用的操作系统。 例如，Windows XP 不支持[CDialog::OnCancel](../../mfc/reference/cdialog-class.md#oncancel)和[CDialog::OnOK](../../mfc/reference/cdialog-class.md#onok)为`CFileDialog`类。 但是，[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]支持它们。 有关生成的不同消息和接收它们的顺序的详细信息，请参阅[CFileDialog 示例： 日志记录事件的顺序](../../visual-cpp-samples.md)。  
  
 若要使用`CFileDialog`对象，请首先通过使用创建该对象`CFileDialog`构造函数。 在构造对话框后，你可以设置或修改中的任何值[CFileDialog::m_ofn](#m_ofn)结构初始化的值或对话框控件的状态。 `m_ofn`结构属于类型`OPENFILENAME`。 有关详细信息，请参阅[OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839) Windows SDK 中的结构。  
  
 初始化对话框控件后，调用[CFileDialog::DoModal](#domodal)方法以显示对话框框中，以便用户可以键入的路径和文件名称。 `DoModal`返回用户单击确定 (IDOK) 或取消 (IDCANCEL) 按钮。 如果`DoModal`返回 IDOK，你可以使用之一`CFileDialog`公共成员函数来检索该信息将由用户。  
  
> [!NOTE]
>  下[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]，多次调用[IFileDialog::SetFileTypes](http://msdn.microsoft.com/library/windows/desktop/bb775980)会导致错误。 第二次调用`SetFileTypes`的所有实例`CFileDialog`将返回`E_UNEXPECTED`中[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。 某些`CFileDialog`方法函数都调用`SetFileTypes`。 例如，有两个调用到`CFileDialog::DoModal`为同一实例的`CFileDialog`生成[断言](diagnostic-services.md#assert)。  
  
 `CFileDialog`包括让你进行操作的共享冲突、 文件名称验证和列表框中更改通知的自定义处理的多个受保护的成员。 这些受保护的成员都是大多数应用程序无需使用，因为默认处理会自动执行的回调函数。 这些函数的消息映射条目不是必需的因为它们是标准的虚拟函数。  
  
 你可以使用 Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916)函数可确定在对话框中的初始化过程中是否发生了错误并了解有关错误的详细信息。  
  
 析构`CFileDialog`自动处理对象。 无需调用[CDialog::EndDialog](../../mfc/reference/cdialog-class.md#enddialog)。  
  
 若要让用户选择多个文件，将设置`OFN_ALLOWMULTISELECT`标志你在调用之前`DoModal`。 必须提供您自己的文件名称缓冲区，以便容纳返回的多个文件名称的列表。 执行此操作通过替换`m_ofn.lpstrFile`指向缓冲区的指针与你已分配之后你构造, `CFileDialog`，但你在调用之前`DoModal`。  
  
 此外，必须设置`m_ofn.nMaxFile`指向的缓冲区中使用的字符数`m_ofn.lpstrFile`。 如果设置到选定文件的最大数目`n`，所需的缓冲区大小是`n * (_MAX_PATH + 1) + 1`。 返回在缓冲区中的第一项是选择文件，其中的文件夹的路径。 有关[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]-样式对话框框中，目录和文件名称字符串是以 null 终止的与一个额外的 null 字符后的最后一个文件名。 这种格式使资源管理器样式对话框以返回包含空格的长文件名。 对于旧式对话框框中，由空格分隔目录和文件名称字符串和该函数使用空间使用的文件名称的短文件名。  
  
 下面的示例演示如何使用一个缓冲区来检索并列出多个文件的名称。  
  
 [!code-cpp[NVC_MFCFiles#23](../../atl-mfc-shared/reference/codesnippet/cpp/cfiledialog-class_1.cpp)]  
  
 若要更改以响应用户选择多个文件名的缓冲区大小，必须派生新类从`CFileDialog`，并重写[CFileDialog::OnFileNameChange](#onfilenamechange)方法。  
  
 如果派生新类从`CFileDialog`，你可以使用消息映射处理任何消息。 若要扩展的默认消息处理，从派生类`CFileDialog`，将消息映射添加到新的类中，并为新的消息提供成员函数。 无需提供挂钩函数，以自定义的对话框。  
  
 要自定义对话框中，从派生类`CFileDialog`，提供自定义对话框模板，并添加一个消息映射来处理来自扩展控件的通知消息。 将任何未处理的消息传递到类的基类。 不需要自定义挂钩函数。  
  
 如果要使用[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]样式`CFileDialog`，不能使用消息映射和对话框模板。 相反，你必须使用 COM 接口的类似的功能。  
  
 有关如何使用`CFileDialog`，请参阅[通用对话框类](../../mfc/common-dialog-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CFileDialog`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdlgs.h  
  
##  <a name="addcheckbutton"></a>CFileDialog::AddCheckButton  
 向对话框添加复选按钮。  
  
```  
HRESULT AddCheckButton(
    DWORD dwIDCtl,  
    const CString& strLabel,  
    BOOL bChecked);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 要添加检查按钮的 ID。  
  
 `strLabel`  
 检查按钮名称。  
  
 `bChecked`  
 一个布尔值，指示检查按钮的当前状态。 `TRUE`如果选中;`FALSE`否则为  
  
### <a name="remarks"></a>备注  
  
##  <a name="addcombobox"></a>CFileDialog::AddComboBox  
 将组合框添加到对话框。  
  
```  
HRESULT AddComboBox(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 要添加的组合框的 ID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="addcontrolitem"></a>CFileDialog::AddControlItem  
 将项添加到对话框中的容器控件。  
  
```  
HRESULT AddControlItem(
    DWORD dwIDCtl,  
    DWORD dwIDItem,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 要向其中添加项的容器控件的 ID。  
  
 `dwIDItem`  
 项的 ID。  
  
 `strLabel`  
 项的文本。  
  
### <a name="remarks"></a>备注  
  
##  <a name="addeditbox"></a>CFileDialog::AddEditBox  
 向对话框添加编辑框。  
  
```  
HRESULT AddEditBox(
    DWORD dwIDCtl,  
    const CString& strText);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 要添加编辑框的 ID。  
  
 `strText`  
 编辑框名称。  
  
### <a name="remarks"></a>备注  
  
##  <a name="addmenu"></a>CFileDialog::AddMenu  
 将菜单添加到对话框。  
  
```  
HRESULT AddMenu(
    DWORD dwIDCtl,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 要添加的菜单的 ID。  
  
 `strLabel`  
 菜单名称中。  
  
### <a name="remarks"></a>备注  
  
##  <a name="addplace"></a>CFileDialog::AddPlace  
 将添加到列表中的文件夹将放置可供用户打开或保存项。  
  
```  
void AddPlace(
    LPCWSTR lpszFolder,  
    FDAP fdap = FDAP_TOP) throw();

 
void AddPlace(
    IShellItem* psi,  
    FDAP fdap = FDAP_TOP) throw();
```  
  
### <a name="parameters"></a>参数  
 `lpszFolder`  
 若要将提供给用户文件夹的路径。 这只能是一个文件夹。  
  
 `fdap`  
 指定的文件夹列表中的放置位置。  
  
 `psi`  
 表示要将提供给用户的文件夹 IShellItem 指向的指针。 这只能是一个文件夹。  
  
### <a name="remarks"></a>备注  
  
##  <a name="addpushbutton"></a>CFileDialog::AddPushButton  
 向对话框添加一个按钮。  
  
```  
HRESULT AddPushButton(
    DWORD dwIDCtl,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 要添加按钮的 ID。  
  
 `strLabel`  
 按钮名称中。  
  
### <a name="remarks"></a>备注  
  
##  <a name="addradiobuttonlist"></a>CFileDialog::AddRadioButtonList  
 将某一选项按钮 （也称为单选按钮） 组添加到对话框。  
  
```  
HRESULT AddRadioButtonList(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 要添加的选项按钮组的 ID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="addseparator"></a>CFileDialog::AddSeparator  
 向对话框添加分隔符。  
  
```  
HRESULT AddSeparator(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 添加分隔符的 ID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="addtext"></a>CFileDialog::AddText  
 将文本添加到对话框。  
  
```  
HRESULT AddText(
    DWORD dwIDCtl,  
    const CString& strText);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 要添加文本的 ID。  
  
 `strText`  
 文本名称中。  
  
### <a name="remarks"></a>备注  
  
##  <a name="applyofntoshelldialog"></a>CFileDialog::ApplyOFNToShellDialog  
 更新的当前状态[CFileDialog](../../mfc/reference/cfiledialog-class.md)基于中存储的值`m_ofn`数据结构。  
  
```  
void ApplyOFNToShellDialog();
```  
  
### <a name="remarks"></a>备注  
 在之前的 Windows 版本中[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]，成员[OPENFILENAME](https://msdn.microsoft.com/library/ms911906.aspx)持续的状态同步数据结构`CFileDialog`。 对任何更改[m_ofn](#m_ofn)成员变量都立即反映在对话框中的状态。 此外，对对话框中的状态的任何更改立即更新`m_ofn`成员变量。  
  
 在[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]中的值`m_ofn`成员变量和状态的`CFileDialog`不保证进行同步。 此函数强制的状态`CFileDialog`要更新以匹配`m_ofn`结构。 Windows 会调用此函数过程中自动[CFileDialog::DoModal](#domodal)。  
  
 有关如何使用`CFileDialog`类下[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]，请参阅[CFileDialog 类](../../mfc/reference/cfiledialog-class.md)。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileDialog::UpdateOFNFromShellDialog](#updateofnfromshelldialog)。  
  
##  <a name="cfiledialog"></a>CFileDialog::CFileDialog  
 调用此函数可构造标准的 Windows 文件对话框。  
  
```  
explicit CFileDialog(
    BOOL bOpenFileDialog,  
    LPCTSTR lpszDefExt = NULL,  
    LPCTSTR lpszFileName = NULL,  
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT,  
    LPCTSTR lpszFilter = NULL,  
    CWnd* pParentWnd = NULL,  
    DWORD dwSize = 0,  
    BOOL bVistaStyle = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bOpenFileDialog`  
 指定哪种类型的对话框中，若要创建参数。 将其设置为`TRUE`构造**文件打开**对话框。 将其设置为`FALSE`构造**文件另存为**对话框。  
  
 [in] `lpszDefExt`  
 默认的文件扩展名。 如果用户不在文件名中包括的已知的扩展 （一个用户的计算机上具有关联），指定的扩展`lpszDefExt`自动追加到的文件名称。 如果此参数为`NULL`，追加无扩展名。  
  
 [in] `lpszFileName`  
 在文件名框中显示的初始文件名称。 如果`NULL`，没有初始文件名称出现。  
  
 [in] `dwFlags`  
 可用于自定义对话框中的一个或多个标志的组合。 有关这些标志的说明，请参阅[OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839) Windows SDK 中的结构。 如果你修改`m_ofn.Flags`结构成员，请使用所做的更改中的按位 OR 运算符以保持不变的默认行为。  
  
 [in] `lpszFilter`  
 指定筛选器的字符串对一系列你可以应用于文件。 如果指定文件筛选器，只有与筛选条件匹配的文件将出现在文件列表中。 请参阅有关如何使用文件筛选器的详细信息备注部分。  
  
 [in] `pParentWnd`  
 指向文件对话框中的父或所有者窗口的指针。  
  
 [in] `dwSize`  
 大小`OPENFILENAME`结构。 此值取决于操作系统版本。 MFC 使用此参数来确定对话框中，若要创建的相应类型 (例如，新[!INCLUDE[Win2kFamily](../../c-runtime-library/includes/win2kfamily_md.md)]对话框而不是 NT4 对话框)。 MFC 代码将确定要使用的正确对话框框大小的 0 表示的默认大小基于在其运行该程序的操作系统版本。  
  
 [in] `bVistaStyle`  
 **请注意**此参数是可在 Visual Studio 2008 及更高版本，将导致新样式对话框中，仅当正在运行供[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]或更高版本。  
  
 参数，指定文件对话框的样式。 将其设置为`TRUE`以使用新的 Vista 样式文件对话框。 否则，将使用旧样式的对话框。 请参阅备注部分的详细信息在 Vista 下运行。  
  
### <a name="remarks"></a>备注  
 任一**文件打开**或**文件另存为**对话框时构造，具体取决于值`bOpenFileDialog`。  
  
 指定默认扩展使用`lpszDefExt`可能生成你预期的行为，因为它很少成为可预测有哪些扩展在用户的计算机上具有文件关联。 如果你需要更好地控制追加的默认扩展插件，可以派生您自己的类从`CFileDialog`，并重写`CFileDialog::OnFileNameOK`方法来执行您自己的扩展处理。  
  
 若要使用户能够选择多个文件，将设置`OFN_ALLOWMULTISELECT`标志你在调用之前[DoModal](#domodal)。 必须提供你自己的文件名称缓冲区来存储返回多个文件名称的列表。 执行此操作通过替换`m_ofn.lpstrFile`指向缓冲区的指针与你已分配之后你构造, [CFileDialog](../../mfc/reference/cfiledialog-class.md)，但你在调用之前`DoModal`。 此外，必须设置`m_ofn.nMaxFile`具有指向的缓冲区中的字符数`m_ofn.lpstrFile`。 如果设置到选定文件的最大数目`n`，必要的缓冲区大小是`n`*(_MAX_PATH + 1) + 1。 例如:   
  
 [!code-cpp[NVC_MFCFiles#23](../../atl-mfc-shared/reference/codesnippet/cpp/cfiledialog-class_1.cpp)]  
  
 若要使用户能够通过使用鼠标或键盘来调整大小资源管理器样式对话框中，设置`OFN_ENABLESIZING`标志。 设置此标志才是必需提供挂钩过程或自定义模板。 标志仅适用于一个资源管理器样式的对话框;旧样式对话框不能调整大小。  
  
 `lpszFilter`参数用于确定文件必须具有要在文件列表中显示的文件名称的类型。 字符串对中的第一个字符串描述筛选器;第二个字符串指示要使用的文件扩展名。 可通过使用分号 （; 字符） 作为分隔符指定多个扩展。 使用两个结尾的字符串 &#124; 字符后, 跟`NULL`字符。 你还可以使用[CString](../../atl-mfc-shared/using-cstring.md)为此参数的对象。  
  
 例如，[!INCLUDE[ofprexcel](../../mfc/reference/includes/ofprexcel_md.md)]等允许用户打开具有扩展.xlc （图表） 或.xls （工作表） 的文件。 无法编写 Excel 的筛选器，如：  
  
 [!code-cpp[NVC_MFCFiles#24](../../atl-mfc-shared/reference/codesnippet/cpp/cfiledialog-class_2.cpp)]  
  
 但是，如果你打算使用此字符串到直接更新`OPENFILENAME`结构，你应当分隔您用空字符 \0'，而不是垂直图条的字符串 (&#124;)。  
  
 `bVistaStyle`参数是适用的仅在下运行[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。 在早期版本的 Windows，则忽略此参数。 如果`bVistaStyle`设置为`TRUE`，当你编译的程序与 Visual Studio 2008 或更高版本，将新的 Vista 样式**文件对话框**将使用。 否则为上一个 MFC 样式**文件对话框**将使用。  
  
 对话框模板不支持基于的对话框上`bVistaStyle`  
  
### <a name="example"></a>示例  
  请参阅示例[CFileDialog::DoModal](#domodal)。  
  
##  <a name="domodal"></a>CFileDialog::DoModal  
 调用此函数可显示 Windows 公共文件对话框，并允许用户浏览文件和目录，然后输入一个文件名。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 **IDOK**或**IDCANCEL**。 如果**IDCANCEL**是返回，调用 Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916)函数来确定是否发生了错误。  
  
 **IDOK**和**IDCANCEL**是指示用户是否选中确定或取消按钮的常量。  
  
### <a name="remarks"></a>备注  
 如果你想要通过设置的成员初始化的各种文件对话框中选项**m_ofn**结构，应执行此操作，然后再调`DoModal`，但在构造对话框对象之后。  
  
 例如，如果你想要允许用户选择多个文件，则设置`OFN_ALLOWMULTISELECT`标志，然后再调`DoModal`，本主题中的代码示例中所示。  
  
 当用户单击对话框的确定或取消按钮或选择关闭从对话框中的选项控制菜单上时，则将控制返回到你的应用程序。 你可以然后调用其他成员函数来检索设置或信息的用户输入到对话框。  
  
 `DoModal`是从类中重写一个虚函数`CDialog`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles#25](../../atl-mfc-shared/reference/codesnippet/cpp/cfiledialog-class_3.cpp)]  
  
##  <a name="enableopendropdown"></a>CFileDialog::EnableOpenDropDown  
 允许在打开或保存在对话框中的按钮的下拉列表。  
  
```  
HRESULT EnableOpenDropDown(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 下拉列表的 ID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="endvisualgroup"></a>CFileDialog::EndVisualGroup  
 停止添加到对话框中的 visual 组的元素。  
  
```  
HRESULT EndVisualGroup();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则则为 S_OK 返回否则为一个错误值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getcheckbuttonstate"></a>CFileDialog::GetCheckButtonState  
 检索对话框中的复选按钮 （复选框） 的当前状态。  
  
```  
HRESULT GetCheckButtonState(
    DWORD dwIDCtl,  
    BOOL& bChecked);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 复选框的 ID。  
  
 `bChecked`  
 复选框的状态。 `TRUE`指示已检查;`FALSE`指示未选中状态。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getcontrolitemstate"></a>CFileDialog::GetControlItemState  
 检索在对话框中找到的容器控件中的项的当前状态。  
  
```  
HRESULT GetControlItemState(
    DWORD dwIDCtl,  
    DWORD dwIDItem,  
    CDCONTROLSTATEF& dwState);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 容器控件的 ID。  
  
 `dwIDItem`  
 项的 ID。  
  
 `dwState`  
 对接收多个值之一，该值指示控件的当前状态 CDCONTROLSTATE 枚举中的变量的引用。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getcontrolstate"></a>CFileDialog::GetControlState  
 检索当前可见性，并已启用的某一给定控件的状态。  
  
```  
HRESULT GetControlState(
    DWORD dwIDCtl,  
    CDCONTROLSTATEF& dwState);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 控件的 ID。  
  
 `dwState`  
 对接收 CDCONTROLSTATE 枚举，该值指示控件的当前状态中的一个或多个值的变量的引用。  
  
### <a name="remarks"></a>备注  
  
##  <a name="geteditboxtext"></a>CFileDialog::GetEditBoxText  
 检索当前的编辑框控件中的文本。  
  
```  
HRESULT GetEditBoxText(
    DWORD dwIDCtl,  
    CString& strText);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 编辑框的 ID。  
  
 `strText`  
 文本值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getfileext"></a>CFileDialog::GetFileExt  
 调用此函数可检索到该对话框中输入的文件名的扩展名。  
  
```  
CString GetFileExt() const;  
```  
  
### <a name="return-value"></a>返回值  
 文件名的扩展名。  
  
### <a name="remarks"></a>备注  
 例如，如果输入的文件的名称是数据。TXT、`GetFileExt`返回"TXT"。  
  
 如果`m_ofn.Flags`具有`OFN_ALLOWMULTISELECT`标志设置，此字符串包含一个以 null 结尾的字符串，与所选，文件组的目录路径的第一个字符串序列跟的用户选定的所有文件的名称。 若要检索文件的路径名，使用[GetStartPosition](#getstartposition)和[GetNextPathName](#getnextpathname)成员函数。  
  
##  <a name="getfilename"></a>CFileDialog::GetFileName  
 调用此函数可检索对话框中输入的文件名的名称。  
  
```  
CString GetFileName() const;  
```  
  
### <a name="return-value"></a>返回值  
 文件的名称。  
  
### <a name="remarks"></a>备注  
 文件的名称中包含的前缀和扩展。 例如，`GetFileName`将返回"文本。DAT"C:\FILES\TEXT.DAT 的文件。  
  
 如果`m_ofn.Flags`具有`OFN_ALLOWMULTISELECT`标志设置，应调用[GetStartPosition](#getstartposition)和[GetNextPathName](#getnextpathname)检索文件的路径名。  
  
##  <a name="getfiletitle"></a>CFileDialog::GetFileTitle  
 调用此函数可检索对话框中输入文件的标题。  
  
```  
CString GetFileTitle() const;  
```  
  
### <a name="return-value"></a>返回值  
 文件的标题。  
  
### <a name="remarks"></a>备注  
 文件的标题包含仅其前缀，而无需路径或扩展。 例如，`GetFileTitle`文件 C:\FILES\TEXT.DAT 将返回"TEXT"。  
  
 如果`m_ofn.Flags`具有`OFN_ALLOWMULTISELECT`标志设置，此字符串包含一个以 null 结尾的字符串，与所选，文件组的目录路径的第一个字符串序列跟的用户选定的所有文件的名称。 出于此原因，而使用[GetStartPosition](#getstartposition)和[GetNextPathName](#getnextpathname)成员函数以检索列表中的下一步文件名称。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileDialog::DoModal](#domodal)。  
  
##  <a name="getfolderpath"></a>CFileDialog::GetFolderPath  
 调用此成员函数可检索的当前打开的文件夹或资源管理器样式打开或另存为的通用对话框的目录的路径。  
  
```  
CString GetFolderPath() const;  
```  
  
### <a name="return-value"></a>返回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，其中包含当前打开的文件夹或目录。  
  
### <a name="remarks"></a>备注  
 对话框中必须已创建具有**OFN_EXPLORER**样式; 否则，该方法将失败，断言。  
  
 仅当显示对话框中，你可以调用此方法。 关闭该对话框后，此函数将不再工作，并且该方法将失败，断言。  
  
##  <a name="getifiledialogcustomize"></a>CFileDialog::GetIFileDialogCustomize  
 检索指向为内部的 COM 对象的指针给定[CFileDialog](../../mfc/reference/cfiledialog-class.md)。  
  
```  
IFileDialogCustomize* GetIFileDialogCustomize();
```  
  
### <a name="return-value"></a>返回值  
 为内部的 COM 对象的指针`CFileDialog`。 它由你负责正确释放该指针。  
  
### <a name="remarks"></a>备注  
 使用此函数仅在[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]具有的对象与`bVistaStyle`设置为`true`。 如果使用此函数时`bVistaStyle`是`false`，它将返回`NULL`在发布模式下和 throw 在调试模式下的断言。  
  
 有关详细信息`IFileDialogCustomize`接口，请参阅[IFileDialogCustomize](http://msdn.microsoft.com/library/windows/desktop/bb775912)。  
  
### <a name="example"></a>示例  
 此示例检索内部的 COM 对象。 若要运行此代码示例，你必须对其进行编译下[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。  
  
 [!code-cpp[NVC_MFC_CFileDialog#4](../../mfc/reference/codesnippet/cpp/cfiledialog-class_4.cpp)]  
  
##  <a name="getifileopendialog"></a>CFileDialog::GetIFileOpenDialog  
 检索指向为内部的 COM 对象的指针给定`CFileDialog`。  
  
```  
IFileOpenDialog* GetIFileOpenDialog();
```  
  
### <a name="return-value"></a>返回值  
 为内部的 COM 对象的指针`CFileDialog`。 它由你负责正确释放该指针。  
  
### <a name="remarks"></a>备注  
 使用此函数仅在[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]具有的对象与`bVistaStyle`设置为`true`。 此函数将返回`NULL`如果`CFileDialog`不**打开**对话框或如果`bVistaStyle`设置为`false`。 在此最终的情况下，该函数将仅返回`NULL`在发布模式下-在调试模式下，它将引发一个断言。  
  
 有关详细信息`IFileOpenDialog`接口，请参阅[IFileOpenDialog](http://msdn.microsoft.com/library/windows/desktop/bb775834)。  
  
### <a name="example"></a>示例  
 此示例检索内部的 COM 对象。 若要运行此代码，你必须对其进行编译下[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。  
  
 [!code-cpp[NVC_MFC_CFileDialog#2](../../mfc/reference/codesnippet/cpp/cfiledialog-class_5.cpp)]  
  
##  <a name="getifilesavedialog"></a>CFileDialog::GetIFileSaveDialog  
 检索指向为内部的 COM 对象的指针给定`CFileDialog`。  
  
```  
IFileSaveDialog* GetIFileSaveDialog();
```  
  
### <a name="return-value"></a>返回值  
 为内部的 COM 对象的指针`CFileDialog`。 它由你负责正确释放该指针。  
  
### <a name="remarks"></a>备注  
 使用此函数仅在[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]具有的对象与`bVistaStyle`设置为`true`。 此函数将返回`NULL`如果`CFileDialog`不**保存**对话框或如果`bVistaStyle`设置为`false`。 在此最终的情况下，该函数将仅返回`NULL`在发布模式下-在调试模式下，它将引发一个断言。  
  
 有关详细信息`IFileSaveDialog`接口，请参阅[IFileSaveDialog](http://msdn.microsoft.com/library/windows/desktop/bb775688)。  
  
### <a name="example"></a>示例  
 此示例检索内部的 COM 对象。 若要运行此代码示例，你必须对其进行编译下[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。  
  
 [!code-cpp[NVC_MFC_CFileDialog#3](../../mfc/reference/codesnippet/cpp/cfiledialog-class_6.cpp)]  
  
##  <a name="getnextpathname"></a>CFileDialog::GetNextPathName  
 调用此函数可从在对话框中选择的组中检索的下一个文件名。  
  
```  
CString GetNextPathName(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 对引用**位置**通过前一个返回值`GetNextPathName`或`GetStartPosition`函数调用。 **NULL**如果已到达列表的末尾。  
  
### <a name="return-value"></a>返回值  
 文件的完整路径。  
  
### <a name="remarks"></a>备注  
 文件名的路径包括文件的标题以及整个目录路径。 例如，`GetNextPathName`将返回"C:\FILES\TEXT。DAT"C:\FILES\TEXT.DAT 的文件。 你可以使用`GetNextPathName`如果建立通过调用的初始位置的向前迭代循环中`GetStartPosition`。  
  
 如果所选内容包含一个文件，将返回该文件名称。  
  
##  <a name="getofn"></a>CFileDialog::GetOFN  
 检索关联**OPENFILENAME**结构。  
  
```  
const OPENFILENAME& GetOFN() const;  
  
OPENFILENAME& GetOFN();
```  
  
### <a name="return-value"></a>返回值  
 [OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839)结构。  
  
### <a name="remarks"></a>备注  
 使用此函数的第二个版本来初始化的外观**文件打开**或**文件另存为**对话框中构造它之后，但它显示为带之前`DoModal`成员函数。 例如，你可以设置**lpstrTitle**的成员**m_ofn**想对话框中，具有到链接的标题。  
  
##  <a name="getpathname"></a>CFileDialog::GetPathName  
 调用此函数可检索对话框中输入的文件的完整路径。  
  
```  
CString GetPathName() const;  
```  
  
### <a name="return-value"></a>返回值  
 文件的完整路径。  
  
### <a name="remarks"></a>备注  
 文件名的路径包括文件的标题以及整个目录路径。 例如，`GetPathName`将返回"C:\FILES\TEXT。DAT"C:\FILES\TEXT.DAT 的文件。  
  
 如果`m_ofn.Flags`具有`OFN_ALLOWMULTISELECT`标志设置，此字符串包含一系列的 null teminated 正在所选，文件组的目录路径的第一个字符串的字符串后, 跟的用户选定的所有文件的名称。 出于此原因，而使用[GetStartPosition](#getstartposition)和[GetNextPathName](#getnextpathname)成员函数以检索列表中的下一步文件名称。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileDialog::DoModal](#domodal)。  
  
##  <a name="getreadonlypref"></a>CFileDialog::GetReadOnlyPref  
 调用此函数可确定是否已在 Windows 标准文件打开和文件另存为对话框框中选择了只读复选框。  
  
```  
BOOL GetReadOnlyPref() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零在对话框中 Read Only 复选框为选中状态; 如果否则为 0。  
  
### <a name="remarks"></a>备注  
 你可以通过设置隐藏只读复选框`OFN_HIDEREADONLY`设置中的样式`CFileDialog`构造函数。  
  
> [!NOTE]
> [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]样式`CFileDialog`对象不支持此函数。 尝试使用此函数在[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]样式`CFileDialog`将引发[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。   
  
##  <a name="getresult"></a>CFileDialog::GetResult  
 检索用户在对话框中所做的选择。  
  
```  
IShellItem* GetResult() throw();
```  
  
### <a name="return-value"></a>返回值  
 表示用户的选择 IShellItem 指向的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getresults"></a>CFileDialog::GetResults  
 检索一个对话框，允许多个所选内容中的用户的选项。  
  
```  
IShellItemArray* GetResults() throw();
```  
  
### <a name="return-value"></a>返回值  
 可以通过其访问对话框中选定的项 IShellItemArray 指向的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getselectedcontrolitem"></a>CFileDialog::GetSelectedControlItem  
 从对话框中指定的容器控件中检索特定项。  
  
```  
HRESULT GetSelectedControlItem(
    DWORD dwIDCtl,  
    DWORD& dwIDItem);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 容器控件的 ID。  
  
 `dwIDItem`  
 用户控件中选定的项的 ID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getstartposition"></a>CFileDialog::GetStartPosition  
 如果调用该成员函数以检索在列表中，第一个文件路径名的位置`m_ofn.Flags`具有`OFN_ALLOWMULTISELECT`标志设置。  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 A**位置**可以用于迭代; 的值**NULL**如果列表为空。  
  
##  <a name="hidecontrol"></a>CFileDialog::HideControl  
 调用此成员函数以隐藏在资源管理器样式打开或另存为的通用对话框中指定的控件。  
  
```  
void HideControl(int nID);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 若要隐藏的控件 ID。  
  
### <a name="remarks"></a>备注  
 对话框中必须已创建具有**OFN_EXPLORER**样式; 否则，该函数将与断言失败。  
  
##  <a name="ispickfoldersmode"></a>CFileDialog::IsPickFoldersMode  
 确定当前对话框是否文件夹选取器模式下。  
  
```  
BOOL IsPickFoldersMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果对话框在文件夹选取器模式下;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="m_ofn"></a>CFileDialog::m_ofn  
 `m_ofn`是一种类型的结构`OPENFILENAME`。 此结构中的数据表示的当前状态`CFileDialog`。  
  
### <a name="remarks"></a>备注  
 使用此结构初始化的外观**文件打开**或**文件另存为**对话框中，在构造之后但在显示其与之前[DoModal](#domodal)方法。 例如，你可以设置`lpstrTitle`的成员`m_ofn`想对话框中，具有到链接的标题。  
  
 与[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]样式[CFileDialog](../../mfc/reference/cfiledialog-class.md)，`m_ofn`不保证始终与对话框中的状态匹配。 它与早期版本的 Windows 中的对话框同步。 请参阅[CFileDialog::ApplyOFNToShellDialog](#applyofntoshelldialog)和[CFileDialog::UpdateOFNFromShellDialog](#updateofnfromshelldialog)有关同步的详细信息`m_ofn`结构和`CFileDialog`状态下[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。  
  
 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]样式文件对话框不支持某些成员和标志`CFileDialog`。 因此，这些将产生任何影响。  
  
 以下是不支持的成员的列表[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]:  
  
- `lpstrCustomFilter`  
  
- `lpstrInitialDir`  
  
- `lCustData`  
  
- `lpfnHook`  
  
- `lpTemplateName`  
  
 以下标志不受支持，因此使用时产生任何影响[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]样式`CFileDialog`:  
  
-   OFN_ENABLEHOOK  
  
-   OFN_ENABLEINCLUDENOTIFY  
  
-   OFN_ENABLETEMPLATE  
  
-   OFN_ENABLETEMPLATEHANDLE  
  
-   OFN_EXPLORER  
  
-   OFN_EXTENSIONDIFFERENT  
  
-   OFN_HIDEREADONLY  
  
-   OFN_LONGNAMES-有效地始终上中[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]  
  
-   在中有效地始终关闭 OFN_NOLONGNAMES-[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]  
  
-   OFN_NONETWORKBUTTON-有效地始终上中[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]  
  
-   OFN_READONLY  
  
-   OFN_SHOWHELP  
  
 有关此结构的详细信息，请参阅[OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839) Windows SDK 中的结构。  
  
##  <a name="makeprominent"></a>CFileDialog::MakeProminent  
 位置对话框中的控件，以便它醒目相比其他控件。  
  
```  
HRESULT MakeProminent(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 控件的 ID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onbuttonclicked"></a>CFileDialog::OnButtonClicked  
 单击该按钮时调用。  
  
```  
virtual void OnButtonClicked(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 按钮的 ID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="oncheckbuttontoggled"></a>CFileDialog::OnCheckButtonToggled  
 选中或取消选中复选框时调用。  
  
```  
virtual void OnCheckButtonToggled(
    DWORD dwIDCtl,  
    BOOL bChecked);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 复选框的 ID。  
  
 `bChecked`  
 选中或取消选中。  
  
### <a name="remarks"></a>备注  
  
##  <a name="oncontrolactivating"></a>CFileDialog::OnControlActivating  
 激活控件时调用。  
  
```  
virtual void OnControlActivating(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 控件的 ID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onfilenamechange"></a>CFileDialog::OnFileNY` `更改  
 重写此方法，如果你想要处理`WM_NOTIFY``CDN_SELCHANGE`消息。  
  
```  
virtual void OnFileNameChange();
```  
  
### <a name="remarks"></a>备注  
 系统会将发送`CDN_SELCHANGE`消息时用户的文件列表中选择新文件或文件夹**打开**或**另存为**对话框。 如果你想要在响应此消息执行任何操作，重写此方法。  
  
 仅当使用开启 OFN_EXPLORER 标志创建对话框中，系统将发送此消息。 有关通知的详细信息，请参阅[CDN_SELCHANGE](http://msdn.microsoft.com/library/windows/desktop/ms646865)。 有关 OFN_EXPLORER 标志的信息，请参阅[OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839)结构和[打开和保存为对话框](http://msdn.microsoft.com/library/windows/desktop/ms646960)。  
  
##  <a name="onfilenameok"></a>CFileDialog::OnFileNameOK  
 仅当你想要提供自定义验证的通用文件对话框中输入的文件名，重写此函数。  
  
```  
virtual BOOL OnFileNameOK();
```  
  
### <a name="return-value"></a>返回值  
 文件名不是有效的文件名; 如果为 1否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数使你可以为任何应用程序特定原因拒绝文件名。 通常情况下，不需要使用此函数，因为框架提供的文件名的默认验证并显示一个消息框，如果输入无效的文件名。  
  
 如果返回 1，对话框中将仍显示为用户输入另一个文件名。 如果返回为 0，则对话框过程解除对话框。 其他非零返回值是当前保留的并且不应使用。  
  
##  <a name="onfolderchange"></a>CFileDialog::OnFolderChange  
 重写此函数来处理**WM_NOTIFYCDN_FOLDERCHANGE**消息。  
  
```  
virtual void OnFolderChange();
```  
  
### <a name="remarks"></a>备注  
 在打开或另存为对话框中打开一个新文件夹时，是发送通知消息。  
  
 仅当使用 OFN_EXPLORER 样式创建对话框中，会发送通知。 有关通知的详细信息，请参阅[CDN_FOLDERCHANGE](http://msdn.microsoft.com/library/windows/desktop/ms646859)。 OFN_EXPLORER 样式有关的信息，请参阅[OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839)结构和[打开和保存为对话框](http://msdn.microsoft.com/library/windows/desktop/ms646960)。  
  
##  <a name="oninitdone"></a>CFileDialog::OnInitDone  
 重写此函数来处理`WM_NOTIFY``CDN_INITDONE`消息。  
  
```  
virtual void OnInitDone();
```  
  
### <a name="remarks"></a>备注  
 系统会将系统完排列中的控件时发送此通知消息**打开**或**另存为**对话框中，以便腾出空间供子对话框中的控件。  
  
 系统将此发送仅当使用对话框中创建了 OFN_EXPLORER 样式。 有关通知的详细信息，请参阅[CDN_INITDONE](http://msdn.microsoft.com/library/windows/desktop/ms646863)。 OFN_EXPLORER 样式有关的信息，请参阅[OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839)结构和[打开和保存为对话框](http://msdn.microsoft.com/library/windows/desktop/ms646960)。  
  
> [!NOTE]
> [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]样式文件对话框不支持此函数。 尝试使用此函数在[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]样式文件对话框将引发[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。 
  
##  <a name="onitemselected"></a>CFileDialog::OnItemSelected  
 当选择容器项时调用。  
  
```  
virtual void OnItemSelected(
    DWORD dwIDCtl,  
    DWORD dwIDItem);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 容器控件的 ID。  
  
 `dwIDItem`  
 项的 ID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onlbselchangednotify"></a>CFileDialog::OnLBSelChangedNotify  
 每当即将更改的列表框中的当前所选内容，都会调用此函数。  
  
```  
virtual void OnLBSelChangedNotify(
    UINT nIDBox,  
    UINT iCurSel,  
    UINT nCode);
```  
  
### <a name="parameters"></a>参数  
 *nIDBox*  
 列表框或在其中发生所选内容的组合框的 ID。  
  
 `iCurSel`  
 当前所选内容的索引。  
  
 `nCode`  
 控件通知代码。 此参数必须具有下列值之一：  
  
- **CD_LBSELCHANGE**指定`iCurSel`是单项选择列表框中选定的项。  
  
- **CD_LBSELSUB**指定`iCurSel`在多选列表框中不再被选中。  
  
- **CD_LBSELADD**指定`iCurSel`多选列表框中选择。  
  
- **CD_LBSELNOITEMS**指定任何选择是否存在于多选列表框。  
  
### <a name="remarks"></a>备注  
 重写此函数可提供自定义的处理操作的选择列表框中会有所变化。 例如，你可以使用此函数来显示的访问权限或日期的上次修改每个文件的用户选择。  
  
##  <a name="onshareviolation"></a>CFileDialog::OnShareViolation  
 重写此函数可提供自定义的处理操作的共享冲突。  
  
```  
virtual UINT OnShareViolation(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>参数  
 `lpszPathName`  
 发生共享冲突文件的路径。  
  
### <a name="return-value"></a>返回值  
 以下值之一：  
  
- **OFN_SHAREFALLTHROUGH**从对话框中返回文件名。  
  
- **OFN_SHARENOWARN**需要采取任何进一步的操作。  
  
- **OFN_SHAREWARN**用户会收到此错误的标准的警告消息。  
  
### <a name="remarks"></a>备注  
 通常情况下，不需要使用此函数，因为框架提供了默认的共享冲突检查并显示一个消息框，如果发生共享冲突。  
  
 如果你想要禁用共享冲突检查，使用按位 OR 运算符合并标志**OFN_SHAREAWARE**与`m_ofn.Flags`。  
  
##  <a name="ontypechange"></a>CFileDialog::OnTypeChange  
 重写此函数来处理**WM_NOTIFYCDN_TYPECHANGE**消息。  
  
```  
virtual void OnTypeChange();
```  
  
### <a name="remarks"></a>备注  
 当用户选择从列表中打开的文件类型的新文件类型或另存为对话框中，是发送通知消息。  
  
 仅当使用 OFN_EXPLORER 样式创建对话框中，会发送通知。 有关通知的详细信息，请参阅[CDN_TYPECHANGE](http://msdn.microsoft.com/library/windows/desktop/ms646868)。 OFN_EXPLORER 样式有关的信息，请参阅[OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839)结构和[打开和保存为对话框](http://msdn.microsoft.com/library/windows/desktop/ms646960)。  
  
##  <a name="removecontrolitem"></a>CFileDialog::RemoveControlItem  
 在对话框的容器控件中移除的项。  
  
```  
HRESULT RemoveControlItem(
    DWORD dwIDCtl,  
    DWORD dwIDItem);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 要从中移除项的容器控件的 ID。  
  
 `dwIDItem`  
 项的 ID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setcheckbuttonstate"></a>CFileDialog::SetCheckButtonState  
 在对话框中设置勾选按钮 （复选框） 的当前的状态。  
  
```  
HRESULT SetCheckButtonState(
    DWORD dwIDCtl,  
    BOOL bChecked);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 复选框的 ID。  
  
 `bChecked`  
 复选框的状态。 `TRUE`指示已检查;`FALSE`指示选中状态。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setcontrolitemstate"></a>CFileDialog::SetControlItemState  
 在对话框中找到的容器控件中设置项的当前的状态。  
  
```  
HRESULT SetControlItemState(
    DWORD dwIDCtl,  
    DWORD dwIDItem,  
    CDCONTROLSTATEF dwState);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 容器控件的 ID。  
  
 `dwIDItem`  
 项的 ID。  
  
 `dwState`  
 一个或多个 CDCONTROLSTATE 枚举值，指示该控件的新状态。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setcontrolitemtext"></a>CFileDialog::SetControlItemText  
 设置控件项的文本。 例如，附带一个单选按钮或菜单中的项的文本。  
  
```  
HRESULT SetControlItemText(
    DWORD dwIDCtl,  
    DWORD dwIDItem,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 容器控件的 ID。  
  
 `dwIDItem`  
 项的 ID。  
  
 `strLabel`  
 项的文本。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setcontrollabel"></a>CFileDialog::SetControlLabel  
 设置与控件，如按钮文本或编辑框标签关联的文本。  
  
```  
HRESULT SetControlLabel(
    DWORD dwIDCtl,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 控件的 ID。  
  
 `strLabel`  
 控件名称。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setcontrolstate"></a>CFileDialog::SetControlState  
 设置当前的可见性和已启用的某一给定控件的状态。  
  
```  
HRESULT SetControlState(
    DWORD dwIDCtl,  
    CDCONTROLSTATEF dwState);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 控件的 ID。  
  
 `dwState`  
 一个或多个值 CDCONTROLSTATE 枚举中指示该控件的当前状态。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setcontroltext"></a>CFileDialog::SetControlText  
 调用此方法以在资源管理器样式中设置为指定的控件的文本**打开**或**另存为**对话框。  
  
```  
void SetControlText(
    int nID,  
    LPCSTR lpsz);

 
void SetControlText(
    int nID,  
    const wchar_t *lpsz);
```  
  
### <a name="parameters"></a>参数  
 [in] `nID`  
 为其设置的文本控件的 ID。  
  
 [in] `lpsz`  
 指向包含要设置控件的文本的字符串的指针。  
  
### <a name="remarks"></a>备注  
 此函数的两个版本是有效的应用程序使用 Unicode。 但是，仅与 LPCSTR 类型的版本是有效的应用程序使用[!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)]。  
  
 若要使用此方法，必须使用 OFN_EXPLORER 样式创建对话框。 否则，该函数将与断言失败。  
  
##  <a name="setdefext"></a>CFileDialog::SetDefExt  
 调用此函数可设置资源管理器样式打开或另存为的通用对话框的默认文件扩展名。  
  
```  
void SetDefExt(LPCSTR lpsz);
```  
  
### <a name="parameters"></a>参数  
 `lpsz`  
 指向包含要使用的对话框对象的默认扩展名的字符串的指针。 此字符串必须包含一个句点 （.）。  
  
### <a name="remarks"></a>备注  
 对话框中必须已创建具有**OFN_EXPLORER**样式; 否则，该函数将与断言失败。  
  
##  <a name="seteditboxtext"></a>CFileDialog::SetEditBoxText  
 在编辑框控件中设置的当前文本。  
  
```  
HRESULT SetEditBoxText(
    DWORD dwIDCtl,  
    const CString& strText);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 编辑框的 ID。  
  
 `strText`  
 文本值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setproperties"></a>CFileDialog::SetProperties  
 提供一个属性存储，它定义将默认值用于正在保存的项。  
  
```  
BOOL SetProperties(LPCWSTR lpszPropList);
```  
  
### <a name="parameters"></a>参数  
 `lpszPropList`  
 由“;”分隔的预定义的属性列表。 标志的列表，请参阅`Flags`部分[OPENFILENAME](http://msdn.microsoft.com/en-us/8cecfd45-f7c1-4f8d-81a0-4e7fecc3b104)。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setselectedcontrolitem"></a>CFileDialog::SetSelectedControlItem  
 中的选项按钮组或在对话框中找到一个组合框设置特定项的选定的状态。  
  
```  
HRESULT SetSelectedControlItem(
    DWORD dwIDCtl,  
    DWORD dwIDItem);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 容器控件的 ID。  
  
 `dwIDItem`  
 用户控件中选定的项的 ID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="settemplate"></a>CFileDialog::SetTemplate  
 设置为对话框模板[CFileDialog](../../mfc/reference/cfiledialog-class.md)对象。  
  
```  
void SetTemplate(
    UINT nWin3ID,  
    UINT nWin4ID);

 
void SetTemplate(
    LPCTSTR lpWin3ID,  
    LPCTSTR lpWin4ID);
```  
  
### <a name="parameters"></a>参数  
 [in] `nWin3ID`  
 包含非 Explorer 的模板资源的 ID 号`CFileDialog`对象。 在 Windows NT 3.51 或不存在 OFN_EXPLORER 样式时，仅使用此模板。  
  
 [in] `nWin4ID`  
 该资源管理器中包含的模板资源的 ID 号`CFileDialog`对象。 仅在使用此模板[!INCLUDE[WinNt4Family](../../mfc/reference/includes/winnt4family_md.md)]和更高版本、 Windows 95 和更高版本，或存在 OFN_EXPLORER 样式时。  
  
 [in] `lpWin3ID`  
 包含非 Explorer 的模板资源的名称`CFileDialog`对象。 在 Windows NT 3.51 或不存在 OFN_EXPLORER 样式时，仅使用此模板。  
  
 [in] `lpWin4ID`  
 包含名称的资源管理器的模板资源`CFileDialog`对象。 仅在使用此模板[!INCLUDE[WinNt4Family](../../mfc/reference/includes/winnt4family_md.md)]和更高版本、 Windows 95 和更高版本，或存在 OFN_EXPLORER 样式时。  
  
### <a name="remarks"></a>备注  
 系统将使用指定的模板之一。 在系统确定要使用的模板根据 OFN_EXPLORER 样式和运行应用程序的操作系统的状态。 通过指定的非资源管理器和资源管理器样式模板，可以很容易到支持 Windows NT 3.51[!INCLUDE[WinNt4Family](../../mfc/reference/includes/winnt4family_md.md)]和更高版本和 Windows 95 和更高版本。  
  
> [!NOTE]
> [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]样式文件对话框不支持此函数。 尝试使用此函数在[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]样式文件对话框中将引发[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。 一种替代方法是使用自定义的对话框。 有关使用自定义的详细信息`CFileDialog`，请参阅[IFileDialogCustomize](http://msdn.microsoft.com/library/windows/desktop/bb775912)。  
  
##  <a name="startvisualgroup"></a>CFileDialog::StartVisualGroup  
 声明对话框中的 visual 组。 对任何"add"方法的后续调用将这些元素添加到此组。  
  
```  
HRESULT StartVisualGroup(
    DWORD dwIDCtl,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 Visual 组的 ID。  
  
 `strLabel`  
 组名称中。  
  
### <a name="remarks"></a>备注  
  
##  <a name="updateofnfromshelldialog"></a>CFileDialog::UpdateOFNFromShellDialog  
 更新`m_ofn`数据结构[CFileDialog](../../mfc/reference/cfiledialog-class.md)基于内部对象的当前状态。  
  
```  
void UpdateOFNFromShellDialog();
```  
  
### <a name="remarks"></a>备注  
 在之前的 Windows 版本中[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]，成员[OPENFILENAME](https://msdn.microsoft.com/library/ms911906.aspx)持续的状态同步数据结构`CFileDialog`。 对任何更改[m_ofn](#m_ofn)成员变量直接受影响的对话框中的状态。 此外，对对话框中的状态的任何更改立即更新 m_ofn 成员变量。  
  
 在[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]、`m_ofn`数据结构不会自动更新。 若要确保中的数据的准确性`m_ofn`成员变量，则应调用`UpdateOFNFromShellDialog`之前访问的数据的函数。 Windows 会调用此函数会自动在处理过程[IFileDialog::OnFileOK](http://msdn.microsoft.com/library/windows/desktop/bb775879)。  
  
 有关如何使用`CFileDialog`类下[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]，请参阅[CFileDialog 类](../../mfc/reference/cfiledialog-class.md)。  
  
### <a name="example"></a>示例  
 此示例将更新`CFileDialog`之前显示它。 在更新前`m_ofn`成员变量，我们需要同步到对话框中的当前状态。  
  
 [!code-cpp[NVC_MFC_CFileDialog#1](../../mfc/reference/codesnippet/cpp/cfiledialog-class_7.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)

