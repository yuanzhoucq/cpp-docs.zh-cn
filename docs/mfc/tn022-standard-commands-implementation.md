---
title: TN022：标准命令实现
ms.date: 11/04/2016
f1_keywords:
- vc.commands
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
ms.openlocfilehash: 5c7041f40c7e30592f642d29d9d02812a9596864
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370396"
---
# <a name="tn022-standard-commands-implementation"></a>TN022：标准命令实现

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

本说明描述了 MFC 2.0 提供的标准命令实现。 首先阅读[技术说明 21，](../mfc/tn021-command-and-message-routing.md)因为它描述了用于实现许多标准命令的机制。

此描述假定了解 MFC 体系结构、API 和常见编程实践。 介绍了文档记录以及未记录的"仅实现"API。 这不是开始学习 MFC 的功能或编程方式的地方。 有关更多一般信息和文档化 API 的详细信息，请参阅 Visual C++。

## <a name="the-problem"></a>问题

MFC 在标头文件 AFXRES 中定义许多标准命令指示。H。 对这些命令的框架支持各不相同。 了解框架类处理这些命令的位置和方式不仅会向您展示框架内部工作原理，而且还会提供有关如何自定义标准实现的有用信息，并教您实现自己的命令处理程序的一些技术。

## <a name="contents-of-this-technical-note"></a>本技术说明的内容

每个命令 ID 由两部分组成：

- 标题：命令 ID 的符号名称（例如，ID_FILE_SAVE），后跟命令的目的（例如，"保存当前文档"）用冒号分隔。

- 一个或多个段落，描述哪些类实现命令，以及默认实现的作用

大多数默认命令实现在框架的基类消息映射中预接。 派生类中有些命令实现需要显式布线。 这些在"说明"下描述。 如果在 AppWizard 中选择正确的选项，这些默认处理程序将在生成的骨架应用程序中为您连接。

## <a name="naming-convention"></a>命名约定

标准命令遵循一个简单的命名约定，我们建议您尽可能使用。 大多数标准命令位于应用程序菜单栏中的标准位置。 命令的符号名称以"ID_"开头，后跟标准弹出菜单名称，后跟菜单项名称。 符号名称在大写中带有下划线单词中断。 对于没有标准菜单项名称的命令，逻辑命令名称以"ID_"开头定义（例如，ID_NEXT_PANE）。

我们使用前缀"ID_"来指示设计绑定到菜单项、工具栏按钮或其他命令用户界面对象的命令。 处理"ID_"命令的命令处理程序应使用 MFC 命令体系结构ON_COMMAND和ON_UPDATE_COMMAND_UI机制。

对于不遵循命令体系结构且需要特定于菜单的代码来启用和禁用它们的菜单项，我们建议您使用标准的"IDM_"前缀。 当然，菜单特定命令的数量应该很小，因为遵循 MFC 命令体系结构不仅使命令处理程序更强大（因为它们将处理工具栏），而且使命令处理程序代码可重用。

## <a name="id-ranges"></a>ID 范围

有关在 MFC 中使用 ID 范围的更多详细信息，请参阅[技术说明 20。](../mfc/tn020-id-naming-and-numbering-conventions.md)

MFC 标准命令位于 0xE000 到 0xEFFF 范围内。 请不要依赖这些指示器的特定值，因为它们可能会在库的未来版本中更改。

应用程序应在 0x8000 到 0xDFFF 范围内定义其命令。

## <a name="standard-command-ids"></a>标准命令指示

对于每个命令 ID，在文件 PROMPTS 中可以找到一个标准消息行提示符字符串。钢筋混凝土。 该菜单提示符的字符串 ID 必须与命令 ID 的字符串 ID 相同。

- ID_FILE_NEW 创建新/空文档。

    > [!NOTE]
    >  您必须将其连接到`CWinApp`派生类的消息映射才能启用此功能。

   `CWinApp::OnFileNew`根据应用程序中的文档模板数量，以不同的方式实现此命令。 如果只有一个`CDocTemplate`，`CWinApp::OnFileNew`将创建该类型的新文档，以及适当的框架和视图类。

   如果有多个`CDocTemplate`，`CWinApp::OnFileNew`将提示用户使用对话框 （AFX_IDD_NEWTYPEDLG），让他们选择要使用的文档类型。 所选`CDocTemplate`文档用于创建文档。

   ID_FILE_NEW的一个常见自定义是提供不同且更图形化的文档类型选择。 在这种情况下，您可以实现自己的`CMyApp::OnFileNew`，并将其放置在消息映射中，而不是`CWinApp::OnFileNew`。 无需调用基类实现。

   ID_FILE_NEW的另一个常见自定义是提供用于创建每种类型文档的单独命令。 在这种情况下，应定义新的命令指示，例如ID_FILE_NEW_CHART和ID_FILE_NEW_SHEET。

