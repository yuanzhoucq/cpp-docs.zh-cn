---
title: "演练：将控件置于工具栏上 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "自定义对话框, 添加控件"
  - "工具栏, 添加控件"
ms.assetid: 8fc94bdf-0da7-45d9-8bc4-52b7b1edf205
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# 演练：将控件置于工具栏上
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题介绍如何将一个包含Windows 控件到工具按钮添加到工具栏。  在MFC中，工具栏按钮必须由[CMFCToolBarButton Class](../mfc/reference/cmfctoolbarbutton-class.md)类派生，例如[CMFCToolBarComboBoxButton Class](../mfc/reference/cmfctoolbarcomboboxbutton-class.md), [CMFCToolBarEditBoxButton Class](../mfc/reference/cmfctoolbareditboxbutton-class.md), [CMFCDropDownToolbarButton Class](../mfc/reference/cmfcdropdowntoolbarbutton-class.md), 或者[CMFCToolBarMenuButton Class](../mfc/reference/cmfctoolbarmenubutton-class.md).  
  
## 向工具栏添加控件  
 若要将控件添加到工具栏，执行以下步骤：  
  
1.  在父级工具栏资源中为按钮保存虚拟资源ID。  有关在Visual Studio中使用工具栏编辑器创建按钮的更多信息，参见[Toolbar Editor](../mfc/toolbar-editor.md)主题。  
  
2.  在父工具栏的所有位图中保存工具栏图像 \(按钮图标\) 。  
  
3.  在消息处理程序中，`AFX_WM_RESETTOOLBAR`消息进程，做如下的：  
  
    1.  通过使用派生的`CMFCToolbarButton`类来构造按钮控件。  
  
    2.  使用 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)的新控件替换虚假按钮。  你可以在堆叠中构造按钮对象，因为`ReplaceButton`复制按钮对象并且维护这个复制对象。  
  
> [!NOTE]
>  如果在你的应用程序中激活了自定义，你需要在**定制**对话框的**工具栏**中找到**重置**按钮来重置工具栏。在你重新编译之后就可以在你的应用程序中看到更新后的控件。  工具栏的状态保存在Windows的注册表中，注册表信息会在应用程序启动时执行`ReplaceButton`方法后加载和供给使用。  
  
## 工具栏控件和自定义  
 **自定义**对话框的**命令**标签包含一个应用程序可用的命令列表。  默认情况下，**自定义**对处理应用程序菜单并且在每一个菜单分类下构建一组标准工具栏按钮。  为了保持工具栏工具提供的扩展功能，你必须在**自定义**对话框中使用自定义控件替换标准的工具栏按钮。  
  
 当你激活自定义时，使用[CMFCToolBarsCustomizeDialog Class](../mfc/reference/cmfctoolbarscustomizedialog-class.md)类的自定义句柄`OnViewCustomize`创建**自定义**对话框。  在你通过调用[CMFCToolBarsCustomizeDialog::Create](../Topic/CMFCToolBarsCustomizeDialog::Create.md)显示你的 **自定义**对话框之前，调用[CMFCToolBarsCustomizeDialog::ReplaceButton](../Topic/CMFCToolBarsCustomizeDialog::ReplaceButton.md)使用新控件替换标准按钮。  
  
## 示例：创建一个查找组合框  
 这个章节描述怎么创建一个出现在工具栏并且包含最近使用的搜索条目的`Find`组合框控件  用户可以在控件中输入一个字符串并按下进去键来搜索文档，或者按下撤销键来返回焦点到主框架。  这个示例假定文档在[CEditView Class](../mfc/reference/ceditview-class.md)衍生的视图中显示。  
  
### 创建查找控件  
 首先，创建`Find` 组合框控件。  
  
1.  向应用程序资源中添加按钮及其命令：  
  
    1.  在应用程序资源中，在你的应用程序中添加一个包含 `ID_EDIT_FIND`命令ID和任何和工具栏有关的位图到工具栏中。  
  
    2.  使用\_EDIT\_FIND命令ID创建一个新的菜单条目。  
  
    3.  给字符串表格添加一个新的字符串"Find the text\\nFind"并且分配一个 `ID_EDIT_FIND_COMBO`命令ID。  这个ID将作为`Find`组合框的命令ID。  
  
        > [!NOTE]
        >  因为`ID_EDIT_FIND`是由`CEditView`执行的一个标准命令。你不必为这个命令实现一个特殊的句柄。但是，必须为新命令 `ID_EDIT_FIND_COMBO`实习一个新到的处理程序。  
  
