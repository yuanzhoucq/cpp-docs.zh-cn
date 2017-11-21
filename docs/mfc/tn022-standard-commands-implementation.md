---
title: "TN022： 标准命令实现 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.commands
dev_langs: C++
helpviewer_keywords:
- ID_PREV_PANE command [MFC]
- ID_APP_EXIT command [MFC]
- ID_NEXT_PANE command [MFC]
- ID_INDICATOR_REC command [MFC]
- ID_WINDOW_SPLIT command [MFC]
- ID_FILE_PRINT_PREVIEW command [MFC]
- ID_WINDOW_CASCADE command [MFC]
- ID_FILE_CLOSE command [MFC]
- ID_FILE_SAVE_COPY_AS command [MFC]
- ID_WINDOW_ARRANGE command [MFC]
- ID_EDIT_FIND command [MFC]
- ID_FILE_OPEN command [MFC]
- ID_FILE_PAGE_SETUP command [MFC]
- ID_OLE_VERB_FIRST command [MFC]
- ID_EDIT_UNDO command [MFC]
- ID_EDIT_CLEAR command [MFC]
- ID_INDICATOR_CAPS command [MFC]
- ID_HELP_INDEX command [MFC]
- commands [MFC], standard
- ID_FILE_PRINT_SETUP command [MFC]
- ID_DEFAULT_HELP command [MFC]
- ID_INDICATOR_SCRL command [MFC]
- ID_FILE_PRINT command [MFC]
- ID_INDICATOR_OVR command [MFC]
- ID_INDICATOR_KANA command [MFC]
- ID_EDIT_COPY command [MFC]
- ID_EDIT_REDO command [MFC]
- ID_EDIT_PASTE command [MFC]
- ID_OLE_INSERT_NEW command [MFC]
- ID_OLE_EDIT_LINKS command [MFC]
- ID_EDIT_PASTE_SPECIAL command [MFC]
- ID_INDICATOR_EXT command [MFC]
- ID_HELP_USING command [MFC]
- standard commands
- ID_VIEW_STATUS_BAR command [MFC]
- ID_FILE_SAVE_AS command [MFC]
- ID_EDIT_CLEAR_ALL command [MFC]
- ID_WINDOW_NEW command [MFC]
- ID_CONTEXT_HELP command [MFC]
- ID_EDIT_REPLACE command [MFC]
- ID_WINDOW_TILE_HORZ command [MFC]
- ID_APP_ABOUT command [MFC]
- TN022
- ID_VIEW_TOOLBAR command [MFC]
- ID_HELP command [MFC]
- ID_WINDOW_TILE_VERT command [MFC]
- ID_EDIT_CUT command [MFC]
- ID_FILE_UPDATE command [MFC]
- ID_EDIT_REPEAT command [MFC]
- ID_FILE_SAVE command [MFC]
- ID_EDIT_PASTE_LINK command [MFC]
- ID_EDIT_SELECT_ALL command [MFC]
- ID_FILE_NEW command [MFC]
- ID_INDICATOR_NUM command
ms.assetid: a7883b46-23f7-4870-ac3a-804aed9258b5
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3851cd7deff77c9703a11ee73ee1d9daa020c848
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="tn022-standard-commands-implementation"></a>TN022：标准命令实现
> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 此注释描述 MFC 2.0 提供的标准命令实现。 读取[技术说明 21](../mfc/tn021-command-and-message-routing.md)第一个因为它说明了用来实现的许多标准命令的机制。  
  
 此说明假定 MFC 体系结构、 Api，以及常见的编程做法的知识。 有案可稽以及未记录"实现仅"Api 进行了描述。 这不是学习有关的功能或如何在 MFC 中编程的开端。 有关更多常规信息和有关有案可稽的 Api 的详细信息，请参阅 Visual c + +。  
  
## <a name="the-problem"></a>问题  
 MFC 标头文件 AFXRES 中定义许多标准命令 Id。H。 这些命令的框架支持而异。 了解 framework 类在何处以及如何处理这些命令将仅显示你如何框架内部的工作方式，但将提供有关如何自定义的标准实现和教授几种技术来实现的有用信息你自己的命令处理程序。  
  
## <a name="contents-of-this-technical-note"></a>此技术说明的内容  
 每个命令 ID 是两个部分中所述：  
  