- ID_FILE_OPEN 打开现有文档。

    > [!NOTE]
    >  您必须将其连接到`CWinApp`派生类的消息映射才能启用此功能。

   `CWinApp::OnFileOpen`具有非常简单的调用`CWinApp::DoPromptFileName`实现，然后是`CWinApp::OpenDocumentFile`要打开的文件或路径名称。 实现`CWinApp`例程`DoPromptFileName`将弹出标准 FileOpen 对话框，并将其填充从当前文档模板获取的文件扩展名。

   ID_FILE_OPEN的一个常见自定义是自定义文件打开对话框或添加其他文件筛选器。 自定义此项的建议方法是将默认实现替换为您自己的 FileOpen 对话框，然后使用文档的文件或`CWinApp::OpenDocumentFile`路径名称调用。 无需调用基类。

- ID_FILE_CLOSE 关闭当前打开的文档。

   `CDocument::OnFileClose`调用`CDocument::SaveModified`以提示用户保存文档（如果文档已被修改，然后调用`OnCloseDocument`）。 所有关闭逻辑（包括销毁文档）都在例程中`OnCloseDocument`完成。

    > [!NOTE]
    >  ID_FILE_CLOSE的行为与发送到文档框架窗口的WM_CLOSE消息或SC_CLOSE系统命令不同。 仅当文档是显示文档的最后一个框架窗口时，关闭窗口才会关闭该文档。 用ID_FILE_CLOSE关闭文档不仅会关闭文档，还将关闭显示文档的所有框架窗口。

- ID_FILE_SAVE保存当前文档。

   实现使用帮助程序例程，该`CDocument::DoSave`例程用于 和`OnFileSave``OnFileSaveAs`。 如果保存以前未保存的文档（即，它没有路径名称，如 FileNew），或者从只读文档读取的文档，`OnFileSave`则逻辑将类似于ID_FILE_SAVE_AS命令，并要求用户提供新的文件名。 打开文件并执行保存的实际过程是通过虚拟函数`OnSaveDocument`完成的。

   自定义ID_FILE_SAVE有两个常见原因。 对于不保存的文档，只需从用户界面中删除ID_FILE_SAVE菜单项和工具栏按钮即可。 还要确保永远不会弄脏文档（即从不调用`CDocument::SetModifiedFlag`），并且框架永远不会导致文档被保存。 对于保存到磁盘文件以外的某个位置的文档，请为该操作定义一个新命令。

   在 的情况下，ID_FILE_SAVE`COleServerDoc`既用于文件保存（对于普通文档）又用于文件更新（对于嵌入文档）。

   如果文档数据存储在单个磁盘文件中，但不希望使用默认`CDocument`序列化实现，则应重写`CDocument::OnSaveDocument`而不是`OnFileSave`。

- ID_FILE_SAVE_AS将当前文档保存在不同的文件名下。

   实现`CDocument::OnFileSaveAs`使用与 相同的`CDocument::DoSave`帮助程序例程`OnFileSave`。 如果`OnFileSaveAs`文档在保存之前没有文件名，则该命令的处理方式与ID_FILE_SAVE相同。 `COleServerDoc::OnFileSaveAs`实现用于保存普通文档数据文件或将表示嵌入在其他某个应用程序中的 OLE 对象的服务器文档作为单独的文件实现逻辑。

   如果自定义ID_FILE_SAVE的逻辑，则可能需要以类似方式自定义ID_FILE_SAVE_AS，或者"保存为"的操作可能不适用于文档。 如果需要，可以从菜单栏中删除菜单项。

- ID_FILE_SAVE_COPY_AS将当前副本保存在新名称下。

   实现`COleServerDoc::OnFileSaveCopyAs`与 非常相似`CDocument::OnFileSaveAs`，只是文档对象在保存后未"附加到"基础文件。 也就是说，如果内存中的文档在保存之前被"修改"，它仍然是"修改的"。 此外，此命令对存储在文档中的路径名称或标题没有影响。