2.  创建从[CComboBox Class](../mfc/reference/ccombobox-class.md)衍生的新类`CFindComboBox`。  
  
3.  在 `CFindComboBox`类中重写`PreTranslateMessage`虚拟方法。  这个方法会激活组合框发送[WM\_KEYDOWN](http://msdn.microsoft.com/library/windows/desktop/ms646280)消息。  若要将焦点从导航栏返回到代码窗口，请按 ESC \(`VK_ESCAPE`\)键。  如过用户点击Enter \(`VK_ENTER`\)键，将会给窗口主框架发送一个包含`ID_EDIT_FIND_COMBO`命令ID的 `WM_COMMAND`消息。  
  
4.  为 `Find` 组合框按钮创建一个类，这是一个派生自 [CMFCToolBarComboBoxButton Class](../mfc/reference/cmfctoolbarcomboboxbutton-class.md) 的类。  在此示例中，它命名为`CFindComboButton`。  
  
5.  `CMFCToolbarComboBoxButton` 构造器带有三个参数：按钮命令ID，按钮图片索引，组合框样式。  设置这些参数如下所示：  
  
    1.  传递`ID_EDIT_FIND_COMBO`作为命令ID。  
  
    2.  使用[CCommandManager::GetCmdImage](http://msdn.microsoft.com/zh-cn/4094d08e-de74-4398-a483-76d27a742dca)包含`ID_EDIT_FIND`来包含图片索引。  
  
    3.  有关可用的组合框样式列表，请参见 [组合框样式](../mfc/reference/combo-box-styles.md)。  
  
6.  在 `CFindComboButton` 类中，重写 `CMFCToolbarComboBoxButton::CreateCombo` 方法。  这里你应该创建一个`CFindComboButton`对象并给他返回一个指针。  
  
7.  使用[IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md)宏来使组合按钮更持久。  工作区域管理器自动加载和保存Windows 注册表中的按钮状态。  
  
8.  在你的文档视图中实现`ID_EDIT_FIND_COMBO`处理程序。  使用[CMFCToolBar::GetCommandButtons](../Topic/CMFCToolBar::GetCommandButtons.md)和`ID_EDIT_FIND_COMBO` 来继承所有的`Find` 组合框按钮。  由于自定义项，可以有一个按钮的多个副本具有相同的命令 ID。  
  
9. 在ID\_EDIT\_FIND 消息处理程序`OnFind`中，使用[CMFCToolBar::IsLastCommandFromButton](../Topic/CMFCToolBar::IsLastCommandFromButton.md)来决定是否从`Find`组合框按钮发送查找命令。  如果是这样，找到该文本并添加搜索字符串到组合框。  
  
### 查找控件添加到主工具栏  
 若要添加组合框按钮到工具栏，请执行以下步骤：  
  
1.  在窗口主框架中实现`AFX_WM_RESETTOOLBAR`消息处理程序`OnToolbarReset`  
  
    > [!NOTE]
    >  框架将此信息添加到主框架窗口当 应用程序启动时工具栏初始化或者工具栏中自定义项时重新设置时。  在两种情况下，你必须使用传统的`Find`组合框按钮替换标准的工具栏按钮。  
  
2.  在`AFX_WM_RESETTOOLBAR`消息处理程序中，检查工具栏ID，就是`AFX_WM_RESETTOOLBAR`消息的`WPARAM`。  如果工具栏ID和包含`Find`组合框按钮的工具栏相同，调用[CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)来替换`Find`按钮\(也就是包含命令ID的按钮 `ID_EDIT_FIND)`包含一个`CFindComboButton`对象。  
  
    > [!NOTE]
    >  你可以在堆叠中构造`CFindComboBox` 对象，因为`ReplaceButton`复制按钮对象并且维护这个复制对象。  
  
### 添加查找控件绑定到自定义对话框  
 在自定义处理程序`OnViewCustomize`中，调用[CMFCToolBarsCustomizeDialog::ReplaceButton](../Topic/CMFCToolBarsCustomizeDialog::ReplaceButton.md) 来替换`Find`按钮\(也就是有命令ID的按钮 `ID_EDIT_FIND)`包含一个`CFindComboButton`对象。  
  
## 请参阅  
 [层次结构图](../mfc/hierarchy-chart.md)   
 [类](../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton Class](../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBarComboBoxButton Class](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCToolBarsCustomizeDialog Class](../mfc/reference/cmfctoolbarscustomizedialog-class.md)