-   标题： 的符号名称的命令 ID (例如， **ID_FILE_SAVE**) 跟 （例如，"将保存当前文档"） 的命令，以冒号分隔的目的。  
  
-   描述的类的一个或多个段落实现该命令，并默认实现的用途  
  
 大多数默认命令实现 prewired 在框架的基类消息映射中。 没有需要在派生类中的显式连结某些命令实现。 这些"注意"下的描述。 如果你在应用程序向导中选择正确的选项，您将这些默认处理程序的连接为你生成主干应用程序中。  
  
## <a name="naming-convention"></a>命名约定  
 标准命令按照简单的命名约定，我们建议你尽可能使用。 大多数标准命令都位于应用程序的菜单栏中的标准位置。 该命令的符号名称开头"ID_"跟标准的弹出菜单名称后, 跟菜单项名称。 以带有下划线断字的大写形式的符号名称。 没有标准菜单项名称的命令，请从"ID_"定义逻辑的命令名称 (例如， **ID_NEXT_PANE**)。  
  
 我们使用前缀"ID_"指示旨在绑定到菜单项、 工具栏按钮或其他命令的用户界面对象的命令。 处理"ID_"命令的命令处理程序应使用`ON_COMMAND`和`ON_UPDATE_COMMAND_UI`机制 MFC 命令体系结构。  
  
 我们建议您使用的菜单项不按照命令体系结构和需要菜单特有的代码来启用和禁用它们的标准"IDM_"前缀。 当然应的菜单特定命令的数目很小，因为以下 MFC 命令体系结构不仅使命令处理程序 （因为它们也适用于工具栏） 更强大但使命令的处理程序代码在可重用。  
  
## <a name="id-ranges"></a>ID 范围  
 请参阅[技术说明 20](../mfc/tn020-id-naming-and-numbering-conventions.md)有关详细信息的 MFC 中的 ID 范围的使用。  
  
 MFC 标准命令低于 0xE000 到 0xEFFF 的范围。 请不要依赖于这些 Id 的特定值因为它们可能会在将来版本的库中的更改。  
  
 你的应用程序应在范围 0x8000 到 0xDFFF 中定义其命令。  
  
## <a name="standard-command-ids"></a>标准命令 Id  
 对于每个命令 ID，没有可在文件的提示中找到一个标准消息行提示字符串。RC。 该菜单提示字符串 ID 必须是相同命令 id。  
  
-   ID_FILE_NEW 创建一个新/空文档。  
  
    > [!NOTE]
    >  你必须连接到你`CWinApp`-派生类的消息映射，以启用此功能。  
  
     `CWinApp::OnFileNew`应用程序中实现此命令以不同的方式根据文档模板数。 如果只有一个`CDocTemplate`，`CWinApp::OnFileNew`将创建该类型，以及适当的框架和视图类的新文档。  
  
     如果存在多个`CDocTemplate`，`CWinApp::OnFileNew`将提示用户提供一个对话框 (**AFX_IDD_NEWTYPEDLG**) 允许他们选择要使用的文档类型。 所选`CDocTemplate`用于创建的文档。  
  
     一个常见的自定义`ID_FILE_NEW`是提供不同和多个图形选择的文档类型。 在这种情况下你可以实现你自己**CMyApp::OnFileNew**并将其放在而不是消息映射中`CWinApp::OnFileNew`。 没有无需调用基类实现。  
  
     另一个常见的自定义`ID_FILE_NEW`是用于创建每个类型的文档中提供一个单独的命令。 在这种情况下应定义新的命令 Id，例如 ID_FILE_NEW_CHART 和 ID_FILE_NEW_SHEET。  
  
-   ID_FILE_OPEN 打开现有文档。  
  
    > [!NOTE]
    >  你必须连接到你`CWinApp`-派生类的消息映射，以启用此功能。  
  
     `CWinApp::OnFileOpen`已调用的非常简单实现**CWinApp::DoPromptFileName**跟`CWinApp::OpenDocumentFile`替换要打开的文件的文件或路径名称。 `CWinApp`实现例程**DoPromptFileName**标准 FileOpen 对话框会显示，并与文件扩展名从当前的文档模板获取进行填充。  
  
     一个常见的自定义`ID_FILE_OPEN`是自定义 FileOpen 对话框或添加其他文件筛选器。 此自定义的建议的方法是将替换为你自己 FileOpen 对话框中，并调用的默认实现`CWinApp::OpenDocumentFile`文档的文件或路径名称。 没有无需调用的基类。  
  
