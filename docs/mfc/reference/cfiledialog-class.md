---
title: "CFileDialog 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFileDialog
dev_langs:
- C++
helpviewer_keywords:
- CFileDialog class
- common file dialog boxes
- dialog boxes, common
ms.assetid: fda4fd3c-08b8-4ce0-8e9d-7bab23f8c6c0
caps.latest.revision: 47
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
ms.openlocfilehash: 7cde10ee445a719bce6be4167698bd86c46a18c0
ms.lasthandoff: 02/24/2017

---
# <a name="cfiledialog-class"></a>CFileDialog 类
封装用于文件打开或保存操作的文件公共对话框。  
  
## <a name="syntax"></a>语法  
  
```  
class CFileDialog : public CCommonDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CFileDialog::CFileDialog](#cfiledialog)|构造 `CFileDialog` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CFileDialog::AddCheckButton](#addcheckbutton)|向对话框中勾选按钮。|  
|[CFileDialog::AddComboBox](#addcombobox)|将组合框添加到对话框。|  
|[CFileDialog::AddControlItem](#addcontrolitem)|将项添加到对话框中的容器控件。|  
|[CFileDialog::AddEditBox](#addeditbox)|将一个编辑框添加到对话框。|  
|[CFileDialog::AddMenu](#addmenu)|向对话框添加一个菜单。|  
|[CFileDialog::AddPlace](#addplace)|已重载。 将添加到列表中的文件夹将适用于用户打开或保存项目。|  
|[CFileDialog::AddPushButton](#addpushbutton)|为对话框中添加一个按钮。|  
|[CFileDialog::AddRadioButtonList](#addradiobuttonlist)|将选项按钮 （也称为单选按钮） 组添加到对话框。|  
|[CFileDialog::AddSeparator](#addseparator)|向对话框添加分隔符。|  
|[CFileDialog::AddText](#addtext)|将文本内容添加到对话框。|  
|[CFileDialog::ApplyOFNToShellDialog](#applyofntoshelldialog)|更新的状态，并且`CFileDialog`来匹配的参数和标志中存储`m_ofn`成员变量。|  
|[CFileDialog::DoModal](#domodal)|显示对话框中，并使用户能够做出选择。|  
|[CFileDialog::EnableOpenDropDown](#enableopendropdown)|则在启用下拉列表**打开**或**保存**对话框中的按钮。|  
|[CFileDialog::EndVisualGroup](#endvisualgroup)|停止在添加到对话框中的可视化组元素。|  
|[CFileDialog::GetCheckButtonState](#getcheckbuttonstate)|获取对话框中的复选按钮 （复选框） 的当前状态。|  
|[CFileDialog::GetControlItemState](#getcontrolitemstate)|获取在对话框中找到的容器控件中的项的当前状态。|  
|[CFileDialog::GetControlState](#getcontrolstate)|获取当前可见性，并启用某一给定控件的状态。|  
|[CFileDialog::GetEditBoxText](#geteditboxtext)|获取一个编辑框控件中当前的文本。|  
|[CFileDialog::GetFileExt](#getfileext)|返回所选文件的扩展名。|  
|[CFileDialog::GetFileName](#getfilename)|返回所选文件的文件名。|  
|[CFileDialog::GetFileTitle](#getfiletitle)|返回所选文件的标题。|  
|[CFileDialog::GetFolderPath](#getfolderpath)|检索当前打开的文件夹或目录的路径的资源管理器样式**打开**或**另存为**通用对话框。|  
|[CFileDialog::GetIFileDialogCustomize](#getifiledialogcustomize)|检索自定义的内部 COM 对象`CFileDialog`对象。|  
|[CFileDialog::GetIFileOpenDialog](#getifileopendialog)|检索的内部 COM 对象`CFileDialog`被用作**打开**文件对话框。|  
|[CFileDialog::GetIFileSaveDialog](#getifilesavedialog)|检索的内部 COM 对象`CFileDialog`被用作**保存**文件对话框。|  
|[CFileDialog::GetNextPathName](#getnextpathname)|返回下一步所选文件的完整路径。|  
|[CFileDialog::GetOFN](#getofn)|检索`OPENFILENAME`结构`CFileDialog`对象。|  
|[CFileDialog::GetPathName](#getpathname)|返回所选文件的完整路径。|  
|[CFileDialog::GetReadOnlyPref](#getreadonlypref)|返回所选文件的只读状态。|  
|[CFileDialog::GetResult](#getresult)|获取用户在对话框中所做的选择。|  
|[CFileDialog::GetResults](#getresults)|在一个对话框，允许多个所选内容中获取用户的选择。|  
|[CFileDialog::GetSelectedControlItem](#getselectedcontrolitem)|从对话框中指定的容器控件中获取特定的项。|  
|[CFileDialog::GetStartPosition](#getstartposition)|返回文件名列表的第一个元素的位置。|  
|[CFileDialog::HideControl](#hidecontrol)|隐藏指定的控件中的资源管理器样式**打开**或**另存为**通用对话框。|  
|[CFileDialog::IsPickFoldersMode](#ispickfoldersmode)|确定是否在文件夹选取器模式下的当前对话框。|  
|[CFileDialog::MakeProminent](#makeprominent)|位置对话框中的控件，以便它醒目相比其他添加的控件。|  
|[CFileDialog::RemoveControlItem](#removecontrolitem)|在对话框中的容器控件中移除的项。|  
|[CFileDialog::SetCheckButtonState](#setcheckbuttonstate)|在对话框中设置复选按钮 （复选框） 的当前的状态。|  
|[CFileDialog::SetControlItemState](#setcontrolitemstate)|在对话框中找到的容器控件中设置某一项的当前状态。|  
|[CFileDialog::SetControlItemText](#setcontrolitemtext)|设置控件项的文本。 例如，通常会显示单选按钮或菜单中的项的文本。|  
|[CFileDialog::SetControlLabel](#setcontrollabel)|设置与控件，例如，按钮文本或编辑框标签关联的文本。|  
|[CFileDialog::SetControlState](#setcontrolstate)|设置当前的可见性和启用的给定控件的状态。|  
|[CFileDialog::SetControlText](#setcontroltext)|中的资源管理器样式设置为指定的控件的文本**打开**或**另存为**通用对话框。|  
|[CFileDialog::SetDefExt](#setdefext)|设置资源管理器样式的默认文件扩展名**打开**或**另存为**通用对话框。|  
|[CFileDialog::SetEditBoxText](#seteditboxtext)|在编辑框控件中设置的当前文本。|  
|[CFileDialog::SetProperties](#setproperties)|提供一个属性存储，它定义将默认值用于正在保存的项。|  
|[CFileDialog::SetSelectedControlItem](#setselectedcontrolitem)|选项按钮组或在对话框中找到一个组合框中设置特定项的选定的状态。|  
|[CFileDialog::SetTemplate](#settemplate)|设置的对话框模板`CFileDialog`对象。|  
|[CFileDialog::StartVisualGroup](#startvisualgroup)|声明对话框中的可视化组。 向"添加"的任何方法的后续调用将这些元素添加到该组。|  
|[CFileDialog::UpdateOFNFromShellDialog](#updateofnfromshelldialog)|更新的数据存储在`m_ofn`成员变量以匹配文件对话框中的当前状态。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CFileDialog::OnButtonClicked](#onbuttonclicked)|单击该按钮时调用。|  
|[CFileDialog::OnCheckButtonToggled](#oncheckbuttontoggled)|当未选中/选中复选框时调用。|  
|[CFileDialog::OnControlActivating](#oncontrolactivating)|当控件处于活动状态时调用。|  
|[CFileDialog::OnFileNameChange](#onfilenamechange)|处理`WM_NOTIFY CDN_SELCHANGE`消息。|  
|[CFileDialog::OnFileNameOK](#onfilenameok)|验证在对话框中输入的文件名。|  
|[CFileDialog::OnFolderChange](#onfolderchange)|处理`WM_NOTIFY CDN_FOLDERCHANGE`消息。|  
|[CFileDialog::OnInitDone](#oninitdone)|处理`WM_NOTIFY CDN_INITDONE`消息。|  
|[CFileDialog::OnItemSelected](#onitemselected)|在选择容器项时调用。|  
|[CFileDialog::OnLBSelChangedNotify](#onlbselchangednotify)|允许你在文件选择发生更改时执行自定义操作。|  
|[CFileDialog::OnShareViolation](#onshareviolation)|句柄共享冲突。|  
|[CFileDialog::OnTypeChange](#ontypechange)|处理`WM_NOTIFY CDN_TYPECHANGE`消息。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CFileDialog::m_ofn](#m_ofn)|Windows`OPENFILENAME`结构。 提供对基本的文件对话框的参数的访问。|  
  
## <a name="remarks"></a>备注  
 公共文件对话框使您可以实现的文件选择对话框中，例如，**打开的文件**和**另存为**，与 Windows 标准一致的方式。  
  
 您可以使用`CFileDialog`按原样提供，该构造函数也可以派生您自己的对话框类`CFileDialog`并编写一个构造函数来满足您的需要。 在任一情况下，这些对话框的行为将类似标准 MFC 对话框因为它们派生出[CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)。 `CFileDialog`依赖于 COMMDLG。Windows 中包含的 DLL 文件。  
  
 外观和功能的`CFileDialog`与[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]不同于早期版本的 Windows。 默认值`CFileDialog`会自动使用新[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]样式而无需代码更改，如果程序的编译和运行下的[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。 使用`bVistaStyle`构造函数来手动重写此自动更新中的参数。 自动更新的例外是自定义的对话框。 它们不会转换为新样式。 有关构造函数的详细信息，请参阅[CFileDialog::CFileDialog](#cfiledialog)。  
  
> [!NOTE]
>  控件 ID 系统不同之处在于[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]早期版本的 Windows 使用时从`CFileDialog`。 您必须更新所有引用`CFileDialog`代码之前可以移植你的项目从早期版本的 Windows 中的控件。  
  
 某些`CFileDialog`下不支持方法[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。 检查各个方法主题，了解有关是否支持该方法的信息。 此外，在下，不支持以下继承的函数[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]:  
  
- [CDialog::OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog)  
  
- [CDialog::OnSetFont](../../mfc/reference/cdialog-class.md#onsetfont)  
  
 Windows 消息`CFileDialog`根据正在使用哪些操作系统类可能有所不同。 例如，Windows XP 不支持[CDialog::OnCancel](../../mfc/reference/cdialog-class.md#oncancel)和[CDialog::OnOK](../../mfc/reference/cdialog-class.md#onok)为`CFileDialog`类。 但是，[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]确实支持它们。 有关不同，将生成的消息和接收它们的顺序的详细信息，请参阅[CFileDialog 示例︰ 日志记录事件的顺序](../../visual-cpp-samples.md)。  
  
 若要使用`CFileDialog`对象，请首先使用创建该对象`CFileDialog`构造函数。 在构造对话框中后，您可以设置或修改中的任何值[CFileDialog::m_ofn](#m_ofn)结构，以初始化值或固定大小的对话框控件的状态。 `m_ofn`结构属于类型`OPENFILENAME`。 有关详细信息，请参阅[OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 初始化对话框控件后，调用[CFileDialog::DoModal](#domodal)方法以显示对话框框中，以便用户可以键入的路径和文件名称。 `DoModal`返回用户单击确定 (IDOK) 或取消 (IDCANCEL) 按钮。 如果`DoModal`返回 IDOK，您可以使用之一`CFileDialog`公共成员函数来检索该信息将由用户。  
  
> [!NOTE]
>  在下[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]，多次调用[IFileDialog::SetFileTypes](http://msdn.microsoft.com/library/windows/desktop/bb775980)将导致错误。 第二次调用`SetFileTypes`的任何实例`CFileDialog`将返回`E_UNEXPECTED`中[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。 某些`CFileDialog`方法函数都调用`SetFileTypes`。 例如，两次调用`CFileDialog::DoModal`的相同实例`CFileDialog`生成[ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c)。  
  
 `CFileDialog`包括多个受保护的成员，您可以实现共享冲突、 文件名称验证和列表框中更改通知的自定义处理。 这些受保护的成员都是大多数应用程序无需使用，因为默认处理自动执行的回调函数。 这些函数的消息映射项不是必需的因为它们是标准的虚函数。  
  
 您可以使用 Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916)函数来确定在对话框中的初始化过程中是否发生了错误，以及若要了解有关错误的详细信息。  
  
 销毁`CFileDialog`自动处理对象。 无需调用[CDialog::EndDialog](../../mfc/reference/cdialog-class.md#enddialog)。  
  
 若要让用户选择多个文件，将设置`OFN_ALLOWMULTISELECT`标志调用之前`DoModal`。 您必须提供您自己文件名缓冲区以容纳返回的多个文件名的列表。 执行此操作通过替换`m_ofn.lpstrFile`用一个指针指向一个缓冲区你已分配之后您构造, `CFileDialog`，但在调用之前`DoModal`。  
  
 此外，您必须设置`m_ofn.nMaxFile`所指向的缓冲区中使用的字符数`m_ofn.lpstrFile`。 如果设置要向选定的文件的最大数目`n`，所需的缓冲区大小是`n * (_MAX_PATH + 1) + 1`。 在缓冲区中返回的第一项是文件已选中的文件夹的路径。 有关[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]-样式对话框框中，目录和文件名称字符串是以 null 终止的具有一个额外的 null 字符之后的最后一个文件名。 这种格式使资源管理器样式对话框，返回包含空格的长文件名。 对于旧式对话框中，由空格分隔的目录和文件名称字符串和该函数使用空格的文件名的短文件名。  
  
 下面的示例演示如何使用一个缓冲区来检索并列出多个文件的名称。  
  
 [!code-cpp[NVC_MFCFiles 第&23;](../../atl-mfc-shared/reference/codesnippet/cpp/cfiledialog-class_1.cpp)]  
  
 若要更改以响应用户选择多个文件名的缓冲区大小，必须派生新类从`CFileDialog`并重写[CFileDialog::OnFileNameChange](#onfilenamechange)方法。  
  
 如果派生新类从`CFileDialog`，可以使用消息映射来处理所有消息。 若要扩展的默认消息处理，从派生类`CFileDialog`、 将消息映射添加到新的类，并为新的消息提供成员函数。 无需提供挂钩函数，以自定义对话框。  
  
 要自定义对话框中，从派生类`CFileDialog`，提供自定义对话框模板，并添加一个消息映射来处理来自扩展控件的通知消息。 将任何未处理的消息传递给类的基类。 不需要自定义挂钩函数。  
  
 当您使用[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]样式`CFileDialog`，不能使用消息映射和对话框模板。 相反，您必须使用 COM 接口的类似的功能。  
  
 有关如何使用`CFileDialog`，请参阅[通用对话框类](../../mfc/common-dialog-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CFileDialog`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdlgs.h  
  
