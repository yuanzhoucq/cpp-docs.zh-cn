---
title: "TN022：标准命令实现 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.commands"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令, 标准"
  - "ID_APP_ABOUT 命令"
  - "ID_APP_EXIT 命令"
  - "ID_CONTEXT_HELP 命令"
  - "ID_DEFAULT_HELP 命令"
  - "ID_EDIT_CLEAR 命令"
  - "ID_EDIT_CLEAR_ALL 命令"
  - "ID_EDIT_COPY 命令"
  - "ID_EDIT_CUT 命令"
  - "ID_EDIT_FIND 命令"
  - "ID_EDIT_PASTE 命令"
  - "ID_EDIT_PASTE_LINK 命令"
  - "ID_EDIT_PASTE_SPECIAL 命令"
  - "ID_EDIT_REDO 命令"
  - "ID_EDIT_REPEAT 命令"
  - "ID_EDIT_REPLACE 命令"
  - "ID_EDIT_SELECT_ALL 命令"
  - "ID_EDIT_UNDO 命令"
  - "ID_FILE_CLOSE 命令"
  - "ID_FILE_NEW 命令"
  - "ID_FILE_OPEN 命令"
  - "ID_FILE_PAGE_SETUP 命令"
  - "ID_FILE_PRINT 命令"
  - "ID_FILE_PRINT_PREVIEW 命令"
  - "ID_FILE_PRINT_SETUP 命令"
  - "ID_FILE_SAVE 命令"
  - "ID_FILE_SAVE_AS 命令"
  - "ID_FILE_SAVE_COPY_AS 命令"
  - "ID_FILE_UPDATE 命令"
  - "ID_HELP 命令"
  - "ID_HELP_INDEX 命令"
  - "ID_HELP_USING 命令"
  - "ID_INDICATOR_CAPS 命令"
  - "ID_INDICATOR_EXT 命令"
  - "ID_INDICATOR_KANA 命令"
  - "ID_INDICATOR_NUM 命令"
  - "ID_INDICATOR_OVR 命令"
  - "ID_INDICATOR_REC 命令"
  - "ID_INDICATOR_SCRL 命令"
  - "ID_NEXT_PANE 命令"
  - "ID_OLE_EDIT_LINKS 命令"
  - "ID_OLE_INSERT_NEW 命令"
  - "ID_OLE_VERB_FIRST 命令"
  - "ID_PREV_PANE 命令"
  - "ID_VIEW_STATUS_BAR 命令"
  - "ID_VIEW_TOOLBAR 命令"
  - "ID_WINDOW_ARRANGE 命令"
  - "ID_WINDOW_CASCADE 命令"
  - "ID_WINDOW_NEW 命令"
  - "ID_WINDOW_SPLIT 命令"
  - "ID_WINDOW_TILE_HORZ 命令"
  - "ID_WINDOW_TILE_VERT 命令"
  - "标准命令"
  - "TN022"
ms.assetid: a7883b46-23f7-4870-ac3a-804aed9258b5
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# TN022：标准命令实现
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。  因此，某些过程和主题可能已过时或不正确。  要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 此注释说明 MFC 提供了的标准实现命令 2.0。  因为它描述用于的标准机制实现许多命令，首先读取 [技术说明 21](../mfc/tn021-command-and-message-routing.md)。  
  
 此说明 MFC 假定结构、API 和常用编程实践的知识。  文档以及仅使用未证明的“实现”API 进行描述。  这不是开始了解的功能安装或如何编程在 MFC。  Visual C\+\+ 参考一般信息和 API 文档有关的详细信息。  
  
## 问题  
 MFC 定义在头文件 AFXRES.H. 的许多标准命令 ID。  这些命令 Framework 支持的更改。  了解框架类在哪里和如何处理这些命令不仅将演示框架如何在内部工作，但提供有用有关自定义标准实现并指导您实现自己的命令处理程序的几种方法。  
  
## 此技术说明内容  
 每个命令 ID。两节中进行说明：  
  
-   标题：命令的目的 \(例如，**ID\_FILE\_SAVE**\) 后跟的命令 ID 的符号 \(例如，“保存当前文件”\) 由冒号分隔。  
  
-   类实现命令的一个或多个段落，描述，以及默认实现  
  
 大多数默认命令实现是事先设定框架中的基类消息映射。  具有显式连结的某些命令要求在派生类中实现。  这些已描述在“注释”下。  如果在 AppWizard 选择正确的选项，这些默认处理程序。将连接生成的主干应用程序。  
  