-   ID_FILE_CLOSE 关闭当前打开的文档。  
  
     **CDocument::OnFileClose**调用`CDocument::SaveModified`提示用户保存文档，如果它已被修改，然后调用`OnCloseDocument`。 在中执行所有关闭逻辑，包括销毁文档，`OnCloseDocument`例程。  
  
    > [!NOTE]
    >  **ID_FILE_CLOSE**作用以不同的方式从`WM_CLOSE`消息或**SC_CLOSE**系统命令发送到文档框架窗口。 仅当为最后一个显示文档的框架窗口，则关闭窗口将关闭文档。 关闭与文档**ID_FILE_CLOSE**不会仅关闭文档，但将关闭所有框架窗口显示文档。  
  
-   ID_FILE_SAVE 将保存当前的文档。  
  
     实现使用 helper 例程**CDocument::DoSave**两个用于**OnFileSave**和**OnFileSaveAs**。 如果你将保存之前从未进行已保存的文档 （即，它没有路径名称，如 FileNew） 或从只读文档，读取**OnFileSave**逻辑将充当**ID_FILE_SAVE_AS**命令，并要求用户提供新的文件名称。 打开文件并进行保存的实际过程通过虚函数`OnSaveDocument`。  
  
     有两个常见的原因，若要自定义**ID_FILE_SAVE**。 对于未保存的文档，只需删除**ID_FILE_SAVE**菜单项和工具栏按钮从用户界面。 此外，请确保你永远不会更新您的文档 (即，永远不会调用`CDocument::SetModifiedFlag`) 和框架将永远不会导致要保存的文档。 对于将保存到任何位置以外的磁盘文件的文档，定义新的命令为该操作。  
  
     情况下`COleServerDoc`， **ID_FILE_SAVE**用于保存文件 （对于正常文档） 和 （对于嵌入文档） 的文件更新。  
  
     如果你的文档数据存储在单个磁盘文件，但不想使用默认值**CDocument**序列化实现，则应重写`CDocument::OnSaveDocument`而不是**OnFileSave**。  
  
-   ID_FILE_SAVE_AS 将保存在不同的文件名称下的当前文档。  
  
     **CDocument::OnFileSaveAs**实现使用相同**CDocument::DoSave** helper 例程作为**OnFileSave**。 **OnFileSaveAs**命令处理一样**ID_FILE_SAVE**如果文档不具有之前保存的任何文件名。 **COleServerDoc::OnFileSaveAs**逻辑以便保存正常文档数据文件或将保存表示 OLE 对象的服务器文档嵌入其他应用程序作为一个单独的文件中的实现。  
  
     如果你自定义的逻辑**ID_FILE_SAVE**，你将可能想要自定义**ID_FILE_SAVE_AS**中以类似方式或"另存为"操作可能不适用于您的文档。 如果不需要的情况下，可以从菜单栏删除菜单项。  
  
-   ID_FILE_SAVE_COPY_AS 将保存新名称下的副本当前文档。  
  
     **COleServerDoc::OnFileSaveCopyAs**实现是非常类似于**CDocument::OnFileSaveAs**，只不过文档对象是否未"附加"到基础文件后保存。 也就是说，如果内存中文档的"修改"在保存之前，它仍"修改"。 此外，此命令不起上的路径名称或存储在文档的标题。  
  
-   ID_FILE_UPDATE 通知要保存嵌入的文档的容器。  
  
     `COleServerDoc::OnUpdateDocument`实现只需 notifiies 应保存嵌入的容器。 容器然后才能保存嵌入的对象调用相应 OLE Api。  
  
-   ID_FILE_PAGE_SETUP 调用应用程序特定的页上安装程序/布局对话框。  
  
     当前没有此对话框中，没有标准，该框架具有此命令没有默认实现。  
  
     如果你选择实现此命令，我们建议使用此命令 id。  
  