##  <a name="a-nameaddcheckbuttona--cfiledialogaddcheckbutton"></a><a name="addcheckbutton"></a>CFileDialog::AddCheckButton  
 向对话框中勾选按钮。  
  
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
 布尔值，该值指示检查按钮的当前状态。 `TRUE`如果选中，则`FALSE`否则为  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameaddcomboboxa--cfiledialogaddcombobox"></a><a name="addcombobox"></a>CFileDialog::AddComboBox  
 将组合框添加到对话框。  
  
```  
HRESULT AddComboBox(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 要添加的组合框的 ID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameaddcontrolitema--cfiledialogaddcontrolitem"></a><a name="addcontrolitem"></a>CFileDialog::AddControlItem  
 将项添加到对话框中的容器控件。  
  
```  
HRESULT AddControlItem(
    DWORD dwIDCtl,  
    DWORD dwIDItem,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 要将项添加到容器控件的 ID。  
  
 `dwIDItem`  
 项的 ID。  
  
 `strLabel`  
 项的文本。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameaddeditboxa--cfiledialogaddeditbox"></a><a name="addeditbox"></a>CFileDialog::AddEditBox  
 将一个编辑框添加到对话框。  
  
```  
HRESULT AddEditBox(
    DWORD dwIDCtl,  
    const CString& strText);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 要添加的编辑框的 ID。  
  
 `strText`  
 编辑框名称。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameaddmenua--cfiledialogaddmenu"></a><a name="addmenu"></a>CFileDialog::AddMenu  
 向对话框添加一个菜单。  
  
```  
HRESULT AddMenu(
    DWORD dwIDCtl,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 要添加菜单上的 ID。  
  
 `strLabel`  
 菜单名称。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameaddplacea--cfiledialogaddplace"></a><a name="addplace"></a>CFileDialog::AddPlace  
 将添加到列表中的文件夹将适用于用户打开或保存项目。  
  
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
 用于可提供给用户的文件夹路径。 这只能是一个文件夹。  
  
 `fdap`  
 指定该文件夹列表中的放置位置。  
  
 `psi`  
 表示将变得可向用户的文件夹 IShellItem 指向的指针。 这只能是一个文件夹。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameaddpushbuttona--cfiledialogaddpushbutton"></a><a name="addpushbutton"></a>CFileDialog::AddPushButton  
 为对话框中添加一个按钮。  
  
```  
HRESULT AddPushButton(
    DWORD dwIDCtl,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 要添加按钮的 ID。  
  
 `strLabel`  
 按钮名称。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameaddradiobuttonlista--cfiledialogaddradiobuttonlist"></a><a name="addradiobuttonlist"></a>CFileDialog::AddRadioButtonList  
 将选项按钮 （也称为单选按钮） 组添加到对话框。  
  
```  
HRESULT AddRadioButtonList(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 要添加的选项按钮组的 ID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameaddseparatora--cfiledialogaddseparator"></a><a name="addseparator"></a>CFileDialog::AddSeparator  
 向对话框添加分隔符。  
  
```  
HRESULT AddSeparator(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 添加分隔符的 ID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameaddtexta--cfiledialogaddtext"></a><a name="addtext"></a>CFileDialog::AddText  
 将文本添加到对话框。  
  
```  
HRESULT AddText(
    DWORD dwIDCtl,  
    const CString& strText);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 要添加的文本的 ID。  
  
 `strText`  
 文本名称中。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameapplyofntoshelldialoga--cfiledialogapplyofntoshelldialog"></a><a name="applyofntoshelldialog"></a>CFileDialog::ApplyOFNToShellDialog  
 更新的当前状态[CFileDialog](../../mfc/reference/cfiledialog-class.md)基于中存储的值`m_ofn`数据结构。  
  
```  
void ApplyOFNToShellDialog();
```  
  
### <a name="remarks"></a>备注  
 在之前的 Windows 版本[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]，该成员[OPENFILENAME](https://msdn.microsoft.com/library/ms911906.aspx)持续的状态同步数据结构`CFileDialog`。 对任何更改[m_ofn](#m_ofn)成员变量都立即反映在对话框中的状态。 此外，对对话框中的状态的任何更改立即更新`m_ofn`成员变量。  
  
 在[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]中的值`m_ofn`成员变量和状态`CFileDialog`不保证进行同步。 此函数会强制状态的`CFileDialog`更新以匹配`m_ofn`结构。 Windows 将调用此函数期间自动[CFileDialog::DoModal](#domodal)。  
  
 有关如何使用`CFileDialog`类下[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]，请参阅[CFileDialog 类](../../mfc/reference/cfiledialog-class.md)。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileDialog::UpdateOFNFromShellDialog](#updateofnfromshelldialog)。  
  
##  <a name="a-namecfiledialoga--cfiledialogcfiledialog"></a><a name="cfiledialog"></a>CFileDialog::CFileDialog  
 调用此函数来构造一个标准的 Windows 文件对话框。  
  
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
 指定哪种类型的对话框中，若要创建的参数。 将其设置为`TRUE`构造**文件打开**对话框。 将其设置为`FALSE`构造**文件另存为**对话框。  
  
 [in] `lpszDefExt`  
 默认的文件扩展名。 如果用户不在文件名中包括的已知的扩展 （一种具有关联用户的计算机上），指定的扩展`lpszDefExt`自动追加到文件的名称。 如果此参数为`NULL`，追加没有扩展名。  
  
 [in] `lpszFileName`  
 在文件名框中显示的初始文件名称。 如果`NULL`，任何初始文件名称将出现。  
  
 [in] `dwFlags`  
 可用于自定义对话框中的一个或多个标志的组合。 有关这些标志的说明，请参阅[OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 如果您修改`m_ofn.Flags`结构成员，请使用所做的更改中的按位 OR 运算符以保持默认行为不变。  
  
 [in] `lpszFilter`  
 指定筛选器的字符串对一系列可以应用到的文件。 如果指定文件筛选器，只有与筛选条件匹配的文件将出现在文件列表中。 请参阅有关如何使用文件筛选器的详细信息备注部分。  
  
 [in] `pParentWnd`  
 指向父窗口或所有者窗口的文件对话框中的指针。  
  
 [in] `dwSize`  
 大小`OPENFILENAME`结构。 此值取决于操作系统版本。 MFC 使用此参数来确定适当类型的对话框来创建 (例如，new[!INCLUDE[Win2kFamily](../../c-runtime-library/includes/win2kfamily_md.md)]对话框而不是 NT4 对话框)。 MFC 代码将确定要使用的正确对话框框大小的 0 表示的默认大小取决于在其运行该程序的操作系统版本。  
  
 [in] `bVistaStyle`  
 **请注意**此参数是可在 Visual Studio 2008 和更高版本，将会导致新样式对话框，以便仅当您在运行时，才使用[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]或更高版本。  
  
 此参数指定文件对话框的样式。 将其设置为`TRUE`以使用新的 Vista 样式文件对话框。 否则，将使用旧样式的对话框。 查看在 Vista 下运行的详细信息备注部分。  
  
### <a name="remarks"></a>备注  
 任一**文件打开**或**文件另存为**构造对话框时，具体取决于值`bOpenFileDialog`。  
  
 指定默认扩展插件使用`lpszDefExt`因为它是很少可预测有哪些扩展包含文件关联用户的计算机上可能不会产生您预期的行为。 如果您需要更好地控制追加默认扩展插件，可以派生您自己的类从`CFileDialog`，并重写`CFileDialog::OnFileNameOK`方法来执行您自己的扩展插件处理。  
  
 若要允许用户选择多个文件，将设置`OFN_ALLOWMULTISELECT`标志调用之前[DoModal](#domodal)。 您必须提供您自己文件名缓冲区来存储返回的多个文件名的列表。 执行此操作通过替换`m_ofn.lpstrFile`用一个指针指向一个缓冲区你已分配之后您构造, [CFileDialog](../../mfc/reference/cfiledialog-class.md)，但在调用之前`DoModal`。 此外，您必须设置`m_ofn.nMaxFile`指向的缓冲区中的字符数与`m_ofn.lpstrFile`。 如果设置要向选定的文件的最大数目`n`，必要的缓冲区大小是`n`*(_MAX_PATH + 1) + 1。 例如:   
  
 [!code-cpp[NVC_MFCFiles 第&23;](../../atl-mfc-shared/reference/codesnippet/cpp/cfiledialog-class_1.cpp)]  
  
 若要使用户能够通过使用鼠标或键盘来调整大小资源管理器样式对话框中，将设置`OFN_ENABLESIZING`标志。 将此标志设置是仅在提供的挂钩过程或自定义模板。 该标志仅适用于一个资源管理器样式的对话框;旧式对话框不能调整大小。  
  
 `lpszFilter`参数用于确定文件必须具有要显示在文件列表中的文件名称的类型。 字符串对中的第一个字符串描述该筛选器;第二个字符串指示要使用的文件扩展名。 可通过使用分号 （; 字符） 作为分隔符指定多个扩展名。 具有两个结尾的字符串 | 字符后, 跟`NULL`字符。 您还可以使用[CString](../../atl-mfc-shared/using-cstring.md)为此参数的对象。  
  
 例如，[!INCLUDE[ofprexcel](../../mfc/reference/includes/ofprexcel_md.md)]使用户可以打开具有扩展.xlc （图表） 或.xls （工作表），文件的其他项中。 Excel 的筛选器可以写成︰  
  
 [!code-cpp[NVC_MFCFiles #&24;](../../atl-mfc-shared/reference/codesnippet/cpp/cfiledialog-class_2.cpp)]  
  
 但是，如果您打算使用此字符串到直接更新`OPENFILENAME`结构中，您应当分隔您用空字符 \0'，而不是垂直图条的字符串 (|)。  
  
 `bVistaStyle`仅当下运行时，参数才适用[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。 在早期版本的 Windows，则忽略此参数。 如果`bVistaStyle`设置为`TRUE`，当编译的程序[!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)]或更高版本，将新的 Vista 样式**文件对话框**将使用。 否则为上一个 MFC 样式**文件对话框**将使用。  
  
 对话框模板不支持基于对话框上`bVistaStyle`  
  
### <a name="example"></a>示例  
  请参阅示例[CFileDialog::DoModal](#domodal)。  
  
##  <a name="a-namedomodala--cfiledialogdomodal"></a><a name="domodal"></a>CFileDialog::DoModal  
 调用此函数可显示 Windows 公共文件对话框，并让用户可以浏览文件和目录，然后输入一个文件名。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 **IDOK**或**IDCANCEL**。 如果**IDCANCEL**是返回，调用 Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916)函数来确定是否发生了错误。  
  
 **IDOK**和**IDCANCEL**是常数，指示用户是否选择了确定或取消按钮。  
  
### <a name="remarks"></a>备注  
 如果您想要通过设置的成员初始化的各种文件对话框中选项**m_ofn**结构中，应执行此操作，然后再调`DoModal`，但在构造对话框对象之后。  
  
 例如，如果您想要允许用户选择多个文件，将设置`OFN_ALLOWMULTISELECT`标志，然后再调`DoModal`，本主题中的代码示例中所示。  
  
 如果用户单击对话框中的确定或取消按钮或选择关闭选项从对话框中控件的菜单上，则将控制返回到您的应用程序。 您然后可以调用其他成员函数来设置或信息检索用户输入在对话框中。  
  
 `DoModal`函数是从类中重写虚函数`CDialog`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles #&25;](../../atl-mfc-shared/reference/codesnippet/cpp/cfiledialog-class_3.cpp)]  
  
##  <a name="a-nameenableopendropdowna--cfiledialogenableopendropdown"></a><a name="enableopendropdown"></a>CFileDialog::EnableOpenDropDown  
 允许在打开或保存在对话框的按钮的下拉列表。  
  
```  
HRESULT EnableOpenDropDown(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 下拉列表的 ID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameendvisualgroupa--cfiledialogendvisualgroup"></a><a name="endvisualgroup"></a>CFileDialog::EndVisualGroup  
 停止在添加到对话框中的可视化组元素。  
  
```  
HRESULT EndVisualGroup();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 S_OK 返回否则为一个错误值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetcheckbuttonstatea--cfiledialoggetcheckbuttonstate"></a><a name="getcheckbuttonstate"></a>CFileDialog::GetCheckButtonState  
 检索处于对话框中的复选按钮 （复选框） 的当前状态。  
  
```  
HRESULT GetCheckButtonState(
    DWORD dwIDCtl,  
    BOOL& bChecked);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 复选框的 ID。  
  
 `bChecked`  
 复选框的状态。 `TRUE`指示已选中;`FALSE`指示未选中。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetcontrolitemstatea--cfiledialoggetcontrolitemstate"></a><a name="getcontrolitemstate"></a>CFileDialog::GetControlItemState  
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
 对一个变量来接收多个值之一，该值指示控件的当前状态 CDCONTROLSTATE 枚举中的引用。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetcontrolstatea--cfiledialoggetcontrolstate"></a><a name="getcontrolstate"></a>CFileDialog::GetControlState  
 检索当前可见性，并启用某一给定控件的状态。  
  
```  
HRESULT GetControlState(
    DWORD dwIDCtl,  
    CDCONTROLSTATEF& dwState);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 控件的 ID。  
  
 `dwState`  
 对一个变量来接收从 CDCONTROLSTATE 枚举，该值指示控件的当前状态的一个或多个值的引用。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegeteditboxtexta--cfiledialoggeteditboxtext"></a><a name="geteditboxtext"></a>CFileDialog::GetEditBoxText  
 检索一个编辑框控件中的当前文本。  
  
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
  
##  <a name="a-namegetfileexta--cfiledialoggetfileext"></a><a name="getfileext"></a>CFileDialog::GetFileExt  
 调用此函数可检索与在对话框中输入的文件名的扩展名。  
  
```  
CString GetFileExt() const;  
```  
  
### <a name="return-value"></a>返回值  
 文件名的扩展名。  
  
### <a name="remarks"></a>备注  
 例如，如果输入的文件的名称是数据。TXT，`GetFileExt`返回"TXT"。  
  
 如果`m_ofn.Flags`具有`OFN_ALLOWMULTISELECT`标志设置，该字符串包含一系列以 null 结尾的字符串，其被选中，该文件组的目录路径的第一个字符串后面跟随用户选定的所有文件的名称。 若要检索文件的路径名，请使用[GetStartPosition](#getstartposition)和[GetNextPathName](#getnextpathname)成员函数。  
  
##  <a name="a-namegetfilenamea--cfiledialoggetfilename"></a><a name="getfilename"></a>CFileDialog::GetFileName  
 调用此函数可检索在该对话框中输入的文件名的名称。  
  
```  
CString GetFileName() const;  
```  
  
### <a name="return-value"></a>返回值  
 文件的名称。  
  
### <a name="remarks"></a>备注  
 文件的名称包含前缀和扩展插件。 例如，`GetFileName`将返回"TEXT。DAT"C:\FILES\TEXT.DAT 的文件。  
  
 如果`m_ofn.Flags`具有`OFN_ALLOWMULTISELECT`标志设置，应调用[GetStartPosition](#getstartposition)和[GetNextPathName](#getnextpathname)检索文件的路径名。  
  
##  <a name="a-namegetfiletitlea--cfiledialoggetfiletitle"></a><a name="getfiletitle"></a>CFileDialog::GetFileTitle  
 调用此函数可检索在该对话框中输入的文件的标题。  
  
```  
CString GetFileTitle() const;  
```  
  
### <a name="return-value"></a>返回值  
 该文件的标题。  
  
### <a name="remarks"></a>备注  
 文件的标题中包含只其前缀，而无需路径或扩展。 例如，`GetFileTitle`将返回文件 C:\FILES\TEXT.DAT"TEXT"。  
  
 如果`m_ofn.Flags`具有`OFN_ALLOWMULTISELECT`标志设置，该字符串包含一系列以 null 结尾的字符串，其被选中，该文件组的目录路径的第一个字符串后面跟随用户选定的所有文件的名称。 由于这个原因，使用[GetStartPosition](#getstartposition)和[GetNextPathName](#getnextpathname)成员函数以检索在列表中的下一个文件名。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileDialog::DoModal](#domodal)。  
  
##  <a name="a-namegetfolderpatha--cfiledialoggetfolderpath"></a><a name="getfolderpath"></a>CFileDialog::GetFolderPath  
 调用此成员函数可检索当前打开的文件夹或资源管理器样式打开或另存为的通用对话框的目录的路径。  
  
```  
CString GetFolderPath() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，它包含当前打开的文件夹或目录。  
  
### <a name="remarks"></a>备注  
 对话框中必须使用创建**OFN_EXPLORER**样式; 否则，该方法将失败，断言。  
  
 仅当显示对话框中，您可以调用此方法。 关闭该对话框后，此函数将不再起作用，并且该方法将失败与断言。  
  
##  <a name="a-namegetifiledialogcustomizea--cfiledialoggetifiledialogcustomize"></a><a name="getifiledialogcustomize"></a>CFileDialog::GetIFileDialogCustomize  
 检索到的内部 COM 对象的指针给定[CFileDialog](../../mfc/reference/cfiledialog-class.md)。  
  
```  
IFileDialogCustomize* GetIFileDialogCustomize();
```  
  
### <a name="return-value"></a>返回值  
 为内部的 COM 对象的指针`CFileDialog`。 它是您有责任正确释放该指针。  
  
### <a name="remarks"></a>备注  
 使用此函数仅在[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]对象具有与`bVistaStyle`设置为`true`。 如果您使用此函数时`bVistaStyle`是`false`，它将返回`NULL`在发布模式下和 throw 在调试模式下的断言。  
  
 有关详细信息`IFileDialogCustomize`接口，请参阅[IFileDialogCustomize](http://msdn.microsoft.com/library/windows/desktop/bb775912)。  
  
### <a name="example"></a>示例  
 此示例检索内部的 COM 对象。 若要运行此代码示例，您必须对其进行编译下[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。  
  
 [!code-cpp[NVC_MFC_CFileDialog #&4;](../../mfc/reference/codesnippet/cpp/cfiledialog-class_4.cpp)]  
  
##  <a name="a-namegetifileopendialoga--cfiledialoggetifileopendialog"></a><a name="getifileopendialog"></a>CFileDialog::GetIFileOpenDialog  
 检索到的内部 COM 对象的指针给定`CFileDialog`。  
  
```  
IFileOpenDialog* GetIFileOpenDialog();
```  
  
### <a name="return-value"></a>返回值  
 为内部的 COM 对象的指针`CFileDialog`。 它是您有责任正确释放该指针。  
  
### <a name="remarks"></a>备注  
 使用此函数仅在[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]对象具有与`bVistaStyle`设置为`true`。 此函数将返回`NULL`如果`CFileDialog`不是**打开**对话框或者，如果`bVistaStyle`设置为`false`。 在此最终的情况下，该函数只返回`NULL`以发布模式-在调试模式下，它将引发断言。  
  
 有关详细信息`IFileOpenDialog`接口，请参阅[IFileOpenDialog](http://msdn.microsoft.com/library/windows/desktop/bb775834)。  
  
### <a name="example"></a>示例  
 此示例检索内部的 COM 对象。 若要运行此代码，您必须对其进行编译下[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。  
  
 [!code-cpp[NVC_MFC_CFileDialog #&2;](../../mfc/reference/codesnippet/cpp/cfiledialog-class_5.cpp)]  
  
##  <a name="a-namegetifilesavedialoga--cfiledialoggetifilesavedialog"></a><a name="getifilesavedialog"></a>CFileDialog::GetIFileSaveDialog  
 检索到的内部 COM 对象的指针给定`CFileDialog`。  
  
```  
IFileSaveDialog* GetIFileSaveDialog();
```  
  
### <a name="return-value"></a>返回值  
 为内部的 COM 对象的指针`CFileDialog`。 它是您有责任正确释放该指针。  
  
### <a name="remarks"></a>备注  
 使用此函数仅在[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]对象具有与`bVistaStyle`设置为`true`。 此函数将返回`NULL`如果`CFileDialog`不是**保存**对话框或者，如果`bVistaStyle`设置为`false`。 在此最终的情况下，该函数只返回`NULL`以发布模式-在调试模式下，它将引发断言。  
  
 有关详细信息`IFileSaveDialog`接口，请参阅[IFileSaveDialog](http://msdn.microsoft.com/library/windows/desktop/bb775688)。  
  
### <a name="example"></a>示例  
 此示例检索内部的 COM 对象。 若要运行此代码示例，您必须对其进行编译下[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。  
  
 [!code-cpp[NVC_MFC_CFileDialog #&3;](../../mfc/reference/codesnippet/cpp/cfiledialog-class_6.cpp)]  
  
##  <a name="a-namegetnextpathnamea--cfiledialoggetnextpathname"></a><a name="getnextpathname"></a>CFileDialog::GetNextPathName  
 调用此函数可从在该对话框中所选组中检索下一个文件名称。  
  
```  
CString GetNextPathName(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 对引用**位置**返回先前值`GetNextPathName`或`GetStartPosition`函数调用。 **NULL**如果已到达列表的末尾。  
  
### <a name="return-value"></a>返回值  
 文件的完整路径。  
  
### <a name="remarks"></a>备注  
 文件名的路径包括文件的标题以及整个目录路径。 例如，`GetNextPathName`将返回"C:\FILES\TEXT。DAT"C:\FILES\TEXT.DAT 的文件。 您可以使用`GetNextPathName`在向前迭代循环中，如果您建立的初始位置，通过调用`GetStartPosition`。  
  
 如果只有一个文件包含所选内容，将返回该文件的名称。  
  
##  <a name="a-namegetofna--cfiledialoggetofn"></a><a name="getofn"></a>CFileDialog::GetOFN  
 检索关联**OPENFILENAME**结构。  
  
```  
const OPENFILENAME& GetOFN() const;  
  
OPENFILENAME& GetOFN();
```  
  
### <a name="return-value"></a>返回值  
 [OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839)结构。  
  
### <a name="remarks"></a>备注  
 使用此函数的第二个版本来初始化的外观**文件打开**或**文件另存为**构造它之后，但它显示为带之前对话框`DoModal`成员函数。 例如，您可以设置**lpstrTitle**的成员**m_ofn**想对话框中，具有到链接的标题。  
  
##  <a name="a-namegetpathnamea--cfiledialoggetpathname"></a><a name="getpathname"></a>CFileDialog::GetPathName  
 调用此函数可检索在该对话框中输入的文件的完整路径。  
  
```  
CString GetPathName() const;  
```  
  
### <a name="return-value"></a>返回值  
 文件的完整路径。  
  
### <a name="remarks"></a>备注  
 文件名的路径包括文件的标题以及整个目录路径。 例如，`GetPathName`将返回"C:\FILES\TEXT。DAT"C:\FILES\TEXT.DAT 的文件。  
  
 如果`m_ofn.Flags`具有`OFN_ALLOWMULTISELECT`标志设置，该字符串包含一系列的 null teminated 被选中，该文件组的目录路径的第一个字符串的字符串后, 跟由用户选择的所有文件的名称。 由于这个原因，使用[GetStartPosition](#getstartposition)和[GetNextPathName](#getnextpathname)成员函数以检索在列表中的下一个文件名。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileDialog::DoModal](#domodal)。  
  
##  <a name="a-namegetreadonlyprefa--cfiledialoggetreadonlypref"></a><a name="getreadonlypref"></a>CFileDialog::GetReadOnlyPref  
 调用此函数可确定是否已在 Windows 标准文件打开和文件另存为对话框框中选择了只读复选框。  
  
```  
BOOL GetReadOnlyPref() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零如果中对话框中的只读复选框处于选中状态，否则为 0。  
  
### <a name="remarks"></a>备注  
 可以通过设置隐藏只读复选框`OFN_HIDEREADONLY`设置中的样式`CFileDialog`构造函数。  
  
> [!NOTE]
> [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]样式`CFileDialog`对象不支持此函数。 尝试使用此函数[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]样式`CFileDialog`将引发[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。   
  
##  <a name="a-namegetresulta--cfiledialoggetresult"></a><a name="getresult"></a>CFileDialog::GetResult  
 检索在对话框中的用户所做的选择。  
  
```  
IShellItem* GetResult() throw();
```  
  
### <a name="return-value"></a>返回值  
 表示用户的选择 IShellItem 指向的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetresultsa--cfiledialoggetresults"></a><a name="getresults"></a>CFileDialog::GetResults  
 检索一个对话框，允许多个所选内容中的用户的选择。  
  
```  
IShellItemArray* GetResults() throw();
```  
  
### <a name="return-value"></a>返回值  
 可以通过其访问对话框中选定的项 IShellItemArray 指向的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetselectedcontrolitema--cfiledialoggetselectedcontrolitem"></a><a name="getselectedcontrolitem"></a>CFileDialog::GetSelectedControlItem  
 从对话框中的指定的容器控件中检索特定项。  
  
```  
HRESULT GetSelectedControlItem(
    DWORD dwIDCtl,  
    DWORD& dwIDItem);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 容器控件的 ID。  
  
 `dwIDItem`  
 用户控件中选定项的 ID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetstartpositiona--cfiledialoggetstartposition"></a><a name="getstartposition"></a>CFileDialog::GetStartPosition  
 如果调用该成员函数以检索在列表中，第一个文件路径名称的位置`m_ofn.Flags`具有`OFN_ALLOWMULTISELECT`标志设置。  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个**位置**可以用于迭代; 值**NULL**如果列表为空。  
  
##  <a name="a-namehidecontrola--cfiledialoghidecontrol"></a><a name="hidecontrol"></a>CFileDialog::HideControl  
 调用该成员函数以隐藏在资源管理器样式打开或另存为的通用对话框中指定的控件。  
  
```  
void HideControl(int nID);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 若要隐藏该控件的 ID。  
  
### <a name="remarks"></a>备注  
 对话框中必须使用创建**OFN_EXPLORER**样式; 否则，该函数将失败，出现一个断言。  
  
##  <a name="a-nameispickfoldersmodea--cfiledialogispickfoldersmode"></a><a name="ispickfoldersmode"></a>CFileDialog::IsPickFoldersMode  
 确定当前的对话框是否文件夹选取器模式下。  
  
```  
BOOL IsPickFoldersMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果对话框中为文件夹选取器模式;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namemofna--cfiledialogmofn"></a><a name="m_ofn"></a>CFileDialog::m_ofn  
 `m_ofn`是一种结构类型的`OPENFILENAME`。 此结构中的数据表示的当前状态`CFileDialog`。  
  
### <a name="remarks"></a>备注  
 使用此结构初始化的外观**文件打开**或**文件另存为**对话框中，在构造之后但在显示其与之前[DoModal](#domodal)方法。 例如，您可以设置`lpstrTitle`的成员`m_ofn`想对话框中，具有到链接的标题。  
  
 与[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]样式[CFileDialog](../../mfc/reference/cfiledialog-class.md)，`m_ofn`不能保证始终匹配对话框中的状态。 它将与在早期版本的 Windows 对话框中进行同步。 请参阅[CFileDialog::ApplyOFNToShellDialog](#applyofntoshelldialog)和[CFileDialog::UpdateOFNFromShellDialog](#updateofnfromshelldialog)有关同步的详细信息`m_ofn`结构和`CFileDialog`状态下[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。  
  
 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]样式的文件对话框不支持某些成员和标志`CFileDialog`。 因此，这些将不起作用。  
  
 下面是不支持的成员的列表[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]:  
  
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
  
-   OFN_LONGNAMES-始终有效地在中[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]  
  
-   中有效地始终关闭 OFN_NOLONGNAMES-[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]  
  
-   OFN_NONETWORKBUTTON-始终有效地在中[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]  
  
-   OFN_READONLY  
  
-   OFN_SHOWHELP  
  
 有关此结构的详细信息，请参阅[OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namemakeprominenta--cfiledialogmakeprominent"></a><a name="makeprominent"></a>CFileDialog::MakeProminent  
 位置对话框中的控件，以便突出显示相比于其他控件。  
  
```  
HRESULT MakeProminent(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 控件的 ID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameonbuttonclickeda--cfiledialogonbuttonclicked"></a><a name="onbuttonclicked"></a>CFileDialog::OnButtonClicked  
 单击该按钮时调用。  
  
```  
virtual void OnButtonClicked(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 按钮的 ID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameoncheckbuttontoggleda--cfiledialogoncheckbuttontoggled"></a><a name="oncheckbuttontoggled"></a>CFileDialog::OnCheckButtonToggled  
 选中或取消选中该复选框时调用。  
  
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
  
##  <a name="a-nameoncontrolactivatinga--cfiledialogoncontrolactivating"></a><a name="oncontrolactivating"></a>CFileDialog::OnControlActivating  
 激活控件时调用。  
  
```  
virtual void OnControlActivating(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 控件的 ID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameonfilenamechangea--cfiledialogonfilenamechange"></a><a name="onfilenamechange"></a>CFileDialog::OnFileNameChange  
 重写此方法，如果你想要处理`WM_NOTIFY``CDN_SELCHANGE`消息。  
  
```  
virtual void OnFileNameChange();
```  
  
### <a name="remarks"></a>备注  
 系统发送`CDN_SELCHANGE`时用户选择新文件或文件夹中的文件列表消息**打开**或**另存为**对话框。 如果你想要在响应此消息中执行任何操作，重写此方法。  
  
 仅当启用了 OFN_EXPLORER 标记创建对话框中，系统将发送此消息。 有关通知的详细信息，请参阅[CDN_SELCHANGE](http://msdn.microsoft.com/library/windows/desktop/ms646865)。 有关 OFN_EXPLORER 标志的信息，请参阅[OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839)结构和[打开和保存为对话框](http://msdn.microsoft.com/library/windows/desktop/ms646960)。  
  
##  <a name="a-nameonfilenameoka--cfiledialogonfilenameok"></a><a name="onfilenameok"></a>CFileDialog::OnFileNameOK  
 仅当您想要提供自定义验证的文件名的输入到公共文件对话框中，重写此函数。  
  
```  
virtual BOOL OnFileNameOK();
```  
  
### <a name="return-value"></a>返回值  
 文件名不是有效的文件名; 如果为 1否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数允许您为特定于应用程序由于某种原因拒绝文件名。 通常情况下，不需要使用此函数，因为框架提供的文件名的默认验证并显示一个消息框，如果输入无效的文件名。  
  
 如果返回 1，对话框中将仍显示用户无法输入另一个文件名。 对话框过程解除对话框中，如果返回为 0。 其他非零返回值是当前保留的并且不应使用。  
  
##  <a name="a-nameonfolderchangea--cfiledialogonfolderchange"></a><a name="onfolderchange"></a>CFileDialog::OnFolderChange  
 重写此函数来处理**WM_NOTIFYCDN_FOLDERCHANGE**消息。  
  
```  
virtual void OnFolderChange();
```  
  
### <a name="remarks"></a>备注  
 在打开或另存为对话框中打开一个新的文件夹时发送通知消息。  
  
 仅当对话框中创建使用 OFN_EXPLORER 样式，则会发送通知。 有关通知的详细信息，请参阅[CDN_FOLDERCHANGE](http://msdn.microsoft.com/library/windows/desktop/ms646859)。 OFN_EXPLORER 的样式有关的信息，请参阅[OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839)结构和[打开和保存为对话框](http://msdn.microsoft.com/library/windows/desktop/ms646960)。  
  
##  <a name="a-nameoninitdonea--cfiledialogoninitdone"></a><a name="oninitdone"></a>CFileDialog::OnInitDone  
 重写此函数来处理`WM_NOTIFY``CDN_INITDONE`消息。  
  
```  
virtual void OnInitDone();
```  
  
### <a name="remarks"></a>备注  
 在上排列控件完成系统时，系统将发送此通知消息**打开**或**另存为**对话框中，以便腾出空间供子对话框中的控件。  
  
 系统将此发送仅当对话框中创建使用 OFN_EXPLORER 样式。 有关通知的详细信息，请参阅[CDN_INITDONE](http://msdn.microsoft.com/library/windows/desktop/ms646863)。 OFN_EXPLORER 的样式有关的信息，请参阅[OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839)结构和[打开和保存为对话框](http://msdn.microsoft.com/library/windows/desktop/ms646960)。  
  
> [!NOTE]
> [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]样式的文件对话框不支持此功能。 尝试使用此函数[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]样式文件对话框将引发[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。 
  
##  <a name="a-nameonitemselecteda--cfiledialogonitemselected"></a><a name="onitemselected"></a>CFileDialog::OnItemSelected  
 选择容器项时调用。  
  
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
  
##  <a name="a-nameonlbselchangednotifya--cfiledialogonlbselchangednotify"></a><a name="onlbselchangednotify"></a>CFileDialog::OnLBSelChangedNotify  
 要更改的列表框中的当前所选内容时，调用此函数。  
  
```  
virtual void OnLBSelChangedNotify(
    UINT nIDBox,  
    UINT iCurSel,  
    UINT nCode);
```  
  
### <a name="parameters"></a>参数  
 *nIDBox*  
 列表框或组合框发生所选内容的 ID。  
  
 `iCurSel`  
 当前选定项的索引。  
  
 `nCode`  
 控件通知代码。 此参数必须具有下列值之一︰  
  
- **CD_LBSELCHANGE**指定`iCurSel`是单项选择列表框中选定的项。  
  
- **CD_LBSELSUB**指定`iCurSel`多选列表框中不再被选中。  
  
- **CD_LBSELADD**指定`iCurSel`多选列表框中选择。  
  
- **CD_LBSELNOITEMS**未选择任何内容存在于多选列表框中指定。  
  
### <a name="remarks"></a>备注  
 重写此函数可提供自定义的处理操作的选择列表框中会有所变化。 例如，可以使用此函数以显示的访问权限或日期的上次修改每个文件的用户选择。  
  
##  <a name="a-nameonshareviolationa--cfiledialogonshareviolation"></a><a name="onshareviolation"></a>CFileDialog::OnShareViolation  
 重写此函数可提供共享冲突的自定义处理。  
  
```  
virtual UINT OnShareViolation(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>参数  
 `lpszPathName`  
 发生共享冲突文件的路径。  
  
### <a name="return-value"></a>返回值  
 以下值之一：  
  
- **OFN_SHAREFALLTHROUGH**从对话框返回文件名。  
  
- **OFN_SHARENOWARN**需要采取任何进一步的操作。  
  
- **OFN_SHAREWARN**用户会收到此错误的标准警告消息。  
  
### <a name="remarks"></a>备注  
 通常情况下，不需要使用此函数，因为框架提供了默认共享冲突进行检查，并显示一个消息框，如果发生共享冲突。  
  
 如果你想要禁用共享冲突检查，使用按位 OR 运算符组合标志**OFN_SHAREAWARE**与`m_ofn.Flags`。  
  
##  <a name="a-nameontypechangea--cfiledialogontypechange"></a><a name="ontypechange"></a>CFileDialog::OnTypeChange  
 重写此函数来处理**WM_NOTIFYCDN_TYPECHANGE**消息。  
  
```  
virtual void OnTypeChange();
```  
  
### <a name="remarks"></a>备注  
 当用户选择从列表中打开的文件类型的新文件类型或另存为对话框发送通知消息。  
  
 仅当对话框中创建使用 OFN_EXPLORER 样式，则会发送通知。 有关通知的详细信息，请参阅[CDN_TYPECHANGE](http://msdn.microsoft.com/library/windows/desktop/ms646868)。 OFN_EXPLORER 的样式有关的信息，请参阅[OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839)结构和[打开和保存为对话框](http://msdn.microsoft.com/library/windows/desktop/ms646960)。  
  
##  <a name="a-nameremovecontrolitema--cfiledialogremovecontrolitem"></a><a name="removecontrolitem"></a>CFileDialog::RemoveControlItem  
 在对话框中的容器控件中移除的项。  
  
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
  
##  <a name="a-namesetcheckbuttonstatea--cfiledialogsetcheckbuttonstate"></a><a name="setcheckbuttonstate"></a>CFileDialog::SetCheckButtonState  
 在对话框中设置复选按钮 （复选框） 的当前的状态。  
  
```  
HRESULT SetCheckButtonState(
    DWORD dwIDCtl,  
    BOOL bChecked);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 复选框的 ID。  
  
 `bChecked`  
 复选框的状态。 `TRUE`指示已选中;`FALSE`指示选中此项。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesetcontrolitemstatea--cfiledialogsetcontrolitemstate"></a><a name="setcontrolitemstate"></a>CFileDialog::SetControlItemState  
 在对话框中找到的容器控件中设置某一项的当前状态。  
  
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
 一个或多个值从 CDCONTROLSTATE 枚举，用于指示该控件的新状态。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesetcontrolitemtexta--cfiledialogsetcontrolitemtext"></a><a name="setcontrolitemtext"></a>CFileDialog::SetControlItemText  
 设置控件项的文本。 例如，通常会显示单选按钮或菜单中的项的文本。  
  
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
  
##  <a name="a-namesetcontrollabela--cfiledialogsetcontrollabel"></a><a name="setcontrollabel"></a>CFileDialog::SetControlLabel  
 设置与控件，例如，按钮文本或编辑框标签关联的文本。  
  
```  
HRESULT SetControlLabel(
    DWORD dwIDCtl,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 控件的 ID。  
  
 `strLabel`  
 控件的名称。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesetcontrolstatea--cfiledialogsetcontrolstate"></a><a name="setcontrolstate"></a>CFileDialog::SetControlState  
 设置当前的可见性和启用的给定控件的状态。  
  
```  
HRESULT SetControlState(
    DWORD dwIDCtl,  
    CDCONTROLSTATEF dwState);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 控件的 ID。  
  
 `dwState`  
 一个或多个值从 CDCONTROLSTATE 枚举，用于指示该控件的当前状态。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesetcontroltexta--cfiledialogsetcontroltext"></a><a name="setcontroltext"></a>CFileDialog::SetControlText  
 调用此方法可设置为指定的控件的文本中的资源管理器样式**打开**或**另存为**对话框。  
  
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
 要为其设置的文本控件的 ID。  
  
 [in] `lpsz`  
 指向包含要为控件设置文本的字符串的指针。  
  
### <a name="remarks"></a>备注  
 此函数的两个版本也适用于使用 Unicode 的应用程序。 但是，只有与 LPCSTR 类型版本是有效的应用程序使用[!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)]。  
  
 若要使用此方法，必须使用 OFN_EXPLORER 样式创建对话框。 否则，该函数将失败并断言。  
  
##  <a name="a-namesetdefexta--cfiledialogsetdefext"></a><a name="setdefext"></a>CFileDialog::SetDefExt  
 调用此函数可设置资源管理器样式打开或另存为的通用对话框中的默认文件扩展名。  
  
```  
void SetDefExt(LPCSTR lpsz);
```  
  
### <a name="parameters"></a>参数  
 `lpsz`  
 指向一个包含要用于对话框对象的默认扩展名字符串的指针。 此字符串必须包含一个句点 （.）。  
  
### <a name="remarks"></a>备注  
 对话框中必须使用创建**OFN_EXPLORER**样式; 否则，该函数将失败，出现一个断言。  
  
##  <a name="a-nameseteditboxtexta--cfiledialogseteditboxtext"></a><a name="seteditboxtext"></a>CFileDialog::SetEditBoxText  
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
  
##  <a name="a-namesetpropertiesa--cfiledialogsetproperties"></a><a name="setproperties"></a>CFileDialog::SetProperties  
 提供一个属性存储，它定义将默认值用于正在保存的项。  
  
```  
BOOL SetProperties(LPCWSTR lpszPropList);
```  
  
### <a name="parameters"></a>参数  
 `lpszPropList`  
 由“;”分隔的预定义的属性列表。 标志的列表，请参阅`Flags`部分[OPENFILENAME](http://msdn.microsoft.com/en-us/8cecfd45-f7c1-4f8d-81a0-4e7fecc3b104)。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesetselectedcontrolitema--cfiledialogsetselectedcontrolitem"></a><a name="setselectedcontrolitem"></a>CFileDialog::SetSelectedControlItem  
 选项按钮组或在对话框中找到一个组合框中设置特定项的选定的状态。  
  
```  
HRESULT SetSelectedControlItem(
    DWORD dwIDCtl,  
    DWORD dwIDItem);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 容器控件的 ID。  
  
 `dwIDItem`  
 用户控件中选定项的 ID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesettemplatea--cfiledialogsettemplate"></a><a name="settemplate"></a>CFileDialog::SetTemplate  
 设置的对话框模板[CFileDialog](../../mfc/reference/cfiledialog-class.md)对象。  
  
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
 资源管理器中包含的模板资源的 ID 号`CFileDialog`对象。 仅在使用此模板[!INCLUDE[WinNt4Family](../../mfc/reference/includes/winnt4family_md.md)]和更高版本、 Windows 95 和更高版本，或在没有 OFN_EXPLORER 样式时。  
  
 [in] `lpWin3ID`  
 包含非 Explorer 模板资源的名称`CFileDialog`对象。 在 Windows NT 3.51 或不存在 OFN_EXPLORER 样式时，仅使用此模板。  
  
 [in] `lpWin4ID`  
 包含资源管理器的模板资源的名称`CFileDialog`对象。 仅在使用此模板[!INCLUDE[WinNt4Family](../../mfc/reference/includes/winnt4family_md.md)]和更高版本、 Windows 95 和更高版本，或在没有 OFN_EXPLORER 样式时。  
  
### <a name="remarks"></a>备注  
 系统将使用指定的模板之一。 系统会确定要使用哪个模板根据 OFN_EXPLORER 样式和操作系统上运行该应用程序的状态。 通过指定一个非资源管理器和资源管理器样式模板，很容易就可以支持 Windows NT 3.51[!INCLUDE[WinNt4Family](../../mfc/reference/includes/winnt4family_md.md)]和更高版本和 Windows 95 和更高版本。  
  
> [!NOTE]
> [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]样式文件对话框不支持此功能。 尝试使用此函数[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]样式文件对话框中将引发[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。 一种替代方法是使用自定义的对话框。 有关使用自定义`CFileDialog`，请参阅[IFileDialogCustomize](http://msdn.microsoft.com/library/windows/desktop/bb775912)。  
  
##  <a name="a-namestartvisualgroupa--cfiledialogstartvisualgroup"></a><a name="startvisualgroup"></a>CFileDialog::StartVisualGroup  
 声明对话框中的可视化组。 向"添加"的任何方法的后续调用将这些元素添加到该组。  
  
```  
HRESULT StartVisualGroup(
    DWORD dwIDCtl,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>参数  
 `dwIDCtl`  
 可视的组的 ID。  
  
 `strLabel`  
 组名称。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameupdateofnfromshelldialoga--cfiledialogupdateofnfromshelldialog"></a><a name="updateofnfromshelldialog"></a>CFileDialog::UpdateOFNFromShellDialog  
 更新`m_ofn`的数据结构[CFileDialog](../../mfc/reference/cfiledialog-class.md)基于内部对象的当前状态。  
  
```  
void UpdateOFNFromShellDialog();
```  
  
### <a name="remarks"></a>备注  
 在之前的 Windows 版本[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]，该成员[OPENFILENAME](https://msdn.microsoft.com/library/ms911906.aspx)持续的状态同步数据结构`CFileDialog`。 对任何更改[m_ofn](#m_ofn)成员变量直接受影响对话框中的状态。 此外，对对话框中的状态的任何更改会立即更新 m_ofn 成员变量。  
  
 在[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]、`m_ofn`数据结构不会自动更新。 若要保证中的数据的准确性`m_ofn`成员变量中，应调用`UpdateOFNFromShellDialog`函数之前访问的数据。 Windows 将调用此函数会自动在处理期间[IFileDialog::OnFileOK](http://msdn.microsoft.com/library/windows/desktop/bb775879)。  
  
 有关如何使用`CFileDialog`类下[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]，请参阅[CFileDialog 类](../../mfc/reference/cfiledialog-class.md)。  
  
### <a name="example"></a>示例  
 此示例将更新`CFileDialog`之前显示它。 在更新前`m_ofn`成员变量中，我们需要以使其为对话框中的当前状态同步。  
  
 [!code-cpp[NVC_MFC_CFileDialog #&1;](../../mfc/reference/codesnippet/cpp/cfiledialog-class_7.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)


