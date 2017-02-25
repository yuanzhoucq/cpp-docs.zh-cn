---
title: "CFileDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFileDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFileDialog class"
  - "common file dialog boxes"
  - "对话框, common"
ms.assetid: fda4fd3c-08b8-4ce0-8e9d-7bab23f8c6c0
caps.latest.revision: 47
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 49
---
# CFileDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装为文件使用打开或文件保存操作的通用对话框。  
  
## 语法  
  
```  
class CFileDialog : public CCommonDialog  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CFileDialog::CFileDialog](../Topic/CFileDialog::CFileDialog.md)|构造 `CFileDialog` 对象。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CFileDialog::AddCheckButton](../Topic/CFileDialog::AddCheckButton.md)|添加一个检查按钮添加到对话框。|  
|[CFileDialog::AddComboBox](../Topic/CFileDialog::AddComboBox.md)|添加一个组合框添加到对话框。|  
|[CFileDialog::AddControlItem](../Topic/CFileDialog::AddControlItem.md)|添加一个项添加到对话框的容器控件。|  
|[CFileDialog::AddEditBox](../Topic/CFileDialog::AddEditBox.md)|添加一个编辑框添加到对话框。|  
|[CFileDialog::AddMenu](../Topic/CFileDialog::AddMenu.md)|添加一个菜单。对话框。|  
|[CFileDialog::AddPlace](../Topic/CFileDialog::AddPlace.md)|已重载。  添加文件夹到具有列出可供用户可以打开或保存项目。|  
|[CFileDialog::AddPushButton](../Topic/CFileDialog::AddPushButton.md)|将一个按钮添加到对话框。|  
|[CFileDialog::AddRadioButtonList](../Topic/CFileDialog::AddRadioButtonList.md)|添加一个选项键 \(也称作单选按钮\) 组添加到对话框。|  
|[CFileDialog::AddSeparator](../Topic/CFileDialog::AddSeparator.md)|添加一个分隔符到对话框。|  
|[CFileDialog::AddText](../Topic/CFileDialog::AddText.md)|添加文本内容添加到对话框。|  
|[CFileDialog::ApplyOFNToShellDialog](../Topic/CFileDialog::ApplyOFNToShellDialog.md)|更新 `CFileDialog` 的状态与 `m_ofn` 成员变量和标志存储的参数。|  
|[CFileDialog::DoModal](../Topic/CFileDialog::DoModal.md)|显示对话框并使用户进行选择。|  
|[CFileDialog::EnableOpenDropDown](../Topic/CFileDialog::EnableOpenDropDown.md)|在对话框中的 **打开** 或 **保存** 按钮将启用下拉列表。|  
|[CFileDialog::EndVisualGroup](../Topic/CFileDialog::EndVisualGroup.md)|停止元素的添加到对话的可视化组。|  
|[CFileDialog::GetCheckButtonState](../Topic/CFileDialog::GetCheckButtonState.md)|获取一个检查按钮 \(复选框\) 的当前状态。对话框。|  
|[CFileDialog::GetControlItemState](../Topic/CFileDialog::GetControlItemState.md)|获取一个项的当前状态在对话框中的容器控件的。|  
|[CFileDialog::GetControlState](../Topic/CFileDialog::GetControlState.md)|获取特定控件的当前可见性并启用状态。|  
|[CFileDialog::GetEditBoxText](../Topic/CFileDialog::GetEditBoxText.md)|获取在编辑框控件的当前文本。|  
|[CFileDialog::GetFileExt](../Topic/CFileDialog::GetFileExt.md)|返回选定的文件扩展名。|  
|[CFileDialog::GetFileName](../Topic/CFileDialog::GetFileName.md)|返回选定的文件的文件名。|  
|[CFileDialog::GetFileTitle](../Topic/CFileDialog::GetFileTitle.md)|返回选定的文件的标题。|  
|[CFileDialog::GetFolderPath](../Topic/CFileDialog::GetFolderPath.md)|检索当前打开的文件夹或目录的路径一资源管理器样式的 **打开** 或 **另存为** 通用对话框的。|  
|[CFileDialog::GetIFileDialogCustomize](../Topic/CFileDialog::GetIFileDialogCustomize.md)|检索自定义的 `CFileDialog` 对象的内部 COM 对象。|  
|[CFileDialog::GetIFileOpenDialog](../Topic/CFileDialog::GetIFileOpenDialog.md)|检索用作 **打开** 文件"对话框 `CFileDialog` 的内部 COM 对象。|  
|[CFileDialog::GetIFileSaveDialog](../Topic/CFileDialog::GetIFileSaveDialog.md)|检索用作 **保存** 文件"对话框 `CFileDialog` 的内部 COM 对象。|  
|[CFileDialog::GetNextPathName](../Topic/CFileDialog::GetNextPathName.md)|返回下选择的文件的完整路径。|  
|[CFileDialog::GetOFN](../Topic/CFileDialog::GetOFN.md)|检索 `CFileDialog` 对象的 `OPENFILENAME` 结构。|  
|[CFileDialog::GetPathName](../Topic/CFileDialog::GetPathName.md)|返回选定的文件的完整路径。|  
|[CFileDialog::GetReadOnlyPref](../Topic/CFileDialog::GetReadOnlyPref.md)|返回选定的文件的只读状态。|  
|[CFileDialog::GetResult](../Topic/CFileDialog::GetResult.md)|获取用户在对话框中做出的选择。|  
|[CFileDialog::GetResults](../Topic/CFileDialog::GetResults.md)|获取在允许多重选择的对话框中的选择。|  
|[CFileDialog::GetSelectedControlItem](../Topic/CFileDialog::GetSelectedControlItem.md)|从在对话框中指定的容器控件获取特定项目。|  
|[CFileDialog::GetStartPosition](../Topic/CFileDialog::GetStartPosition.md)|返回文件名的第一个元素的位置列表中。|  
|[CFileDialog::HideControl](../Topic/CFileDialog::HideControl.md)|在一资源管理器样式的 **打开** 或 **另存为** 通用对话框隐藏指定的控件。|  
|[CFileDialog::IsPickFoldersMode](../Topic/CFileDialog::IsPickFoldersMode.md)|是否在文件夹选择器模式确定当前对话框。|  
|[CFileDialog::MakeProminent](../Topic/CFileDialog::MakeProminent.md)|在对话框中放置一个控件，以便突出显示与其他添加的控件比较。|  
|[CFileDialog::RemoveControlItem](../Topic/CFileDialog::RemoveControlItem.md)|在对话框的容器控件移除项。|  
|[CFileDialog::SetCheckButtonState](../Topic/CFileDialog::SetCheckButtonState.md)|一个检查按钮 \(复选框\) 的当前状态。对话框。|  
|[CFileDialog::SetControlItemState](../Topic/CFileDialog::SetControlItemState.md)|设置一个项的当前状态在对话框中的容器控件的。|  
|[CFileDialog::SetControlItemText](../Topic/CFileDialog::SetControlItemText.md)|设置控件的项的文本。  例如，附带一个单选按钮或项目在菜单的文本。|  
|[CFileDialog::SetControlLabel](../Topic/CFileDialog::SetControlLabel.md)|将文本与一个控件，如按钮文本或编辑框标签。|  
|[CFileDialog::SetControlState](../Topic/CFileDialog::SetControlState.md)|设置特定控件的当前可见性并启用状态。|  
|[CFileDialog::SetControlText](../Topic/CFileDialog::SetControlText.md)|设置指定控件的文本在一资源管理器样式的 **打开** 或 **另存为** 通用对话框。|  
|[CFileDialog::SetDefExt](../Topic/CFileDialog::SetDefExt.md)|设置一资源管理器样式的 **打开** 或 **另存为** 通用对话框的默认文件扩展名。|  
|[CFileDialog::SetEditBoxText](../Topic/CFileDialog::SetEditBoxText.md)|设置在编辑框控件的当前文本。|  
|[CFileDialog::SetProperties](../Topic/CFileDialog::SetProperties.md)|提供定义为项目的默认保存的属性存储。|  
|[CFileDialog::SetSelectedControlItem](../Topic/CFileDialog::SetSelectedControlItem.md)|在选项按钮组中设置特定项目的选定状态或组合框在对话框中找到。|  
|[CFileDialog::SetTemplate](../Topic/CFileDialog::SetTemplate.md)|设置 `CFileDialog` 对象的对话框模板。|  
|[CFileDialog::StartVisualGroup](../Topic/CFileDialog::StartVisualGroup.md)|声明对话框的可视化组。  以后对任何“添加”方法将那些元素添加到此组。|  
|[CFileDialog::UpdateOFNFromShellDialog](../Topic/CFileDialog::UpdateOFNFromShellDialog.md)|更新在 `m_ofn` 成员变量存储的数据与文件对话框的当前状态。|  
  
### 受保护的方法  
  
|名称|描述|  
|--------|--------|  
|[CFileDialog::OnButtonClicked](../Topic/CFileDialog::OnButtonClicked.md)|调用，当单击该按钮。|  
|[CFileDialog::OnCheckButtonToggled](../Topic/CFileDialog::OnCheckButtonToggled.md)|调用，如果复选框处于选中\/取消选中。|  
|[CFileDialog::OnControlActivating](../Topic/CFileDialog::OnControlActivating.md)|调用，当控件处于活动状态。|  
|[CFileDialog::OnFileNameChange](../Topic/CFileDialog::OnFileNameChange.md)|处理 `WM_NOTIFY CDN_SELCHANGE` 消息。|  
|[CFileDialog::OnFileNameOK](../Topic/CFileDialog::OnFileNameOK.md)|验证在对话框中输入的文件名。|  
|[CFileDialog::OnFolderChange](../Topic/CFileDialog::OnFolderChange.md)|处理 `WM_NOTIFY CDN_FOLDERCHANGE` 消息。|  
|[CFileDialog::OnInitDone](../Topic/CFileDialog::OnInitDone.md)|处理 `WM_NOTIFY CDN_INITDONE` 消息。|  
|[CFileDialog::OnItemSelected](../Topic/CFileDialog::OnItemSelected.md)|调用，当容器选择项。|  
|[CFileDialog::OnLBSelChangedNotify](../Topic/CFileDialog::OnLBSelChangedNotify.md)|文件时，在选择发生更改时，可以执行自定义操作。|  
|[CFileDialog::OnShareViolation](../Topic/CFileDialog::OnShareViolation.md)|处理共享冲突。|  
|[CFileDialog::OnTypeChange](../Topic/CFileDialog::OnTypeChange.md)|处理 `WM_NOTIFY CDN_TYPECHANGE` 消息。|  
  
### 公共数据成员  
  
|名称|描述|  
|--------|--------|  
|[CFileDialog::m\_ofn](../Topic/CFileDialog::m_ofn.md)|Windows `OPENFILENAME` 结构。  提供对基本的文件对话框参数。|  
  
## 备注  
 常用文件对话框允许使用 Windows 标准一致的已实现文件选择对话框，例如，**打开文件** 和 **另存为**，有些。  
  
 可以使用 [CFileDialog](../../mfc/reference/cfiledialog-class.md) 使用提供的构造函数，也可从 `CFileDialog` 和写入派生自己的对话框选件类构造函数以满足您的要求。  在任何情况下，因为它们是从派生 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)，这些对话框中的行为与标准 MFC 对话框。  `CFileDialog` 依赖于 Windows 中包含的 COMMDLG.DLL 文件。  
  
 外观和 `CFileDialog` 的功能和 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] 与 Windows 的早期版本有所不同。  如果程序编译并运行在 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]下，默认值 `CFileDialog` 自动使用新 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] 样式，而无需代码更改。  使用 `bVistaStyle` 参数在构造函数中手动重写此自动更新。  对自动更新的例外情况是自定义对话框。  它们不会转换为新样式。  有关构造函数的更多信息，请参见 [CFileDialog::CFileDialog](../Topic/CFileDialog::CFileDialog.md)。  
  
> [!NOTE]
>  当您使用 `CFileDialog`时，控件 ID 系统在 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] 不同于 Windows 的早期版本。  然后才能端口需要从 Windows 之前，的早期版本的项目必须更新所有引用。`CFileDialog` 代码中的控件。  
  
 某些 `CFileDialog` 方法不支持在 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]下。  检查单个方法主题有关的信息方法是否支持。  此外，以下继承的功能不支持在 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]下：  
  
-   [CDialog::OnInitDialog](../Topic/CDialog::OnInitDialog.md)  
  
-   [CDialog::OnSetFont](../Topic/CDialog::OnSetFont.md)  
  
 `CFileDialog` 选件类的窗口消息会因什么操作系统使用。  例如，Windows XP 不支持 [CDialog::OnCancel](../Topic/CDialog::OnCancel.md) 和 [CDialog::OnOK](../Topic/CDialog::OnOK.md)`CFileDialog` 选件类的。  但是，[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] 支持它们。  有关生成和订单接收的不同消息的更多信息，请参见 [CFileDialog 示例：记录事件顺序](../../top/visual-cpp-samples.md)。  
  
 使用 `CFileDialog` 构造函数，若要使用 `CFileDialog` 对象，请首先创建对象。  在对话框中构造后，可以设置或修改在 [CFileDialog::m\_ofn](../Topic/CFileDialog::m_ofn.md) 结构中的所有值初始化对话框控件的值或状态。  `m_ofn` 机制是类型 `OPENFILENAME`。  有关更多信息，请参见中 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839) 结构。  
  
 在初始化对话框控件后，调用 [CFileDialog::DoModal](../Topic/CFileDialog::DoModal.md) 方法显示对话框，以便用户可以键入该路径和文件名。  `DoModal` 返回用户是否单击“确定” \(IDOK\) 或移除“取消” \(IDCANCEL\) 按钮。  如果 `DoModal` 返回 IDOK，您可以使用一个 `CFileDialog` 公共成员函数检索用户输入的信息。  
  
> [!NOTE]
>  在 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]下，多次调用 [IFileDialog::SetFileTypes](http://msdn.microsoft.com/library/windows/desktop/bb775980) 导致错误。  第二次调用 `CFileDialog` 的所有实例的 `SetFileTypes` 将返回在 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]的 `E_UNEXPECTED`。  某些 `CFileDialog` 方法函数调用 `SetFileTypes`。  例如，两个调用。`CFileDialog` 的同一实例的 `CFileDialog::DoModal` 生成 [断言](../Topic/ASSERT%20\(MFC\).md)。  
  
 `CFileDialog` 包含允许您执行自定义处理共享冲突、文件名验证和列表框更改通知的多个受保护的成员。  这些受保护成员是回调函数大多数应用程序不必使用，因为默认处理自动执行。  这些功能的消息映射项，因为它们是标准虚函数，则不需要。  
  
 可以使用 Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) 函数确定错误是否在对话框的初始化时生成并了解有关该错误。  
  
 `CFileDialog` 对象析构自动处理。  您不必调用 [CDialog::EndDialog](../Topic/CDialog::EndDialog.md)。  
  
 在调用 `DoModal`之前，若要允许用户选择的多个文件，请设置 `OFN_ALLOWMULTISELECT` 标志。  您必须提供自己的文件名缓冲区容纳返回的列表多文件的名称。  通过替换 `m_ofn.lpstrFile` 执行此操作。指针到分配的缓冲区，在构造 `CFileDialog`后，但，在调用 `DoModal`之前。  
  
 此外，还必须设置 `m_ofn.nMaxFile` 使用字符数缓冲区中的指向由 `m_ofn.lpstrFile`。  如果设置要选择的文件的最大数目。`n`，所需的缓冲区大小是 `n * (_MAX_PATH + 1) + 1`。  在缓冲区返回的第一项是路径为选定某个文件的文件夹。  对于 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]样式对话框中，目录和文件名字符串 Null 终止，带有额外的 null 字符在最后一个文件名之后。  此格式使资源管理器样式的对话框返回包含空格的长文件名。  对于旧式对话框中，目录和文件名字符串由空格分隔，并且该函数用于空间的文件名使用短文件名。  
  
 下面的示例演示如何使用缓冲检索和列出多文件的名称。  
  
 [!code-cpp[NVC_MFCFiles#23](../../mfc/codesnippet/CPP/cfiledialog-class_1.cpp)]  
  
 若要更改缓冲区大小以响应选择多个文件名称的用户，则必须从 `CFileDialog` 派生新选件类并重写 [CFileDialog::OnFileNameChange](../Topic/CFileDialog::OnFileNameChange.md) 方法。  
  
 如果从 `CFileDialog`派生新选件类，可以使用消息映射来处理所有消息。  若要扩展默认消息处理，从 `CFileDialog`派生选件类，添加消息映射到新选件类，并为新消息提供成员函数。  您不必提供挂钩函数自定义对话框。  
  
 若要自定义对话框，从 `CFileDialog`派生选件类，提供了一个自定义对话框模板，并将消息映射处理从扩展控件的通知消息。  通过任何未处理的消息给基类。  您不必自定义挂钩函数。  
  
 当您使用 `CFileDialog`的 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] 样式时，不能使用消息映射和对话框模板。  相反，您必须具有类似的功能使用 COM 接口。  
  
 有关如何使用 `CFileDialog`的更多信息，请参见[通用对话框类](../../mfc/common-dialog-classes.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CFileDialog`  
  
## 要求  
 **标头：** afxdlgs.h  
  
## 请参阅  
 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)