-   ID_FILE_PRINT_SETUP 调用标准的打印设置对话框。  
  
    > [!NOTE]
    >  你必须连接到你`CWinApp`-派生类的消息映射，以启用此功能。  
  
     此命令时，用户可以自定义打印机和打印设置至少标准的打印设置对话框，将调用此文档或最多中的所有文档此应用程序。 必须使用控制面板来更改整个系统的默认打印机设置。  
  
     `CWinApp::OnFilePrintSetup`具有非常简单的实现创建`CPrintDialog`对象，并调用**CWinApp::DoPrintDialog**实现函数。 这将设置应用程序默认打印机设置。  
  
     常见的需要自定义此命令是为了允许每个文档打印机设置，应使用该文档何时保存存储。 若要执行此操作应添加中的消息映射处理程序你**CDocument**创建类`CPrintDialog`对象，请使用相应的打印机的属性对其进行初始化 (通常**hDevMode**和**hDevNames**)，调用**CPrintDialog::DoModal，**并保存更改的打印机设置。 强大的实现，你应该查看的实现**CWinApp::DoPrintDialog**检测错误和**CWinApp::UpdatePrinterSelection**来处理合理的默认值和跟踪系统级打印机更改。  
  
-   当前文档的 ID_FILE_PRINT 标准打印  
  
    > [!NOTE]
    >  你必须连接到你`CView`-派生类的消息映射，以启用此功能。  
  
     此命令将打印当前文档中，或更准确地运行，启动打印过程，包括调用标准打印对话框和运行打印引擎。  
  
     **CView::OnFilePrint**实现此命令和主要打印循环。 调用虚拟`CView::OnPreparePrinting`到含有打印对话框的用户的提示。 它然后准备输出 DC 转到打印机、 打印进度对话框会显示 (**AFX_IDD_PRINTDLG**)，并将发送`StartDoc`转义到打印机。 **CView::OnFilePrint**还包含主要面向页打印循环。 对于每个页中，它调用的虚拟`CView::OnPrepareDC`跟`StartPage`转义和调用虚拟`CView::OnPrint`该页面的。 完成时，虚拟`CView::OnEndPrinting`调用，并打印进度对话框关闭。  
  
     MFC 打印体系结构旨在挂钩中打印和打印预览的许多不同的方法。 你通常会发现各种`CView`可重写函数适合任何面向页的打印作业。 仅在使用打印机面向非页的输出中，如果您发现需要替换的应用程序的情况下**ID_FILE_PRINT**实现。  
  
-   当前文档 ID_FILE_PRINT_PREVIEW 输入打印预览模式。  
  
    > [!NOTE]
    >  你必须连接到你`CView`-派生类的消息映射，以启用此功能。  
  
     **CView::OnFilePrintPreview**通过调用有案可稽的 helper 函数启动的打印预览模式**CView::DoPrintPreview**。 **CView::DoPrintPreview**就像是打印预览循环的主要引擎**OnFilePrint**是主要的引擎，打印循环。  
  
     打印预览操作可以自定义各种不同的方式通过将传递到不同的参数**DoPrintPreview**。 请参阅[技术注意 30](../mfc/tn030-customizing-printing-and-print-preview.md)，其中讨论了一些打印预览的详细信息以及如何自定义它。  
  
-   **ID_FILE_MRU_FILE1**...**FILE16**文件 MRU 的命令 Id 的范围`list`。  
  
     **CWinApp::OnUpdateRecentFileMenu**是更高级的用途之一的更新命令 UI 处理程序`ON_UPDATE_COMMAND_UI`机制。 在菜单资源，你仅需要定义单个菜单项 id **ID_FILE_MRU_FILE1**。 该菜单项保持最初已禁用。  
  
     随着 MRU 列表的增长，更多菜单项被添加到列表。 标准`CWinApp`实现默认为四个最近使用过的文件的标准限制。 你可以通过调用来更改默认值`CWinApp::LoadStdProfileSettings`具有更大或更小的值。 MRU 列表存储在应用程序的。INI 文件。 应用程序中加载列表`InitInstance`函数如果调用`LoadStdProfileSettings`，并将其应用程序退出时保存。 此外，MRU 更新命令 UI 处理程序会将绝对路径转换为针对文件菜单上的显示的相对路径。  
  
     **CWinApp::OnOpenRecentFile**是`ON_COMMAND`执行实际的命令的处理程序。 只需获取的文件名称从 MRU 列表和调用`CWinApp::OpenDocumentFile`，执行的打开的文件和更新 MRU 列表的所有工作。  
  
     不建议此命令处理程序的自定义。  
  