- ID_FILE_UPDATE通知容器保存嵌入的文档。

   实现`COleServerDoc::OnUpdateDocument`只是通知容器应保存嵌入。 然后，容器调用适当的 OLE API 以保存嵌入的对象。

- ID_FILE_PAGE_SETUP调用特定于应用程序的页面设置/布局对话框。

   目前没有此对话框的标准，并且框架没有此命令的默认实现。

   如果选择实现此命令，我们建议您使用此命令 ID。

- ID_FILE_PRINT_SETUP调用标准打印设置对话框。

    > [!NOTE]
    >  您必须将其连接到`CWinApp`派生类的消息映射才能启用此功能。

   此命令调用标准打印设置对话框，允许用户至少为本文档或最多此应用程序中的所有文档自定义打印机和打印设置。 您必须使用"控制面板"更改整个系统的默认打印机设置。

   `CWinApp::OnFilePrintSetup`具有创建`CPrintDialog`对象并调用实现函数的非常简单的`CWinApp::DoPrintDialog`实现。 这将设置应用程序默认打印机设置。

   自定义此命令的常见需要是允许每个文档的打印机设置，这些设置在保存时应随文档一起存储。 为此，应在`CDocument`类中添加一个消息映射处理程序，该处理程序创建一个`CPrintDialog`对象，使用适当的打印机属性（通常*为 hDevMode*和*hDevNames）* 初始化它`CPrintDialog::DoModal`，调用 调用 ，并保存已更改的打印机设置。 对于可靠的实现，您应该查看`CWinApp::DoPrintDialog`用于检测错误和处理`CWinApp::UpdatePrinterSelection`合理的默认值和处理系统范围打印机更改的实现。

- ID_FILE_PRINT 当前文档的标准打印

    > [!NOTE]
    >  您必须将其连接到`CView`派生类的消息映射才能启用此功能。

   此命令打印当前文档，或者更正确地启动打印过程，这涉及调用标准打印对话框并运行打印引擎。

   `CView::OnFilePrint`实现此命令和主打印循环。 它调用虚拟`CView::OnPreparePrinting`以提示用户使用打印对话框。 然后，它将输出 DC 准备转到打印机，启动打印进度对话框（AFX_IDD_PRINTDLG），然后将`StartDoc`转义器发送到打印机。 `CView::OnFilePrint`还包含面向页面的主打印循环。 对于每个页面，它调用虚拟`CView::OnPrepareDC`，后跟一`StartPage`个转义，并`CView::OnPrint`调用该页的虚拟。 完成后，将调用虚拟`CView::OnEndPrinting`，并关闭打印进度对话框。

   MFC 打印架构旨在以许多不同的方式进行打印和打印预览。 您通常会发现各种`CView`可重写功能足以执行任何面向页面的打印任务。 仅当应用程序使用打印机进行非面向页面的输出时，您才应发现需要替换ID_FILE_PRINT实现。

- ID_FILE_PRINT_PREVIEW 输入当前文档的打印预览模式。

    > [!NOTE]
    >  您必须将其连接到`CView`派生类的消息映射才能启用此功能。

   `CView::OnFilePrintPreview`通过调用记录的帮助程序函数`CView::DoPrintPreview`启动打印预览模式。 `CView::DoPrintPreview`是打印预览循环的主引擎，就像打印循环的主引擎`OnFilePrint`一样。

   打印预览操作可以通过将不同的参数传递给`DoPrintPreview`来以多种方式进行自定义。 请参阅[技术说明30，](../mfc/tn030-customizing-printing-and-print-preview.md)其中讨论了打印预览的一些细节以及如何自定义它。

