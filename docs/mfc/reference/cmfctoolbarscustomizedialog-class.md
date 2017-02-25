---
title: "CMFCToolBarsCustomizeDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCToolBarsCustomizeDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarsCustomizeDialog class"
ms.assetid: 78e2cddd-4f13-4097-afc3-1ad646a113f1
caps.latest.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 30
---
# CMFCToolBarsCustomizeDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用户能够自定义工具栏、菜单、键盘快捷键、用户定义的工具和视觉样式在应用程序的无模式对话框选项\([CPropertySheet Class](../../mfc/reference/cpropertysheet-class.md)）。  通常，用户访问此对话框可通过选择 **自定义** 从 **工具** 菜单。  
  
 **自定义** 对话框具有六个选项: **命令**、 **工具栏**、 **工具**、 **键盘**、 **菜单**和 **选项**。  
  
## 语法  
  
```  
class CMFCToolBarsCustomizeDialog : public CPropertySheet  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog](../Topic/CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog.md)|构造 `CMFCToolBarsCustomizeDialog` 对象。|  
|`CMFCToolBarsCustomizeDialog::~CMFCToolBarsCustomizeDialog`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddButton](../Topic/CMFCToolBarsCustomizeDialog::AddButton.md)|插入工具栏按钮。命令中列出在页的 **命令**|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddMenu](../Topic/CMFCToolBarsCustomizeDialog::AddMenu.md)|从资源加载一个菜单并调用 [CMFCToolBarsCustomizeDialog::AddMenuCommands](../Topic/CMFCToolBarsCustomizeDialog::AddMenuCommands.md) 添加到该菜单命令列出了 **命令** 页。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddMenuCommands](../Topic/CMFCToolBarsCustomizeDialog::AddMenuCommands.md)|从资源加载一个菜单并调用 [CMFCToolBarsCustomizeDialog::AddMenuCommands](../Topic/CMFCToolBarsCustomizeDialog::AddMenuCommands.md) 添加到该菜单命令列出了 **命令** 页。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddToolBar](../Topic/CMFCToolBarsCustomizeDialog::AddToolBar.md)|从资源加载的工具栏。  然后，以便在菜单的每个命令调用 [CMFCToolBarsCustomizeDialog::AddButton](../Topic/CMFCToolBarsCustomizeDialog::AddButton.md) 方法插入按钮在命令列表在 **命令** 页中指定的类别下。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::Create](../Topic/CMFCToolBarsCustomizeDialog::Create.md)|显示 **自定义项** 对话框。|  
|`CMFCToolBarsCustomizeDialog::EnableTools`|保留供将来使用。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars](../Topic/CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars.md)|使用 **自定义** 对话框，启用或禁用创建新工具栏。|  
|[CMFCToolBarsCustomizeDialog::FillAllCommandsList](../Topic/CMFCToolBarsCustomizeDialog::FillAllCommandsList.md)|填充命令的提供的 `CListBox` 对象在 **所有命令** 类别。|  
|[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](../Topic/CMFCToolBarsCustomizeDialog::FillCategoriesComboBox.md)|填充每个命令类的名称提供的 `CComboBox` 对象在 **自定义** 对话框中。|  
|[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](../Topic/CMFCToolBarsCustomizeDialog::FillCategoriesListBox.md)|填充每个命令类的名称提供的 `CListBox` 对象在 **自定义** 对话框中。|  
|[CMFCToolBarsCustomizeDialog::GetCommandName](../Topic/CMFCToolBarsCustomizeDialog::GetCommandName.md)|检索与特定命令ID的名称.|  
|[CMFCToolBarsCustomizeDialog::GetCountInCategory](../Topic/CMFCToolBarsCustomizeDialog::GetCountInCategory.md)|检索的项数。具有给定文本标签提供的列表。|  
|[CMFCToolBarsCustomizeDialog::GetFlags](../Topic/CMFCToolBarsCustomizeDialog::GetFlags.md)|检索设置标志影响对话框的行为。|  
|`CMFCToolBarsCustomizeDialog::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage](../Topic/CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage.md)|启动图像编辑器，以便用户可以自定义工具栏按钮或菜单项图标。|  
|[CMFCToolBarsCustomizeDialog::OnInitDialog](../Topic/CMFCToolBarsCustomizeDialog::OnInitDialog.md)|重写、属性表初始化。  （重写 [CPropertySheet::OnInitDialog](../Topic/CPropertySheet::OnInitDialog.md)。）|  
|[CMFCToolBarsCustomizeDialog::PostNcDestroy](../Topic/CMFCToolBarsCustomizeDialog::PostNcDestroy.md)|调用由结构，在销毁后窗口。  （重写 `CPropertySheet::PostNcDestroy`。）|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::RemoveButton](../Topic/CMFCToolBarsCustomizeDialog::RemoveButton.md)|移除按钮与指定的命令ID从指定的类，或从所有类别。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::RenameCategory](../Topic/CMFCToolBarsCustomizeDialog::RenameCategory.md)|对列表框的类别重命名 **命令** 的选项类别。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::ReplaceButton](../Topic/CMFCToolBarsCustomizeDialog::ReplaceButton.md)|用新工具栏按钮对象替换在命令列表的按钮。**命令** 可选的。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::SetUserCategory](../Topic/CMFCToolBarsCustomizeDialog::SetUserCategory.md)|添加一个类别。在 **命令** 选项将显示类别的列表。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::CheckToolsValidity](../Topic/CMFCToolBarsCustomizeDialog::CheckToolsValidity.md)|调用由框架确定用户定义的工具列表是否有效。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnAfterChangeTool](../Topic/CMFCToolBarsCustomizeDialog::OnAfterChangeTool.md)|调用由结构，当用户定义的工具更改的属性。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnAssignKey](../Topic/CMFCToolBarsCustomizeDialog::OnAssignKey.md)|确定指定的键盘快捷键是否可分配到事件。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnBeforeChangeTool](../Topic/CMFCToolBarsCustomizeDialog::OnBeforeChangeTool.md)|确定是否可以更改一个用户定义的工具。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnInitToolsPage](../Topic/CMFCToolBarsCustomizeDialog::OnInitToolsPage.md)|调用由框架，以便在用户选择时 **工具** 选项请求。|  
  
## 备注  
 若要显示 **自定义** 对话框中，创建一 `CMFCToolBarsCustomizeDialog` 对象并调用 [CMFCToolBarsCustomizeDialog::Create](../Topic/CMFCToolBarsCustomizeDialog::Create.md) 方法。  
  
 当 **自定义** 对话框处于活动状态时，应用程序将限制该用户添加到自定义项任务的特定模式下工作。  
  
## 示例  
 下面的示例在 `CMFCToolBarsCustomizeDialog` 选件类演示如何使用各种方法。  使用 **自定义** 对话框中，该示例演示如何替换列表框中的一个工具栏按钮在 **命令** 页的命令，使可以创建新工具栏和显示 **自定义项** 对话框。  此代码段是 [pocket IE演示示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/CPP/cmfctoolbarscustomizedialog-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 [CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)  
  
## 要求  
 **标头:** afxToolBarsCustomizeDialog.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CPropertySheet Class](../../mfc/reference/cpropertysheet-class.md)