-   ID_EDIT_CLEAR 清除当前的选择  
  
     当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生类。  
  
     `CEditView`提供的此命令使用实现`CEdit::Clear`。 如果没有当前选定内容，则禁用该命令。  
  
     如果你选择实现此命令，我们建议使用此命令 id。  
  
-   ID_EDIT_CLEAR_ALL 清除整个文档。  
  
     当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生类。  
  
     如果你选择实现此命令，我们建议使用此命令 id。 请参阅 MFC 教程示例[SCRIBBLE](../visual-cpp-samples.md)有关示例实现。  
  
-   ID_EDIT_COPY 将当前所选内容复制到剪贴板。  
  
     当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生类。  
  
     `CEditView`提供的此命令，用于将当前选定的文本复制到作为 CF_TEXT 使用剪贴板实现`CEdit::Copy`。 如果没有当前选定内容，则禁用该命令。  
  
     如果你选择实现此命令，我们建议使用此命令 id。  
  
-   ID_EDIT_CUT 剪切到剪贴板当前所选内容。  
  
     当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生类。  
  
     `CEditView`提供的此命令，用于将当前选定的文本剪切到剪贴板 CF_TEXT 使用实现`CEdit::Cut`。 如果没有当前选定内容，则禁用该命令。  
  
     如果你选择实现此命令，我们建议使用此命令 id。  
  
-   ID_EDIT_FIND 开始查找操作中，将显示无模式查找对话框。  
  
     当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生类。  
  
     `CEditView`提供的此命令，用于调用实现帮助器函数的实现**OnEditFindReplace**使用并将以前的查找/替换设置存储在私有实现变量。 `CFindReplaceDialog`类用于管理用于提示用户的无模式对话框。  
  
     如果你选择实现此命令，我们建议使用此命令 id。  
  
-   ID_EDIT_PASTE 插入当前剪贴板的内容。  
  
     当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生类。  
  
     `CEditView`提供的此命令，将替换所选的文本使用的当前剪贴板数据复制实现`CEdit::Paste`。 如果没有已禁用命令没有**CF_TEXT**将剪贴板中。  
  
     **COleClientDoc**只是为此命令中提供的更新命令 UI 处理程序。 如果剪贴板不包含可嵌入 OLE 项/对象，该命令将被禁用。 你负责编写实际的命令来执行实际粘贴的处理程序。 如果 OLE 应用程序还可将粘贴其他格式，则应提供在视图或文档中的自己更新命令 UI 处理程序 (即，某个位置之前**COleClientDoc**命令目标路由中)。  
  
     如果你选择实现此命令，我们建议使用此命令 id。  
  
     用于更换有标准的 OLE 实现，使用`COleClientItem::CanPaste`。  
  
-   ID_EDIT_PASTE_LINK 从当前的剪贴板内容插入一个链接。  
  
     当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生类。  
  
     `COleDocument`此命令只是提供的更新命令 UI 处理程序。 如果剪贴板不包含可链接 OLE 项/对象，该命令将被禁用。 你负责编写实际的命令来执行实际粘贴的处理程序。 如果 OLE 应用程序还可将粘贴其他格式，则应提供在视图或文档中的自己更新命令 UI 处理程序 (即，某个位置之前`COleDocument`命令目标路由中)。  
  
     如果你选择实现此命令，我们建议使用此命令 id。  
  
     用于更换有标准的 OLE 实现，使用`COleClientItem::CanPasteLink`。  
  
-   ID_EDIT_PASTE_SPECIAL 插入选项的当前剪贴板内容。  
  
     当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生类。 MFC 不提供此对话框。  
  
     如果你选择实现此命令，我们建议使用此命令 id。  
  
-   ID_EDIT_REPEAT 重复最后一个操作。  
  
     当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生类。  
  
     `CEditView`提供此命令可重复最后一次的查找操作的实现。 使用最后一个查找的私有实现变量。 如果无法尝试查找，则禁用该命令。  
  
     如果你选择实现此命令，我们建议使用此命令 id。  
  
-   ID_EDIT_REPLACE 开始替换操作中，将显示无模式替换对话框。  
  
     当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生类。  
  
     `CEditView`提供的此命令，用于调用实现帮助器函数的实现**OnEditFindReplace**使用并将以前的查找/替换设置存储在私有实现变量。 `CFindReplaceDialog`类用于管理无模式对话框，提示用户。  
  
     如果你选择实现此命令，我们建议使用此命令 id。  
  