- ID_FILE_MRU_FILE1...FILE16 文件 MRU 列表的命令指示数**范围**。

   `CWinApp::OnUpdateRecentFileMenu`是更新命令 UI 处理程序，它是ON_UPDATE_COMMAND_UI机制的更高级用途之一。 在菜单资源中，只需定义具有 ID ID_FILE_MRU_FILE1的单个菜单项。 该菜单项最初保持禁用状态。

   随着 MRU 列表的增长，更多的菜单项将添加到列表中。 标准`CWinApp`实现默认为四个最近使用的文件的标准限制。 可以通过使用较大或更小的值调用`CWinApp::LoadStdProfileSettings`来更改默认值。 MRU 列表存储在应用程序的 中。INI 文件。 如果调用`LoadStdProfileSettings`，则列表将加载到应用程序的`InitInstance`函数中，并在应用程序退出时保存。 MRU 更新命令 UI 处理程序还将将绝对路径转换为相对路径，以便显示在文件菜单上。

   `CWinApp::OnOpenRecentFile`是执行实际命令的ON_COMMAND处理程序。 它只是从 MRU 列表和调用`CWinApp::OpenDocumentFile`中获取文件名，它执行打开文件和更新 MRU 列表的所有工作。

   不建议自定义此命令处理程序。

- ID_EDIT_CLEAR 清除当前选择

   目前没有此命令的标准实现。 您必须为每个`CView`派生类实现此。

   `CEditView`使用`CEdit::Clear`提供此命令的实现。 如果没有当前选择，则禁用该命令。

   如果选择实现此命令，我们建议您使用此命令 ID。

- ID_EDIT_CLEAR_ALL清除整个文档。

   目前没有此命令的标准实现。 您必须为每个`CView`派生类实现此。

   如果选择实现此命令，我们建议您使用此命令 ID。 有关实现示例，请参阅 MFC 教程示例[SCRIBBLE。](../overview/visual-cpp-samples.md)

- ID_EDIT_COPY将当前选择复制到剪贴板。

   目前没有此命令的标准实现。 您必须为每个`CView`派生类实现此。

   `CEditView`提供此命令的实现，该命令将当前选定的文本复制到剪贴板，CF_TEXT使用`CEdit::Copy`。 如果没有当前选择，则禁用该命令。

   如果选择实现此命令，我们建议您使用此命令 ID。

- ID_EDIT_CUT将当前选择剪切到剪贴板。

   目前没有此命令的标准实现。 您必须为每个`CView`派生类实现此。

   `CEditView`提供此命令的实现，该命令将当前选定的文本剪切到剪贴板，CF_TEXT使用`CEdit::Cut`。 如果没有当前选择，则禁用该命令。

   如果选择实现此命令，我们建议您使用此命令 ID。

- ID_EDIT_FIND 开始查找操作，则启动无模式查找对话框。

   目前没有此命令的标准实现。 您必须为每个`CView`派生类实现此。

   `CEditView`提供此命令的实现，该命令调用实现帮助器函数`OnEditFindReplace`，以便在私有实现变量中使用和存储以前的查找/替换设置。 类`CFindReplaceDialog`用于管理用于提示用户的无模式对话框。

   如果选择实现此命令，我们建议您使用此命令 ID。

- ID_EDIT_PASTE 插入当前剪贴板内容。

   目前没有此命令的标准实现。 您必须为每个`CView`派生类实现此。

   `CEditView`提供此命令的实现，该命令使用`CEdit::Paste`复制当前剪贴板数据，替换所选文本。 如果剪贴板中没有**CF_TEXT，** 则禁用该命令。

   `COleClientDoc`只是为此命令提供更新命令 UI 处理程序。 如果剪贴板不包含可嵌入的 OLE 项/对象，则该命令将被禁用。 您负责为实际命令编写处理程序以执行实际粘贴。 如果 OLE 应用程序还可以粘贴其他格式，则应在视图或文档中（即命令目标路由之前`COleClientDoc`的某个位置）中提供您自己的更新命令 UI 处理程序。

   如果选择实现此命令，我们建议您使用此命令 ID。

   要替换标准 OLE 实现，`COleClientItem::CanPaste`请使用 。

- ID_EDIT_PASTE_LINK 从当前剪贴板内容插入链接。

   目前没有此命令的标准实现。 您必须为每个`CView`派生类实现此。

   `COleDocument`只是为此命令提供更新命令 UI 处理程序。 如果剪贴板不包含可链接的 OLE 项/对象，则该命令将被禁用。 您负责为实际命令编写处理程序以执行实际粘贴。 如果 OLE 应用程序还可以粘贴其他格式，则应在视图或文档中（即命令目标路由之前`COleDocument`的某个位置）中提供您自己的更新命令 UI 处理程序。

   如果选择实现此命令，我们建议您使用此命令 ID。

   要替换标准 OLE 实现，`COleClientItem::CanPasteLink`请使用 。