## 命名约定  
 标准命令执行简单的命名约定 \(也建议您使用。  大多数标准命令在标准排列应用程序的菜单栏中。  命令开头的符号以“标准弹出菜单名称”后面的 ID\_ 的，后跟菜单项的名称。  符号带有下划线的字符区分词义大写的。  对于没有标准的命令菜单项命名一个逻辑，该命令名是定义的以 ID\_“”\(例如，**ID\_NEXT\_PANE**。\)  
  
 我们应使用前缀“ID\_”指示旨在绑定到菜单项，工具栏按钮或其他命令用户界面对象的命令。  处理“ID\_”命令处理程序应使用 `ON_COMMAND`，并且命令机制 MFC 的 `ON_UPDATE_COMMAND_UI` 结构。  
  
 建议为后面没有跟命令结构不需要菜单特定代码启用和禁用了菜单项使用标准“IDM\_”前缀。  当然特定命令应是小型自 MFC 命令菜单按照结构数不但使命令处理程序更强大 \(因为这些工具栏的使用\)，但允许命令处理程序可重用代码。  
  
## ID 范围  
 有关详细信息参考 [技术说明 20](../mfc/tn020-id-naming-and-numbering-conventions.md) 在使用 MFC 中的 ID 范围。  
  
 标准 MFC 命令在范围 0xE000 内为 0xEFFF。  因为它们发生在库的将来版本，更改不要依靠特定值这些 ID。  
  
 应用程序应定义在其范围 0x8000 的命令。0xDFFF。  
  
## 标准命令 ID  
 对于每个命令 ID，可以在文件 PROMPTS.RC 找到的消息行命令提示字符串。  该菜单提示的字符串 ID 必须与命令 ID 的 .  
  
-   创建新 ID\_FILE\_NEW\/空文档。  
  
    > [!NOTE]
    >  必须连接到此 `CWinApp`派生的类启用此功能的消息映射。  
  
     `CWinApp::OnFileNew` 根据文档模板的数量在应用程序的不同实现此命令。  如果只有一个 `CDocTemplate`，`CWinApp::OnFileNew` 将创建一个类型的文档，以及相应的帧和视图类。  
  
     如果有多个 `CDocTemplate`，`CWinApp::OnFileNew` 将提示包含允许使用的文档类型自己的对话框 \(**AFX\_IDD\_NEWTYPEDLG**\) 用户选择。  选择的 `CDocTemplate` 用来创建文档。  
  
     `ID_FILE_NEW` 的公共自定义是提供文档类型不同和更图形的选择。  在这种情况下您在消息映射来实现您自己和 **CMyApp::OnFileNew** 放置它而不是 `CWinApp::OnFileNew`。  不需要调用基类实现。  
  
     `ID_FILE_NEW` 的其他常见自定义是为每种类型创建文档的单独的命令。  在这种情况下您应定义新的命令 ID，例如 ID\_FILE\_NEW\_CHART 和 ID\_FILE\_NEW\_SHEET。  
  
-   ID\_FILE\_OPEN 打开现有文档。  
  
    > [!NOTE]
    >  必须连接到此 `CWinApp`派生的类启用此功能的消息映射。  
  
     `CWinApp::OnFileOpen` 没有名为 **CWinApp::DoPromptFileName** 的一个非常简单实现后跟 `CWinApp::OpenDocumentFile` 的文件的文件或路径名打开。  `CWinApp` 实现标准 FileOpen 定期引发 **DoPromptFileName** 对话框并填充它与当前文档模板获取的文件扩展名。  
  
     `ID_FILE_OPEN` 的公共自定义为自定义 FileOpen 对话框或添加其他文件筛选器。  建议用来自定义这将替换默认实现用自己的 FileOpen 对话框，并调用的文件或路径名称的 `CWinApp::OpenDocumentFile`。  不需要调用基类。  
  
-   ID\_FILE\_CLOSE 关闭当前打开的文档。  
  
     调用**CDocument::OnFileClose** `CDocument::SaveModified` 提示用户保存文档，如果修改了然后调用 `OnCloseDocument`。  结束的任何逻辑，包括损坏文档，在例程 `OnCloseDocument` 完成。  
  
    > [!NOTE]
    >  **ID\_FILE\_CLOSE** 操作与 `WM_CLOSE` 或 **SC\_CLOSE** 消息系统命令发送到不同的文档框架窗口。  当这是显示文档的最后一帧，窗口关闭窗口将关闭文档。  关闭与 **ID\_FILE\_CLOSE** 的文档不仅将关闭文档，但下关闭显示文档的任何框架窗口。  
  
-   ID\_FILE\_SAVE 保存当前文件。  
  
     实现用于 **OnFileSave** 和 **OnFileSaveAs**使用的帮助器例程 **CDocument::DoSave**。  即如果您保存未在的文档 \(DllEntryPoint 没有路径名，则 FileNew\) 或从预保存只读文档读取 **OnFileSave** 逻辑，将像 **ID\_FILE\_SAVE\_AS** 命令并要求用户提供新的文件名。  打开文件并保存实际执行进程通过虚函数 `OnSaveDocument`完成。  
  
     有两种自 **ID\_FILE\_SAVE**定义常见原因。  对于不保存的文档，从用户界面中移除 **ID\_FILE\_SAVE** 菜单项和工具栏按钮。  还要确保错误文档 \(即从不调用 `CDocument::SetModifiedFlag`\)，而框架不会保存文档。  除磁盘文件以外，在保存对在某处的文档，请定义该操作的命令。  
  
     对于 `COleServerDoc`，**ID\_FILE\_SAVE** 用于保存文件 \(用于正常情况\) 文档和文件更新使用 \(用于嵌入的文档\)。  
  
     如果文档数据在单独的磁盘文件中，但是，您不希望使用默认 **CDocument** 实现序列化，则应重写 `CDocument::OnSaveDocument` 而不是 **OnFileSave**。  
  
-   ID\_FILE\_SAVE\_AS 保存当前文件在不同的文件名。下  
  
     **CDocument::OnFileSaveAs** 实现 **CDocument::DoSave** 使用 Helper 例程和 **OnFileSave**。  如果文档保存之前，**OnFileSaveAs** 没有文件名在命令处理正 **ID\_FILE\_SAVE**。  **COleServerDoc::OnFileSaveAs** 实现逻辑将常规数据文件或保存表示 OLE 对象的服务器文档嵌入其他应用程序作为独立的文件。  
  
     如果自 **ID\_FILE\_SAVE**定义逻辑，您可能希望的方式与自 **ID\_FILE\_SAVE\_AS** 定义或“另存为”操作可能不适用于文档。  如果不需要的，可从菜单栏移除菜单项。  
  
-   ID\_FILE\_SAVE\_COPY\_AS 副本保存当前文件以新的名称下。  
  
     **COleServerDoc::OnFileSaveCopyAs** 实现非常类似于 **CDocument::OnFileSaveAs**，除此之外，此文档对象不是“连接”到基础文件中 \<Import 保存之后。  即，如果“修改的内存中文档”，在“保存，修改仍为”之前。  此外，此命令不会影响存储的路径名或标题的效果在文档中。  
  
-   通知 ID\_FILE\_UPDATE 容器保存嵌入的文档。  
  
     `COleServerDoc::OnUpdateDocument` 实现 notifiies 容器应当保存嵌入。  容器然后调用相应的 OLE 嵌入 API 以保存对象。  
  
-   ID\_FILE\_PAGE\_SETUP 调用特定的页面设置\/布局对话框。  
  
     目前没有此对话框的标准，并且，框架没有此命令的默认实现。  
  
     如果您选择此命令实现，建议您使用此命令 ID.  
  
-   ID\_FILE\_PRINT\_SETUP 调用标准的打印对话框设置。  
  
    > [!NOTE]
    >  必须连接到此 `CWinApp`派生的类启用此功能的消息映射。  
  
     此调用命令允许用户自定义文档或至多至少全部文档的打印机和打印设置本应用程序中标准的打印对话框设置。  必须使用控制面板中更改整个系统的默认打印机设置。  
  
     `CWinApp::OnFilePrintSetup` 具有创建 `CPrintDialog` 对象并调用 **CWinApp::DoPrintDialog** 实现函数的一个非常简单实现。  它设置了应用程序默认打印机打印机设置。  
  
     此命令对自定义常用的是允许每文档打印机设置，应存储的文档，则保存。  若要执行应将 **CDocument** 类的消息映射处理程序创建 `CPrintDialog` 对象，将它初始化与适当的打印机的此特性 \(通常是 **hDevMode** 和 **hDevNames**\)，请调用 **CPrintDialog::DoModal,** 并保存更改的打印机设置。  对于一种可靠的实现，您应查看 **CWinApp::DoPrintDialog** 的实现用于检测错误，而且处理敏感默认跟踪和系统范围内打印机的 **CWinApp::UpdatePrinterSelection** 更改。  
  
-   当前文件的 ID\_FILE\_PRINT 标准输出  
  
    > [!NOTE]
    >  必须连接到此 `CView`派生的类启用此功能的消息映射。  
  
     此命令更加正确打印当前文件，或开始晒印方法，涉及调用标准的打印对话框和运行打印引擎。  
  
     **CView::OnFilePrint** 实现该命令和主要输出循环。  它调用虚 `CView::OnPreparePrinting` 为用户的提示。打印的对话框。  然后准备输出 DC 转到打印机，输出进度对话框引发 \(**AFX\_IDD\_PRINTDLG**\)，然后发送 `StartDoc` 转义打印机。  **CView::OnFilePrint** 还包含页主要面向打印循环。  对于每页，它将调用的 `CView::OnPrepareDC` 虚后跟 `StartPage` 转义并调用该页的虚拟 `CView::OnPrint`。  完成后，`CView::OnEndPrinting` 虚调用，并且，输出进度对话框关闭。  
  
     打印架构的 MFC 设计功能的打印和打印预览的多种不同方式。  您通常会发现各种 `CView` 重写函数足够用于分页面向打印所有任务。  对于使用的打印机。应用非分页只放置到输出，则查找需要替换 **ID\_FILE\_PRINT** 实现。  
  
-   ID\_FILE\_PRINT\_PREVIEW 输入当前文件的打印预览模式。  
  
    > [!NOTE]
    >  必须连接到此 `CView`派生的类启用此功能的消息映射。  
  
     **CView::OnFilePrintPreview** 通过调用文档的帮助器函数启动打印预览模式 **CView::DoPrintPreview**。  像 **OnFilePrint** 是打印循环的，主要引擎**CView::DoPrintPreview** 是打印预览循环的主要引擎。  
  
     打印预览操作可以自定义用各种方法通过将不同的参数传递到 **DoPrintPreview**。   参考 [技术说明 30](../mfc/tn030-customizing-printing-and-print-preview.md)，讨论某些打印预览详细信息以及如何自定义它。  
  
-   **ID\_FILE\_MRU\_FILE1**…**FILE16** 范围 MRU 文件的 `list`命令 ID。  
  
     **CWinApp::OnUpdateRecentFileMenu** 是一个使用 `ON_UPDATE_COMMAND_UI` 机制 \(更高级使用的更新命令用户界面处理程序。  在菜单资源，只需定义。ID **ID\_FILE\_MRU\_FILE1**的一个菜单项。  初始菜单项仍为禁用。  
  
     当增大 MRU 列表，更多菜单项添加到列表中。  `CWinApp` 实现标准默认为四最近使用的文件中标准限制。  通过调用具有更大或较小值更改默认的 `CWinApp::LoadStdProfileSettings`。  MRU 列表存储在应用程序的 .ini 文件。  列表在应用程序的 `InitInstance` 函数中调用 `LoadStdProfileSettings`和加载您是否保存，以便在应用程序退出时。  MRU 更新命令用户界面处理程序还会将绝对路径显示的相对路径。"文件"菜单。  
  
     **CWinApp::OnOpenRecentFile** 是执行实际命令的 `ON_COMMAND` 处理程序。  它从 MRU 列表获取文件名并调用 `CWinApp::OpenDocumentFile`，完成打开文件并更新 MRU 列出所有工作。  
  
     不建议使用此命令处理程序的自定义。  
  
-   ID\_EDIT\_CLEAR 清除当前选择  
  
     目前没有此命令的标准实现。  必须实现此每个 `CView`的派生类。  
  
     使用 `CEdit::Clear`中，`CEditView` 提供此命令的实现。  此外，如果不存在当前选择，命令被禁用。  
  
     如果您选择此命令实现，建议您使用此命令 ID.  
  
-   ID\_EDIT\_CLEAR\_ALL 清除整个文档。  
  
     目前没有此命令的标准实现。  必须实现此每个 `CView`的派生类。  
  
     如果您选择此命令实现，建议您使用此命令 ID.  有关示例实现参见 MFC 教程示例 [自由曲线](../top/visual-cpp-samples.md)。  
  
-   ID\_EDIT\_COPY将当前所选内容复制到剪贴板。  
  
     目前没有此命令的标准实现。  必须实现此每个 `CView`的派生类。  
  
     `CEditView` 提供此命令的实现，使用 `CEdit::Copy`，复制当前选择的文本。剪贴板用作 CF\_TEXT。  此外，如果不存在当前选择，命令被禁用。  
  
     如果您选择此命令实现，建议您使用此命令 ID.  
  
-   ID\_EDIT\_CUT将当前所选内容剪切到剪贴板。  
  
     目前没有此命令的标准实现。  必须实现此每个 `CView`的派生类。  
  
     `CEditView` 提供此命令的实现，使用 `CEdit::Cut`，剪切当前选择的文本。剪贴板用作 CF\_TEXT。  此外，如果不存在当前选择，命令被禁用。  
  
     如果您选择此命令实现，建议您使用此命令 ID.  
  
-   ID\_EDIT\_FIND 开始查找操作，生成无模式对话框的外观。  
  
     目前没有此命令的标准实现。  必须实现此每个 `CView`的派生类。  
  
     `CEditView` 提供此命令的实现，此实现调用 Helper 函数使用 **OnEditFindReplace**，并查找\/替换以前存储在私有变量中实现的设置。  `CFindReplaceDialog` 类用于管理的用户提示无模式对话框。  
  
     如果您选择此命令实现，建议您使用此命令 ID.  
  
-   ID\_EDIT\_PASTE 当前插入剪贴板的内容。  
  
     目前没有此命令的标准实现。  必须实现此每个 `CView`的派生类。  
  
     `CEditView` 提供此命令的实现，将替换选定的文本当前剪贴板数据使用 `CEdit::Paste`。  如果在，剪贴板的 **CF\_TEXT** 命令被禁用。  
  
     **COleClientDoc** 此为命令提供一个 UI 更新命令处理程序。  如果剪贴板不包含可嵌入的 OLE 项\/对象，命令将处于禁用状态。  您负责编写实际命令的处理程序可以执行实际内容。  如果 OLE 应用程序还可以将其他格式，您应提供视图或文档的更新命令用户界面处理程序 \(即的某处，在命令目标路由的 **COleClientDoc** 之前\)。  
  
     如果您选择此命令实现，建议您使用此命令 ID.  
  
     对于替换标准 OLE 实现，请使用 `COleClientItem::CanPaste`。  
  
-   ID\_EDIT\_PASTE\_LINK 从当前插入剪贴板内容的链接。  
  
     目前没有此命令的标准实现。  必须实现此每个 `CView`的派生类。  
  
     `COleDocument` 此为命令提供一个 UI 更新命令处理程序。  如果剪贴板不包含可链接的 OLE 项\/对象，命令将处于禁用状态。  您负责编写实际命令的处理程序可以执行实际内容。  如果 OLE 应用程序还可以将其他格式，您应提供视图或文档的更新命令用户界面处理程序 \(即的某处，在命令目标路由的  `COleDocument` 之前\)。  
  
     如果您选择此命令实现，建议您使用此命令 ID.  
  
     对于替换标准 OLE 实现，请使用 `COleClientItem::CanPasteLink`。  
  
-   ID\_EDIT\_PASTE\_SPECIAL 具有选项的当前插入剪贴板的内容。  
  
     目前没有此命令的标准实现。  必须实现此每个 `CView`的派生类。  MFC 不提供此对话框。  
  
     如果您选择此命令实现，建议您使用此命令 ID.  
  
-   ID\_EDIT\_REPEAT 重复上次操作。  
  
     目前没有此命令的标准实现。  必须实现此每个 `CView`的派生类。  
  
     `CEditView` 提供此命令的实现对于最后查找操作。  使用最后一个找到实现的私有变量。  如果找到，不能尝试，命令被禁用。  
  
     如果您选择此命令实现，建议您使用此命令 ID.  
  
-   ID\_EDIT\_REPLACE 开始替换操作，使无模式中替换"对话框。  
  
     目前没有此命令的标准实现。  必须实现此每个 `CView`的派生类。  
  
     `CEditView` 提供此命令的实现，此实现调用 Helper 函数使用 **OnEditFindReplace**，并查找\/替换以前存储在私有变量中实现的设置。  `CFindReplaceDialog` 类用于管理的用户提示无模式对话框。  
  
     如果您选择此命令实现，建议您使用此命令 ID.  
  
-   ID\_EDIT\_SELECT\_ALL 选择整个文档。  
  
     目前没有此命令的标准实现。  必须实现此每个 `CView`的派生类。  
  
     `CEditView` 提供此命令的实现，选择文档中的所有文本。  如果未选择，的文本命令被禁用。  
  
     如果您选择此命令实现，建议您使用此命令 ID.  
  
-   ID\_EDIT\_UNDO 撤消上一操作。  
  
     目前没有此命令的标准实现。  必须实现此每个 `CView`的派生类。  
  
     使用 `CEdit::Undo`中，`CEditView` 提供此命令的实现。  如果 `CEdit::CanUndo` 返回错误，命令被禁用。  
  
     如果您选择此命令实现，建议您使用此命令 ID.  
  
-   ID\_EDIT\_REDO 重做次操作。  
  
     目前没有此命令的标准实现。  必须实现此每个 `CView`的派生类。  
  
     如果您选择此命令实现，建议您使用此命令 ID.  
  
-   ID\_WINDOW\_NEW 打开活动文档的其他窗口。  
  
     **CMDIFrameWnd::OnWindowNew** 实现此功能强大的功能。使用当前文件的文档模板创建包含当前文档的其他视图中的其他帧。  
  
     与最多个文档界面 \(MDI\) \(MDI\) 窗口菜单命令，因此，如果不活动 MDI 子窗口，命令被禁用。  
  
     不建议使用此命令处理程序的自定义。  如果希望提供创建附加视图或框架窗口的命令，可能再好些发明自己的命令。  可以克隆从 **CMDIFrameWnd::OnWindowNew** 生成代码以及修改它以特定框架和显示设置的类。  
  
-   ID\_WINDOW\_ARRANGE 图标排列在 MDI 窗口的底部。  
  
     `CMDIFrameWnd` 实现中实现辅助函数 **OnMDIWindowCmd**的 MDI 此标准命令。  因此此帮助程序映射到命令 ID MDI 窗口消息，并且可共享的代码。  
  
     与\(MDI\) 窗口菜单命令，因此，如果不活动 MDI 子窗口，命令被禁用。  
  
     不建议使用此命令处理程序的自定义。  
  
-   ID\_WINDOW\_CASCADE 层叠窗口，使其重叠。  
  
     `CMDIFrameWnd` 实现中实现辅助函数 **OnMDIWindowCmd**的 MDI 此标准命令。  因此此帮助程序映射到命令 ID MDI 窗口消息，并且可共享的代码。  
  
     与\(MDI\) 窗口菜单命令，因此，如果不活动 MDI 子窗口，命令被禁用。  
  
     不建议使用此命令处理程序的自定义。  
  
-   ID\_WINDOW\_TILE\_HORZ 水平平铺窗口。  
  
     此命令在 `CMDIFrameWnd` 实现类似，**ID\_WINDOW\_CASCADE**，但不同的 MDI 窗口消息为操作使用。  
  
     则应挑选应用程序默认的平铺方向。  您可以通过更改“窗口平铺”菜单项的 ID 执行为 **ID\_WINDOW\_TILE\_HORZ** 或 **ID\_WINDOW\_TILE\_VERT**。  
  
-   ID\_WINDOW\_TILE\_VERT 垂直平铺窗口。  
  
     此命令在 `CMDIFrameWnd` 实现类似，**ID\_WINDOW\_CASCADE**，但不同的 MDI 窗口消息为操作使用。  
  
     则应挑选应用程序默认的平铺方向。  您可以通过更改“窗口平铺”菜单项的 ID 执行为 **ID\_WINDOW\_TILE\_HORZ** 或 **ID\_WINDOW\_TILE\_VERT**。  
  
-   ID\_WINDOW\_SPLIT 为拆分的键盘界面。  
  
     `CView` 处理 `CSplitterWnd` 实现使用此命令。  如果视图是拆分窗口的一部分，则此命令将委托给实现函数 `CSplitterWnd::DoKeyboardSplit`。  这将使得键盘用户或拆分 unsplit 拆分窗口的模式会将拆分器。  
  
     如果视图不在拆分，禁用此命令。  
  
     不建议使用此命令处理程序的自定义。  
  
-   ID\_APP\_ABOUT 调用对话框。  
  
     没有一应用程序的标准实现"关于"框。  默认 AppWizard 创建的应用程序将为应用程序创建一个自定义对话框类并使用它作为框。  AppWizard 还需要编写处理此命令并调用对话框的常用的命令处理程序。  
  
     您几乎总是实现此命令。  
  
-   ID\_APP\_EXIT   退出应用程序。  
  
     **CWinApp::OnAppExit** 通过将 `WM_CLOSE` 消息处理此命令添加到应用程序的主窗口。  标准关闭应用程序 \(错误的文件的提示等\) 由 `CFrameWnd` 实现处理。  
  
     不建议使用此命令处理程序的自定义。  `CWinApp::SaveAllModified` 或 `CFrameWnd` 结束的逻辑建议重写。  
  
     如果您选择此命令实现，建议您使用此命令 ID.  
  
-   列出 ID\_HELP\_INDEX 帮助主题从 .HLP 文件。  
  
    > [!NOTE]
    >  必须连接到此 `CWinApp`派生的类启用此功能的消息映射。  
  
     `CWinApp::OnHelpIndex`。通过调用 `CWinApp::WinHelp`处理此命令。  
  
     不建议使用此命令处理程序的自定义。  
  
-   ID\_HELP\_USING 显示帮助说明如何使用帮助。  
  
    > [!NOTE]
    >  必须连接到此 `CWinApp`派生的类启用此功能的消息映射。  
  
     `CWinApp::OnHelpUsing`。通过调用 `CWinApp::WinHelp`处理此命令。  
  
     不建议使用此命令处理程序的自定义。  
  
-   ID\_CONTEXT\_HELP 恩特斯 SHIFT\-F1 帮助模式。  
  
    > [!NOTE]
    >  必须连接到此 `CWinApp`派生的类启用此功能的消息映射。  
  
     `CWinApp::OnContextHelp` 通过设置帮助模式光标，输入一模式循环和等待用户选择窗口处理此命令获取帮助。   有关更多详细信息在" MFC 参考 [技术说明 28](../mfc/tn028-context-sensitive-help-support.md) 帮助实现。  
  
     不建议使用此命令处理程序的自定义。  
  
-   ID\_HELP 为在当前上下文的帮助  
  
    > [!NOTE]
    >  必须连接到此 `CWinApp`派生的类启用此功能的消息映射。  
  
     `CWinApp::OnHelp` 通过获取当前应用程序上下文的帮助上下文处理此命令。  此处理简单的" F1 帮助，消息框上的帮助等。   有关更多详细信息在" MFC 参考 [技术说明 28](../mfc/tn028-context-sensitive-help-support.md) 帮助实现。  
  
     不建议使用此命令处理程序的自定义。  
  
-   ID\_DEFAULT\_HELP 显示默认上下文的帮助  
  
    > [!NOTE]
    >  必须连接到此 `CWinApp`派生的类启用此功能的消息映射。  
  
     此命令映射通常为 `CWinApp::OnHelpIndex`。  
  
     可提供不同的命令处理默认程序帮助和帮助索引之间的差异是否需要。  
  
-   ID\_NEXT\_PANE 转到下窗格  
  
     `CView` 处理 `CSplitterWnd` 实现使用此命令。  如果视图是拆分窗口的一部分，则此命令将委托给实现函数**CSplitterWnd::OnNextPaneCmd.**。  这是移动活动视图移到在拆分的下一个窗格。  
  
     禁用此命令，则不在拆分视图或未转到的下一个窗格。  
  
     不建议使用此命令处理程序的自定义。  
  
-   ID\_PREV\_PANE 转到上窗格  
  
     `CView` 处理 `CSplitterWnd` 实现使用此命令。  如果视图是拆分窗口的一部分，则此命令将委托给实现函数**CSplitterWnd::OnNextPaneCmd.**。  这是移动活动视图移到在拆分的前一个窗格。  
  
     禁用此命令，则不在拆分视图或未转到的前一个窗格。  
  
     不建议使用此命令处理程序的自定义。  
  
-   ID\_OLE\_INSERT\_NEW 插入新的 OLE 对象  
  
     目前没有此命令的标准实现。  此 `CView`必须实现 \(插入新的 OLE 项\/对象的派生类在当前选择。  
  
     任何 OLE 客户端应用程序应执行此命令。  AppWizard，用 OLE 选项，将创建 **OnInsertObject** 的主干中视图类的实现必须完成。  
  
     为此命令的完整实现参见 MFC OLE 示例 [OCLIENT](../top/visual-cpp-samples.md) 示例。  
  
-   OLE ID\_OLE\_EDIT\_LINKS 编辑链接  
  
     `COleDocument` 处理此命令使用 MFC 提供的标准 OLE 链接对话框中实现。  此对话框的实现通过 `COleLinksDialog` 类访问。  如果文件不包含任何当前命令链接，禁用。  
  
     不建议使用此命令处理程序的自定义。  
  
-   之前的 ID\_OLE\_VERB\_FIRST… OLE 谓词的 ID 范围  
  
     `COleDocument` 对于当前选定 OLE 项的或对象支持的谓词中使用此命令 ID 范围。  这必须是范围，因为给定的 OLE 项\/对象类型可以支持零一个或多个自定义谓词。  在应用程序菜单，应具有 ID **ID\_OLE\_VERB\_FIRST**的菜单项。  当程序运行，菜单将更新为包含相应的谓词菜单。许多谓词的说明 \(或弹出菜单\)。  OLE 菜单的管理都由 `AfxOleSetEditMenu`处理，执行此命令的更新命令用户界面处理程序。  
  
     不处理的每显式命令处理程序的范围的命令 ID。  **COleDocument::OnCmdMsg** 重写捕获此范围的任何命令 ID，并将它们更改为从零开始的数字谓词并启动该谓词的服务器 \(使用 `COleClientItem::DoVerb`\)。  
  
     建议不使用自定义或使用此命令 ID 范围的其他使用方式。  
  
-   ID\_VIEW\_TOOLBAR 在打开和关闭之间切换工具栏  
  
     `CFrameWnd` 处理此命令和命令用户界面更新处理程序切换工具栏的可视状态。  工具栏必须是帧的子窗口使用 `AFX_IDW_TOOLBAR`子窗口的 ID。  命令处理程序生效。切换工具栏窗口的可见性。  `CFrameWnd::RecalcLayout` 在其新状态用于绘制使用工具栏的框架窗口。  当工具栏，可见时，该更新命令用户界面处理程序检查菜单项。  
  
     不建议使用此命令处理程序的自定义。  如果希望添加其他的工具栏，您将需要修改克隆和命令处理程序与命令更新 UI 此处理程序的命令。  
  
-   ID\_VIEW\_STATUS\_BAR 在打开和关闭之间切换状态栏  
  
     此命令在 `CFrameWnd` 实现类似，**ID\_VIEW\_TOOLBAR**，但使用不同的子窗口 ID \(**AFX\_IDW\_STATUS\_BAR**\)。  
  
## 更新命令处理程序  
 若干标准命令 ID 用作指示器在状态栏。  在应用程序空闲时间期间，使用这些相同的更新命令用户界面处理机制显示它们的当前视觉状态。  因为它们不能由用户 \(即选择不可以按下状态栏窗格\)，然后它没有意义具有这些命令 ID 的 `ON_COMMAND` 处理程序。  
  
-   **ID\_INDICATOR\_CAPS** :Caps Lock 指示符。  
  
-   **ID\_INDICATOR\_NUM** :NUM Lock 指示符。  
  
-   **ID\_INDICATOR\_SCRL** : SCRL lock 指示。  
  
-   **ID\_INDICATOR\_KANA** :KANA Lock 指示符 \(仅和对应于系统\)。  
  
 所有这三这些 **CFrameWnd::OnUpdateKeyIndicator**，使用命令 ID 映射到相应的虚拟键的实现帮助程序中实现。  常见实现启用或禁用 \(为禁用状态窗格没有文本\) \= `CCmdUI` 对象根据相应的虚拟键是否当前被锁定。  
  
 不建议使用此命令处理程序的自定义。  
  
-   **ID\_INDICATOR\_EXT : EXT**结束的选择指示符。  
  
-   **ID\_INDICATOR\_OVR : OV**和**R**罢工指示符。  
  
-   ording 指示器的**ID\_INDICATOR\_REC : REC**。  
  
 目前没有这些指示器的标准实现。  
  
 如果您选择实现这些指示器，建议在状态栏使用这些指示器 ID 和维护排序指示符 \(即此顺序：EXT，和，数字，SCRL，OVR，REC\)。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)