-   ID_EDIT_SELECT_ALL 选择整个文档。  
  
     当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生类。  
  
     `CEditView`提供此命令，用于在文档中选择所有文本的实现。 如果不没有选择任何文本，则禁用该命令。  
  
     如果你选择实现此命令，我们建议使用此命令 id。  
  
-   ID_EDIT_UNDO 撤消上一个操作。  
  
     当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生类。  
  
     `CEditView`提供的此实现命令，使用`CEdit::Undo`。 如果已禁用命令`CEdit::CanUndo`方法将返回 FALSE。  
  
     如果你选择实现此命令，我们建议使用此命令 id。  
  
-   ID_EDIT_REDO 重做最后一个操作。  
  
     当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生类。  
  
     如果你选择实现此命令，我们建议使用此命令 id。  
  
-   ID_WINDOW_NEW 打开在活动文档另一个窗口。  
  
     **CMDIFrameWnd::OnWindowNew**实现此功能很强大，通过使用当前文档的文档模板创建另一个框架，其中包含当前文档的另一个视图。  
  
     大多数多文档界面 (MDI) 窗口菜单与命令一样，如果没有任何活动的 MDI 子窗口，则禁用该命令。  
  
     不建议此命令处理程序的自定义。 如果你想要提供一个可创建其他视图或框架窗口的命令，你将可能会更好关闭发明您自己的命令。 您可以克隆中的代码**CMDIFrameWnd::OnWindowNew**和修改它为你喜欢的特定的框架和视图类。  
  
-   在 MDI 窗口底部 ID_WINDOW_ARRANGE 排列图标。  
  
     `CMDIFrameWnd`实现帮助器函数中实现此标准的 MDI 命令**OnMDIWindowCmd**。 此帮助程序将命令 Id 映射到 MDI 窗口消息，并因此共享大量的代码。  
  
     与大多数 MDI 窗口菜单命令，一样没有活动的 MDI 子窗口是否已禁用命令。  
  
     不建议此命令处理程序的自定义。  
  
-   ID_WINDOW_CASCADE 级联窗口成相互重叠。  
  
     `CMDIFrameWnd`实现帮助器函数中实现此标准的 MDI 命令**OnMDIWindowCmd**。 此帮助程序将命令 Id 映射到 MDI 窗口消息，并因此共享大量的代码。  
  
     与大多数 MDI 窗口菜单命令，一样没有活动的 MDI 子窗口是否已禁用命令。  
  
     不建议此命令处理程序的自定义。  
  
-   ID_WINDOW_TILE_HORZ 磁贴 windows 水平。  
  
     此命令实现中`CMDIFrameWnd`就像**ID_WINDOW_CASCADE**，只是不同的 MDI 窗口消息用来执行操作。  
  
     你的应用程序，则应选择默认磁贴方向。 你可以执行此操作通过更改窗口"磁贴"菜单项的 ID 为**ID_WINDOW_TILE_HORZ**或**ID_WINDOW_TILE_VERT**。  
  
-   ID_WINDOW_TILE_VERT 磁贴 windows 垂直。  
  
     此命令实现中`CMDIFrameWnd`就像**ID_WINDOW_CASCADE**，只是不同的 MDI 窗口消息用来执行操作。  
  
     你的应用程序，则应选择默认磁贴方向。 你可以执行此操作通过更改窗口"磁贴"菜单项的 ID 为**ID_WINDOW_TILE_HORZ**或**ID_WINDOW_TILE_VERT**。  
  
-   ID_WINDOW_SPLIT 键盘置于拆分器的接口。  
  
     `CView`处理此命令`CSplitterWnd`实现。 如果视图是拆分窗口的一部分，此命令将委托给实现函数`CSplitterWnd::DoKeyboardSplit`。 这会将拆分器置于一种模式，将允许键盘用户拆分或撤销拆分拆分窗口。  
  
     如果视图不在拆分，则禁用此命令。  
  
     不建议此命令处理程序的自定义。  
  