- ID_EDIT_PASTE_SPECIAL使用选项插入当前剪贴板内容。

   目前没有此命令的标准实现。 您必须为每个`CView`派生类实现此。 MFC 不提供此对话框。

   如果选择实现此命令，我们建议您使用此命令 ID。

- ID_EDIT_REPEAT重复最后一个操作。

   目前没有此命令的标准实现。 您必须为每个`CView`派生类实现此。

   `CEditView`提供此命令的实现以重复最后一个查找操作。 使用最后一个查找的私有实现变量。 如果无法尝试查找，则该命令将禁用。

   如果选择实现此命令，我们建议您使用此命令 ID。

- ID_EDIT_REPLACE 开始替换操作，请启动无模式替换对话框。

   目前没有此命令的标准实现。 您必须为每个`CView`派生类实现此。

   `CEditView`提供此命令的实现，该命令调用实现帮助器函数`OnEditFindReplace`，以便在私有实现变量中使用和存储以前的查找/替换设置。 类`CFindReplaceDialog`用于管理提示用户的无模式对话框。

   如果选择实现此命令，我们建议您使用此命令 ID。

- ID_EDIT_SELECT_ALL 选择整个文档。

   目前没有此命令的标准实现。 您必须为每个`CView`派生类实现此。

   `CEditView`提供此命令的实现，该命令选择文档中的所有文本。 如果没有要选择的文本，则禁用该命令。

   如果选择实现此命令，我们建议您使用此命令 ID。

- ID_EDIT_UNDO撤消最后一个操作。

   目前没有此命令的标准实现。 您必须为每个`CView`派生类实现此。

   `CEditView`使用此 命令的实现`CEdit::Undo`。 如果返回 FALSE，`CEdit::CanUndo`则该命令将禁用。

   如果选择实现此命令，我们建议您使用此命令 ID。

- ID_EDIT_REDO重做最后一个操作。

   目前没有此命令的标准实现。 您必须为每个`CView`派生类实现此。

   如果选择实现此命令，我们建议您使用此命令 ID。

- ID_WINDOW_NEW 在活动文档上打开另一个窗口。

   `CMDIFrameWnd::OnWindowNew`通过使用当前文档的文档模板创建包含当前文档的另一个视图的另一个框架，实现这一强大的功能。

   与大多数多个文档接口 （MDI） 窗口菜单命令一样，如果没有活动的 MDI 子窗口，则禁用该命令。

   不建议自定义此命令处理程序。 如果要提供创建其他视图或框架窗口的命令，最好创建自己的命令。 可以从克隆代码`CMDIFrameWnd::OnWindowNew`并将其修改为特定框架并查看您喜欢的类。

- ID_WINDOW_ARRANGE排列 MDI 窗口底部的图标。

   `CMDIFrameWnd`在实现帮助器函数`OnMDIWindowCmd`中实现此标准 MDI 命令。 此帮助程序将命令 ID 映射到 MDI Windows 消息，因此可以共享大量代码。

   与大多数 MDI 窗口菜单命令一样，如果没有活动的 MDI 子窗口，则该命令将禁用。

   不建议自定义此命令处理程序。

- ID_WINDOW_CASCADE级联窗口，以便它们重叠。

   `CMDIFrameWnd`在实现帮助器函数`OnMDIWindowCmd`中实现此标准 MDI 命令。 此帮助程序将命令 ID 映射到 MDI Windows 消息，因此可以共享大量代码。

   与大多数 MDI 窗口菜单命令一样，如果没有活动的 MDI 子窗口，则该命令将禁用。

   不建议自定义此命令处理程序。

- ID_WINDOW_TILE_HORZ水平磁贴窗口。

   此命令在ID_WINDOW_CASCADE中`CMDIFrameWnd`实现，但操作使用不同的 MDI Windows 消息。

   应为应用程序选择默认磁贴方向。 为此，可以将窗口"Tile"菜单项的 ID 更改为ID_WINDOW_TILE_HORZ或ID_WINDOW_TILE_VERT。

- ID_WINDOW_TILE_VERT垂直磁贴窗口。

   此命令在ID_WINDOW_CASCADE中`CMDIFrameWnd`实现，但操作使用不同的 MDI Windows 消息。

   应为应用程序选择默认磁贴方向。 为此，可以将窗口"Tile"菜单项的 ID 更改为ID_WINDOW_TILE_HORZ或ID_WINDOW_TILE_VERT。

- ID_WINDOW_SPLIT键盘接口到拆分器。

   `CView`处理实现的此`CSplitterWnd`命令。 如果视图是拆分器窗口的一部分，则此命令将委派给实现函数`CSplitterWnd::DoKeyboardSplit`。 这将将拆分器置于允许键盘用户拆分或取消拆分拆分窗口的模式。

   如果视图不在拆分器中，则禁用此命令。

   不建议自定义此命令处理程序。

- ID_APP_ABOUT调用"关于"对话框。

   应用程序"关于"框没有标准实现。 默认 AppWizard 创建的应用程序将为应用程序创建自定义对话框类，并将其用作"关于"框。 AppWizard 还将编写处理此命令并调用对话框的琐碎命令处理程序。

   您几乎总是实现此命令。

- ID_APP_EXIT退出应用程序。

   `CWinApp::OnAppExit`通过向应用程序的主窗口发送WM_CLOSE消息来处理此命令。 应用程序的标准关闭（提示脏文件等）由`CFrameWnd`实现处理。

   不建议自定义此命令处理程序。 建议重写`CWinApp::SaveAllModified`或`CFrameWnd`关闭逻辑。

   如果选择实现此命令，我们建议您使用此命令 ID。

- ID_HELP_INDEX 列表 从 中提供帮助主题。HLP 文件。

    > [!NOTE]
    >  您必须将其连接到`CWinApp`派生类的消息映射才能启用此功能。

   `CWinApp::OnHelpIndex`通过琐碎地调用`CWinApp::WinHelp`来处理此命令。

   不建议自定义此命令处理程序。

- ID_HELP_USING 显示有关如何使用帮助的帮助。

    > [!NOTE]
    >  您必须将其连接到`CWinApp`派生类的消息映射才能启用此功能。

   `CWinApp::OnHelpUsing`通过琐碎地调用`CWinApp::WinHelp`来处理此命令。

   不建议自定义此命令处理程序。

- ID_CONTEXT_HELP进入 SHIFT-F1 帮助模式。

    > [!NOTE]
    >  您必须将其连接到`CWinApp`派生类的消息映射才能启用此功能。

   `CWinApp::OnContextHelp`通过设置帮助模式游标、输入模式循环并等待用户选择窗口以获取有关帮助来处理此命令。 有关 MFC 帮助实施的更多信息[，请参阅技术说明 28。](../mfc/tn028-context-sensitive-help-support.md)

   不建议自定义此命令处理程序。

- ID_HELP 在当前上下文上提供帮助

    > [!NOTE]
    >  您必须将其连接到`CWinApp`派生类的消息映射才能启用此功能。

   `CWinApp::OnHelp`通过获取当前应用程序上下文的正确帮助上下文来处理此命令。 这将处理简单的 F1 帮助、消息框上的帮助等。 有关 MFC 帮助实施的更多详细信息，请参阅[技术说明 28。](../mfc/tn028-context-sensitive-help-support.md)

   不建议自定义此命令处理程序。

- ID_DEFAULT_HELP 显示上下文的默认帮助

    > [!NOTE]
    >  您必须将其连接到`CWinApp`派生类的消息映射才能启用此功能。

   此命令通常映射到`CWinApp::OnHelpIndex`。

   如果需要默认帮助和帮助索引之间的区别，则可以提供不同的命令处理程序。

- ID_NEXT_PANE转到下一个窗格

   `CView`处理实现的此`CSplitterWnd`命令。 如果视图是拆分器窗口的一部分，则此命令将委派给实现函数`CSplitterWnd::OnNextPaneCmd`。 这将将活动视图移动到拆分器中的下一个窗格。

   如果视图不在拆分器中，或者没有下一个窗格可转到，则禁用此命令。

   不建议自定义此命令处理程序。

- ID_PREV_PANE 转到上一个窗格

   `CView`处理实现的此`CSplitterWnd`命令。 如果视图是拆分器窗口的一部分，则此命令将委派给实现函数`CSplitterWnd::OnNextPaneCmd`。 这将将活动视图移动到拆分器中的上一个窗格。

   如果视图不在拆分器中，或者没有要转到的上一个窗格，则禁用此命令。

   不建议自定义此命令处理程序。