-   ID_APP_ABOUT 调用关于对话框。  
  
     没有标准实现应用程序的关于框中。 默认应用程序向导创建应用程序将创建一个自定义对话框类，你的应用程序，并将其用作你有关的框。 应用程序向导也将编写的普通命令处理程序，也不能处理此命令调用对话框。  
  
     几乎始终将实现此命令。  
  
-   ID_APP_EXIT 退出应用程序。  
  
     **CWinApp::OnAppExit**处理此命令通过发送`WM_CLOSE`消息发送到应用程序的主窗口。 由处理标准 （会提示输入已更新文件，依此类推） 的应用程序关闭`CFrameWnd`实现。  
  
     不建议此命令处理程序的自定义。 重写`CWinApp::SaveAllModified`或`CFrameWnd`关闭逻辑建议。  
  
     如果你选择实现此命令，我们建议使用此命令 id。  
  
-   从 ID_HELP_INDEX 列出帮助主题。HLP 文件。  
  
    > [!NOTE]
    >  你必须连接到你`CWinApp`-派生类的消息映射，以启用此功能。  
  
     `CWinApp::OnHelpIndex`处理此命令通过一般而言调用`CWinApp::WinHelp`。  
  
     不建议此命令处理程序的自定义。  
  
-   ID_HELP_USING 显示如何使用帮助的帮助。  
  
    > [!NOTE]
    >  你必须连接到你`CWinApp`-派生类的消息映射，以启用此功能。  
  
     `CWinApp::OnHelpUsing`处理此命令通过一般而言调用`CWinApp::WinHelp`。  
  
     不建议此命令处理程序的自定义。  
  
-   ID_CONTEXT_HELP 进入 SHIFT 的 F1 帮助模式。  
  
    > [!NOTE]
    >  你必须连接到你`CWinApp`-派生类的消息映射，以启用此功能。  
  
     `CWinApp::OnContextHelp`通过设置帮助模式光标、 输入模式的循环等待用户选择一个窗口，以获取有关帮助处理此命令。 请参阅[技术注意 28](../mfc/tn028-context-sensitive-help-support.md)有关 MFC 帮助实现的详细信息。  
  
     不建议此命令处理程序的自定义。  
  
-   ID_HELP 提供了在当前上下文的帮助  
  
    > [!NOTE]
    >  你必须连接到你`CWinApp`-派生类的消息映射，以启用此功能。  
  
     `CWinApp::OnHelp`为当前的应用程序上下文中获取正确的帮助上下文来处理此命令。 这处理简单的 F1 帮助，依次类推帮助消息框上。 请参阅[技术注意 28](../mfc/tn028-context-sensitive-help-support.md)的 MFC 中的更多详细信息帮助实现。  
  
     不建议此命令处理程序的自定义。  
  
-   ID_DEFAULT_HELP 显示默认上下文的帮助  
  
    > [!NOTE]
    >  你必须连接到你`CWinApp`-派生类的消息映射，以启用此功能。  
  
     此命令通常会映射到`CWinApp::OnHelpIndex`。  
  
     如果需要区分默认帮助与帮助索引，则可以提供不同的命令处理程序。  
  
-   ID_NEXT_PANE 将转到下一个窗格  
  
     `CView`处理此命令`CSplitterWnd`实现。 如果视图是拆分窗口的一部分，此命令将委托给实现函数**CSplitterWnd::OnNextPaneCmd**。 这会将活动视图移动到下一步中拆分器窗格中。  
  
     如果视图不在拆分或没有下一步的窗格中，转到，则禁用此命令。  
  
     不建议此命令处理程序的自定义。  
  
-   ID_PREV_PANE 将转到上一个窗格  
  
     `CView`处理此命令`CSplitterWnd`实现。 如果视图是拆分窗口的一部分，此命令将委托给实现函数**CSplitterWnd::OnNextPaneCmd**。 这会将活动视图移动到在拆分器的上窗格中。  
  
     如果视图不在拆分或没有任何以前的窗格中，转到，则禁用此命令。  
  
     不建议此命令处理程序的自定义。  
  
-   ID_OLE_INSERT_NEW 插入新的 OLE 对象  
  
     当前没有此命令的标准实现。 您必须实现此为您`CView`-派生类中当前选定的位置插入一个新的 OLE 项/对象。  
  
     所有的 OLE 客户端应用程序应实现此命令。 应用程序向导，使用 OLE 选项中，将创建的主干实现**OnInsertObject**你将必须完成的视图类中。  
  
     请参阅 MFC OLE 示例[OCLIENT](../visual-cpp-samples.md)更大的示例此命令的完整实现。  
  