- ID_OLE_INSERT_NEW 插入新的 OLE 对象

   目前没有此命令的标准实现。 您必须为`CView`派生类实现此目的，才能在当前选择中插入新的 OLE 项/对象。

   所有 OLE 客户端应用程序都应实现此命令。 使用 OLE 选项的 AppWizard 将在视图类`OnInsertObject`中创建您必须完成的骨架实现。

   有关此命令的完整实现，请参阅 MFC OLE[示例 OCLIENT](../overview/visual-cpp-samples.md)示例。

- ID_OLE_EDIT_LINKS编辑 OLE 链接

   `COleDocument`使用提供 MFC 的标准 OLE 链接对话框的实现来处理此命令。 此对话框的实现通过`COleLinksDialog`类访问。 如果当前文档不包含任何链接，则该命令将禁用。

   不建议自定义此命令处理程序。

- ID_OLE_VERB_FIRST...OLE 动词的 ID 范围

   `COleDocument`对于当前选定的 OLE 项/对象支持的谓词，使用此命令 ID 范围。 这必须是一个范围，因为给定的 OLE 项/对象类型可以支持零个或多个自定义谓词。 在应用程序的菜单中，应该有一个带有ID_OLE_VERB_FIRST ID 的菜单项。 运行程序时，菜单将使用适当的菜单谓词描述（或包含许多动词的弹出式菜单）进行更新。 OLE 菜单的管理由`AfxOleSetEditMenu`处理，由 在此命令的更新命令 UI 处理程序中完成。

   在此范围内，没有用于处理每个命令 ID 的显式命令处理程序。 `COleDocument::OnCmdMsg`重写以捕获此范围内的所有命令指示，将它们转换为零基动词数字，并启动该谓词的服务器（使用`COleClientItem::DoVerb`）。

   不建议自定义或使用此命令 ID 范围。

- ID_VIEW_TOOLBAR打开和关闭工具栏

   `CFrameWnd`处理此命令和更新命令 UI 处理程序以切换工具栏的可见状态。 工具栏必须是框架的子窗口，其子窗口 ID 为 AFX_IDW_TOOLBAR。 命令处理程序实际上切换工具栏窗口的可见性。 `CFrameWnd::RecalcLayout`用于使用处于新状态的工具栏重绘框架窗口。 当工具栏可见时，更新命令 UI 处理程序将检查菜单项。

   不建议自定义此命令处理程序。 如果要添加其他工具栏，将希望克隆和修改此命令的命令处理程序和更新命令 UI 处理程序。

- ID_VIEW_STATUS_BAR打开和关闭状态栏

   此命令在ID_VIEW_TOOLBAR中`CFrameWnd`实现，但使用不同的子窗口 ID （AFX_IDW_STATUS_BAR）。

## <a name="update-only-command-handlers"></a>仅更新命令处理程序

多个标准命令指示号用作状态栏中的指示器。 它们使用相同的更新命令 UI 处理机制来在应用程序空闲期间显示其当前可视状态。 由于用户无法选择它们（即不能推送状态栏窗格），因此对这些命令的 ON_COMMAND处理程序没有意义。

- ID_INDICATOR_CAPS ：CAP 锁指示灯。

- ID_INDICATOR_NUM ：NUM 锁定指示器。

- ID_INDICATOR_SCRL ： SCRL 锁定指示灯。

- ID_INDICATOR_KANA ： KANA 锁定指示器（仅适用于日本系统）。

这三个功能都在 中`CFrameWnd::OnUpdateKeyIndicator`实现，一个使用命令 ID 映射到相应虚拟密钥的实现帮助程序。 公共实现启用或禁用（对于禁用的状态窗格 = 无文本），`CCmdUI`具体取决于相应的虚拟密钥当前是否锁定。

不建议自定义此命令处理程序。

- ID_INDICATOR_EXT ： EX"选择指标"。

- ID_INDICATOR_OVR ： OVeR 打击指示器。

- ID_INDICATOR_REC ： 重新调整指示器。

目前，这些指标没有标准实施。

如果您选择实现这些指标，我们建议您使用这些指标 ID 并保持状态栏中的指标顺序（即按此顺序排列：EXT、CAP、NUM、SCRL、OVR、REC）。

## <a name="see-also"></a>另请参阅

[技术说明（按编号）](../mfc/technical-notes-by-number.md)<br/>
[按类别分类的技术说明](../mfc/technical-notes-by-category.md)