-   ID_OLE_EDIT_LINKS 编辑 OLE 链接  
  
     `COleDocument`通过使用标准的 OLE 链接对话框提供 MFC 实现中处理此命令。 通过访问此对话框的实现`COleLinksDialog`类。 如果当前文档不包含任何链接，将禁用该命令。  
  
     不建议此命令处理程序的自定义。  
  
-   ID_OLE_VERB_FIRST...用于 OLE 谓词的最后一个 ID 范围  
  
     `COleDocument`当前所选 OLE 项/对象支持的谓词中使用此命令 ID 范围。 这必须是一个范围，因为给定的 OLE 项/对象类型可以支持零个或多个自定义的谓词。 在你的应用程序菜单中，你应具有一个菜单项的 id **ID_OLE_VERB_FIRST**。 当运行该程序时，将随相应的菜单谓词说明 （或多个谓词的弹出菜单） 更新菜单。 OLE 菜单的管理将由处理`AfxOleSetEditMenu`，完成此命令更新命令 UI 处理程序中。  
  
     有无显式命令事件处理程序处理每个在此范围内的命令 ID。 **COleDocument::OnCmdMsg**被重写以捕获在此范围内的所有命令 Id，它们转换为从零开始的谓词数字，并启动该动词的服务器 (使用`COleClientItem::DoVerb`)。  
  
     不建议自定义项或其他使用此命令 ID 范围。  
  
-   ID_VIEW_TOOLBAR 打开和关闭之间切换工具栏  
  
     `CFrameWnd`处理此命令，并更新命令 UI 处理程序来切换工具栏的可见状态。 工具栏必须是子窗口的框架的子窗口 id 为`AFX_IDW_TOOLBAR`。 命令处理程序实际切换的可见性工具栏窗口。 `CFrameWnd::RecalcLayout`用于在其新的状态重绘通过工具栏的框架窗口。 在工具栏可见时，更新命令 UI 处理程序将检查菜单项。  
  
     不建议此命令处理程序的自定义。 如果你想要添加额外的工具栏，你将想要克隆和修改的命令处理程序和更新命令 UI 处理此命令。  
  
-   ID_VIEW_STATUS_BAR 打开和关闭之间切换状态栏  
  
     此命令实现中`CFrameWnd`就像**ID_VIEW_TOOLBAR**，除非不同的子窗口 ID (**AFX_IDW_STATUS_BAR**) 使用。  
  
## <a name="update-only-command-handlers"></a>仅更新命令处理程序  
 多个标准命令 Id 用作中状态栏的指示符。 这些使用相同的处理机制的更新命令 UI 以应用程序空闲时显示其当前的可视状态。 由于它们不能由用户选择 （即，不能推送状态栏窗格），则没有意义能够`ON_COMMAND`这些命令 Id 的处理程序。  
  
-   **ID_INDICATOR_CAPS** : CAP 锁指示符。  
  
-   **ID_INDICATOR_NUM** : NUM lock 指示器。  
  
-   **ID_INDICATOR_SCRL** : SCRL 锁指示符。  
  
-   **ID_INDICATOR_KANA** ： 假名锁指示符 （仅适用于日语系统）。  
  
 在中实现，所有三种**CFrameWnd::OnUpdateKeyIndicator**，使用的命令 ID 映射到相应的虚拟键的实现帮助器。 通用的实现启用或禁用 （已禁用的状态窗格 = 没有文本）`CCmdUI`具体取决于是否适当虚拟键当前已锁定的对象。  
  
 不建议此命令处理程序的自定义。  
  
-   **ID_INDICATOR_EXT: EXT**结束选择指示器。  
  
-   **ID_INDICATOR_OVR： 向**e**R**strike 指示器。  
  
-   **ID_INDICATOR_REC: REC**ording 指示器。  
  
 当前没有这些指示器的标准实现。  
  
 如果你选择实现这些指示符，我们建议你使用这些指示器 Id 和维护内你状态栏的指示符的顺序 (即，按以下顺序： EXT、 CAP、 NUM、 SCRL、 改写、 REC)。  
  
## <a name="see-also"></a>另请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

