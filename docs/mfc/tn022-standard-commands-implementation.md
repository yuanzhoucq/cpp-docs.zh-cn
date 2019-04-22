---
title: TN022:标准命令实现
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
ms.openlocfilehash: 8d568760cc75a4c1f2ddb6dd88108cc830783194
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58775826"
---
# <a name="tn022-standard-commands-implementation"></a>TN022:标准命令实现

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

此注释描述 MFC 2.0 提供的标准命令实现方式。 读取[技术说明 21](../mfc/tn021-command-and-message-routing.md)第一个因为它说明了用来实现的许多标准命令的机制。

此说明假定你了解 MFC 体系结构、 Api 和常见的编程做法。 有案可稽以及未记录"的实现仅"介绍了 Api。 这不是一个位置，若要开始学习有关的功能或如何在 MFC 中编程。 到视觉对象，请参阅C++更多常规信息和有关有案可稽的 Api 的详细信息。

## <a name="the-problem"></a>问题

MFC 标头文件 AFXRES 中定义多个标准命令 Id。H. 这些命令的框架支持而异。 了解 framework 类在何处以及如何处理这些命令不会仅显示您如何框架的内部工作原理，但提供了有关如何自定义的标准实现，并讲授实现的几种方法有用信息自己命令的处理程序。

## <a name="contents-of-this-technical-note"></a>此技术说明的内容

每个命令 ID 是两个部分中所述：

- 标题： 跟命令 （例如，"将保存当前文档"） 的目的的符号名称的命令 ID (例如，ID_FILE_SAVE) 是由冒号分隔。

- 描述哪些类的一个或多个段落实现该命令，并默认实现的功能

大多数默认命令实现被 prewired 框架的基类消息映射中。 有一些需要在派生类中的显式绑定的命令实现。 描述了这些内容在"说明"下。 如果在应用程序向导中选择正确的选项，您将这些默认处理程序的连接为您生成主干应用程序中。

## <a name="naming-convention"></a>命名约定

标准命令遵循简单的命名约定，我们建议尽可能使用。 大多数标准命令都位于应用程序的菜单栏中的标准位置。 该命令的符号名称以"ID_"跟菜单项名称的标准的弹出菜单名称后跟开头。 以使用下划线断字的大写形式的符号名称。 对于不具有标准菜单项名称的命令，从"ID_"(例如，ID_NEXT_PANE) 开始定义逻辑命令名称。

我们使用前缀"ID_"指示旨在将绑定到菜单项、 工具栏按钮或其他命令用户界面对象的命令。 处理"ID_"命令的命令处理程序应使用 MFC 命令体系结构的 ON_COMMAND 和 ON_UPDATE_COMMAND_UI 的机制。

我们建议不遵循命令体系结构并需要特定于菜单的代码，以启用和禁用这些菜单项使用标准的"IDM_"前缀。 当然应菜单特定命令的数目很小，因为以下 MFC 命令体系结构不仅可使命令处理程序功能更强大 （因为它们也适用于工具栏） 但使命令处理程序代码可重用。

## <a name="id-ranges"></a>ID 范围

请参阅[技术说明 20](../mfc/tn020-id-naming-and-numbering-conventions.md)有关的详细信息的 MFC 中的 ID 范围的使用。

在范围内 0xE000 到 0xEFFF 在 MFC 标准命令。 请不要依赖这些 Id 的特定值，因此均将在未来版本的库中进行。

你的应用程序应在范围内 0x8000 到 0xDFFF 定义其命令。

## <a name="standard-command-ids"></a>标准命令 Id

对于每个命令 ID，没有可在文件的提示中找到一个标准消息行提示字符串。RC。 该菜单提示字符串 ID 必须是相同的命令 id。

- ID_FILE_NEW 创建一个新的/空文档。

    > [!NOTE]
    >  你必须连接到你`CWinApp`的派生类的消息映射，以启用此功能。

   `CWinApp::OnFileNew` 在应用程序中实现此命令以不同的方式根据文档模板的数量。 如果只有一个`CDocTemplate`，`CWinApp::OnFileNew`将创建该类型，以及适当的框架和视图类的新文档。

   如果有多个`CDocTemplate`，`CWinApp::OnFileNew`会提示用户一个对话框 (AFX_IDD_NEWTYPEDLG)，让他们选择哪些文档要使用的类型。 所选`CDocTemplate`用于创建文档。

   ID_FILE_NEW 的一个常见的自定义是提供不同的域和文档类型的更多图形的选择。 在这种情况下可以实现你自己`CMyApp::OnFileNew`并将它放在消息映射而不是`CWinApp::OnFileNew`。 没有无需调用基类实现。

   ID_FILE_NEW 的另一个常见的自定义是用于创建每种类型的文档提供单独的命令。 在这种情况下应定义新的命令 Id，例如 ID_FILE_NEW_CHART 和 ID_FILE_NEW_SHEET。

- ID_FILE_OPEN 打开现有文档。

    > [!NOTE]
    >  你必须连接到你`CWinApp`的派生类的消息映射，以启用此功能。

   `CWinApp::OnFileOpen` 具有非常简单的实现调用`CWinApp::DoPromptFileName`跟`CWinApp::OpenDocumentFile`要打开的文件的文件或路径名称。 `CWinApp`实现例程`DoPromptFileName`显示标准文件打开对话框，并从当前的文档模板中获取的文件扩展名将其填充。

   ID_FILE_OPEN 的一个常见的自定义项是自定义文件打开对话框或添加其他文件筛选器。 此自定义的建议的方法是将替换为你自己的文件打开对话框中，并调用的默认实现`CWinApp::OpenDocumentFile`文档的文件或路径名称。 没有无需调用类的基类。

- ID_FILE_CLOSE 关闭当前打开的文档。

   `CDocument::OnFileClose` 调用`CDocument::SaveModified`提示用户保存文档，如果它已被修改，然后调用`OnCloseDocument`。 在中完成所有关闭逻辑，包括销毁文档，`OnCloseDocument`例程。

    > [!NOTE]
    >  ID_FILE_CLOSE 以不同的方式从 WM_CLOSE 消息或 SC_CLOSE 系统命令发送到的文档框架窗口的行为。 关闭窗口将关闭文档，仅当这就是显示文档的最后一个框架窗口。 关闭文档与 ID_FILE_CLOSE 不会仅关闭文档，但将关闭显示文档的所有框架窗口。

- ID_FILE_SAVE 保存当前文档。

   该实现使用一个帮助器例程`CDocument::DoSave`两个用于`OnFileSave`和`OnFileSaveAs`。 如果你保存未保存过的文档 （即，它没有路径名称，如 filenew） 或从只读的文档，读取`OnFileSave`逻辑将表现基本一样 ID_FILE_SAVE_AS 命令，并要求用户提供新的文件名称. 打开文件并进行保存的实际过程是通过虚拟函数`OnSaveDocument`。

   有两个自定义 ID_FILE_SAVE 的常见原因。 对于未保存的文档，只需删除 ID_FILE_SAVE 菜单项和工具栏按钮从用户界面。 此外，请确保您永远不会更新您的文档 (即，永远不会调用`CDocument::SetModifiedFlag`) 和框架将永远不会导致要保存的文档。 对于将保存到某一位置以外的磁盘文件的文档，定义新的命令为该操作。

   情况下`COleServerDoc`，ID_FILE_SAVE 用于保存文件 （适用于常规文档） 和 （适用于 embedded 文档） 的文件更新。

   如果你的文档数据存储在单个磁盘文件，但不想要使用默认值`CDocument`序列化实现，则应重写`CDocument::OnSaveDocument`而不是`OnFileSave`。

- ID_FILE_SAVE_AS 保存当前文档在不同的文件名称。

   `CDocument::OnFileSaveAs`实现使用相同`CDocument::DoSave`帮助器例程作为`OnFileSave`。 `OnFileSaveAs`如果文档不有任何文件名保存之前，只需作为 ID_FILE_SAVE 处理的命令。 `COleServerDoc::OnFileSaveAs` 实现保存正常文档数据文件或保存服务器文档，表示作为单独的文件的一些其他应用程序中嵌入的 OLE 对象的逻辑。

   如果自定义 ID_FILE_SAVE 的逻辑，您可能希望自 ID_FILE_SAVE_AS 定义以类似的方式，或者"另存为"操作可能不适用于您的文档。 如果不需要可以从菜单栏删除菜单项。

- ID_FILE_SAVE_COPY_AS 保存副本当前文档以新名称。

   `COleServerDoc::OnFileSaveCopyAs`实现是非常类似于`CDocument::OnFileSaveAs`，只不过文档对象不"附加"到基础文件后保存。 也就是说，如果内存中修改该文档""在保存之前，它是仍然"修改"。 此外，此命令对无效的路径名称或存储在文档中的标题。

- ID_FILE_UPDATE 通知要保存嵌入的文档的容器。

   `COleServerDoc::OnUpdateDocument`实现只需 notifiies 应保存嵌入的容器。 然后，容器以便保存嵌入的对象调用相应 OLE Api。

- ID_FILE_PAGE_SETUP 调用特定于应用程序页设置/布局对话框。

   目前此对话框中，没有标准和框架有此命令没有默认实现。

   如果您选择实现此命令，我们建议使用此命令 id。

- ID_FILE_PRINT_SETUP 调用标准的打印设置对话框。

    > [!NOTE]
    >  你必须连接到你`CWinApp`的派生类的消息映射，以启用此功能。

   此命令可调用的标准打印设置对话框中，则允许用户自定义打印机和打印的设置至少本文档或最多的所有文档在此应用程序。 必须使用控制面板若要更改整个系统的默认打印机设置。

   `CWinApp::OnFilePrintSetup` 具有非常简单的实现创建`CPrintDialog`对象并调用`CWinApp::DoPrintDialog`实现函数。 这将设置应用程序默认打印机设置。

   常见的需要自定义此命令是允许为每个文档打印机设置，应当存储在一起时保存的文档。 若要执行此操作应添加中的消息映射处理程序您`CDocument`类，该类创建`CPrintDialog`对象，具有相应的打印机属性对其进行初始化 (通常*hDevMode*和*hDevNames*)，调用`CPrintDialog::DoModal`，并保存已更改的打印机设置。 强大的实现，您应该看一下如何实现的`CWinApp::DoPrintDialog`来检测错误和`CWinApp::UpdatePrinterSelection`面对的合理的默认值和跟踪系统级打印机更改。

- 当前文档的 ID_FILE_PRINT 标准打印

    > [!NOTE]
    >  你必须连接到你`CView`的派生类的消息映射，以启用此功能。

   此命令将打印当前文档，或更准确地说开始打印进程，这就需要调用标准打印对话框并运行打印引擎。

   `CView::OnFilePrint` 实现此命令，并主要打印循环。 调用虚拟`CView::OnPreparePrinting`到具有打印对话框中的用户的提示。 它然后准备要转到打印机的输出 DC，将打开打印进度对话框 (AFX_IDD_PRINTDLG)，并发送`StartDoc`转义到打印机。 `CView::OnFilePrint` 此外包含主要面向页面的打印循环。 对于每个页上，它调用的虚拟`CView::OnPrepareDC`跟`StartPage`转义和调用虚拟`CView::OnPrint`该页。 完成后，虚拟`CView::OnEndPrinting`调用时，并在打印进度对话框关闭。

   MFC 打印体系结构旨在中打印和打印预览为许多不同的方式挂接。 通常会发现各种`CView`适合任何面向页面的打印任务的可重写函数。 仅对于非页面方向输出使用打印机的应用程序，您应发现需要替换 ID_FILE_PRINT 实现。

- 当前文档 ID_FILE_PRINT_PREVIEW 输入打印预览模式。

    > [!NOTE]
    >  你必须连接到你`CView`的派生类的消息映射，以启用此功能。

   `CView::OnFilePrintPreview` 通过调用有案可稽的帮助器函数开始打印预览模式`CView::DoPrintPreview`。 `CView::DoPrintPreview` 就像是为打印预览循环的主引擎`OnFilePrint`是打印循环的主引擎。

   打印预览操作可以自定义在不同的方式传递到不同的参数`DoPrintPreview`。 请参阅[技术注意 30](../mfc/tn030-customizing-printing-and-print-preview.md)，其中讨论了一些打印预览的详细信息以及如何自定义它。

- ID_FILE_MRU_FILE1...FILE16 一系列命令 Id 文件 MRU**列表**。

   `CWinApp::OnUpdateRecentFileMenu` 是的更新命令 UI 处理程序是 ON_UPDATE_COMMAND_UI 机制的更高级用法之一。 在菜单资源中，您只需使用 ID ID_FILE_MRU_FILE1 定义的单个菜单项。 该菜单项保持最初禁用状态。

   随着 MRU 列表的增长，更多菜单项添加到列表。 标准`CWinApp`实现默认为四个最近使用的文件的标准限制。 您可以通过调用来更改默认`CWinApp::LoadStdProfileSettings`具有更大或较小值。 MRU 列表存储在应用程序。INI 文件。 在应用程序的加载列表`InitInstance`函数，如果调用`LoadStdProfileSettings`，和你的应用程序退出时保存。 MRU 更新命令 UI 处理程序也将转换为绝对路径的文件菜单上显示的相对路径。

   `CWinApp::OnOpenRecentFile` 是的 ON_COMMAND 处理程序执行的实际命令。 只需获取的文件的名称从 MRU 列表和调用`CWinApp::OpenDocumentFile`，打开该文件，并且更新 MRU 列表的所有工作。

   不建议使用此命令处理程序的自定义。

- ID_EDIT_CLEAR 清除当前选定内容

   当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生的类。

   `CEditView` 提供的此命令使用实现`CEdit::Clear`。 如果没有当前选定内容，将禁用该命令。

   如果您选择实现此命令，我们建议使用此命令 id。

- ID_EDIT_CLEAR_ALL 清除整个文档。

   当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生的类。

   如果您选择实现此命令，我们建议使用此命令 id。 请参阅 MFC 教程示例[SCRIBBLE](../overview/visual-cpp-samples.md)有关的示例实现。

- ID_EDIT_COPY 将当前选定内容复制到剪贴板。

   当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生的类。

   `CEditView` 提供的此命令，将当前所选的文本复制到剪贴板上形式 CF_TEXT 使用实现`CEdit::Copy`。 如果没有当前选定内容，将禁用该命令。

   如果您选择实现此命令，我们建议使用此命令 id。

- ID_EDIT_CUT 剪切到剪贴板当前所选内容。

   当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生的类。

   `CEditView` 提供的此命令，将当前所选的文本剪切到剪贴板作为 CF_TEXT 使用实现`CEdit::Cut`。 如果没有当前选定内容，将禁用该命令。

   如果您选择实现此命令，我们建议使用此命令 id。

- ID_EDIT_FIND 开始查找操作中，将显示无模式查找对话框。

   当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生的类。

   `CEditView` 提供此命令，调用实现帮助器函数的实现`OnEditFindReplace`使用并将以前的查找/替换设置存储在私有实现变量。 `CFindReplaceDialog`类用于管理无模式对话框用于提示用户。

   如果您选择实现此命令，我们建议使用此命令 id。

- ID_EDIT_PASTE 插入当前的剪贴板内容。

   当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生的类。

   `CEditView` 提供的此命令，将替换为所选的文本使用当前的剪贴板数据复制实现`CEdit::Paste`。 如果没有，则将禁用该命令没有**CF_TEXT**剪贴板中。

   `COleClientDoc` 此命令只提供更新命令 UI 处理程序。 如果剪贴板不包含可嵌入 OLE 项/对象，该命令将被禁用。 你负责编写实际的命令来执行实际粘贴的处理程序。 如果 OLE 应用程序还可以粘贴其他格式，则应提供视图或文档中的你自己更新命令 UI 处理程序 (即，某个位置之前`COleClientDoc`命令目标路由中)。

   如果您选择实现此命令，我们建议使用此命令 id。

   用于替换标准 OLE 实现，使用`COleClientItem::CanPaste`。

- ID_EDIT_PASTE_LINK 插入从当前的剪贴板内容的链接。

   当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生的类。

   `COleDocument` 此命令只提供更新命令 UI 处理程序。 如果剪贴板不包含可链接 OLE 项/对象，该命令将被禁用。 你负责编写实际的命令来执行实际粘贴的处理程序。 如果 OLE 应用程序还可以粘贴其他格式，则应提供视图或文档中的你自己更新命令 UI 处理程序 (即，某个位置之前`COleDocument`命令目标路由中)。

   如果您选择实现此命令，我们建议使用此命令 id。

   用于替换标准 OLE 实现，使用`COleClientItem::CanPasteLink`。

- ID_EDIT_PASTE_SPECIAL 插入选项与当前的剪贴板内容。

   当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生的类。 MFC 不提供此对话框。

   如果您选择实现此命令，我们建议使用此命令 id。

- ID_EDIT_REPEAT 重复最后一个操作。

   当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生的类。

   `CEditView` 提供此命令可重复执行最后一次的查找操作的实现。 使用最后一个查找私有实现变量。 如果不能尝试查找，将禁用该命令。

   如果您选择实现此命令，我们建议使用此命令 id。

- ID_EDIT_REPLACE 开始替换操作中，将显示替换为无模式对话框。

   当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生的类。

   `CEditView` 提供此命令，调用实现帮助器函数的实现`OnEditFindReplace`使用并将以前的查找/替换设置存储在私有实现变量。 `CFindReplaceDialog`类用于管理无模式对话框，提示用户。

   如果您选择实现此命令，我们建议使用此命令 id。

- ID_EDIT_SELECT_ALL 选择整个文档。

   当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生的类。

   `CEditView` 提供此命令，选择所有文本文档中的实现。 如果不未选择任何文本，该命令将禁用。

   如果您选择实现此命令，我们建议使用此命令 id。

- ID_EDIT_UNDO 撤消上一个操作。

   当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生的类。

   `CEditView` 提供的此实现命令，使用`CEdit::Undo`。 如果该命令将禁用`CEdit::CanUndo`返回 FALSE。

   如果您选择实现此命令，我们建议使用此命令 id。

- ID_EDIT_REDO 重做最后一次操作。

   当前没有此命令的标准实现。 您必须为每个实现此`CView`-派生的类。

   如果您选择实现此命令，我们建议使用此命令 id。

- ID_WINDOW_NEW 打开另一个窗口，在活动文档。

   `CMDIFrameWnd::OnWindowNew` 通过使用当前文档的文档模板创建另一个框架，其中包含当前文档的另一个视图来实现此功能强大的功能。

   大多数多文档界面 (MDI) 窗口菜单与命令一样，如果没有活动的 MDI 子窗口已禁用命令。

   不建议使用此命令处理程序的自定义。 如果你想要提供创建其他视图或框架窗口的命令，可能会更好发明您自己的命令。 可以克隆中的代码`CMDIFrameWnd::OnWindowNew`并修改它为你喜欢的特定的框架和视图类。

- 在 MDI 窗口的底部 ID_WINDOW_ARRANGE 排列图标。

   `CMDIFrameWnd` 实现帮助器函数中实现此标准的 MDI 命令`OnMDIWindowCmd`。 此帮助器将命令 Id 映射到 MDI Windows 消息，因此可共享大量代码。

   如大多数 MDI 窗口菜单命令，如果没有活动的 MDI 子窗口已禁用命令。

   不建议使用此命令处理程序的自定义。

- ID_WINDOW_CASCADE 级联窗口，以便它们重叠。

   `CMDIFrameWnd` 实现帮助器函数中实现此标准的 MDI 命令`OnMDIWindowCmd`。 此帮助器将命令 Id 映射到 MDI Windows 消息，因此可共享大量代码。

   如大多数 MDI 窗口菜单命令，如果没有活动的 MDI 子窗口已禁用命令。

   不建议使用此命令处理程序的自定义。

- ID_WINDOW_TILE_HORZ 磁贴 windows 水平。

   此命令中实现`CMDIFrameWnd`一样 ID_WINDOW_CASCADE，但不同的 MDI Windows 消息用于该操作。

   为应用程序，应选择默认磁贴方向。 可以通过更改为 ID_WINDOW_TILE_HORZ 或 ID_WINDOW_TILE_VERT 窗口"磁贴"菜单项的 ID 来执行此操作。

- ID_WINDOW_TILE_VERT 磁贴 windows 垂直。

   此命令中实现`CMDIFrameWnd`一样 ID_WINDOW_CASCADE，但不同的 MDI Windows 消息用于该操作。

   为应用程序，应选择默认磁贴方向。 可以通过更改为 ID_WINDOW_TILE_HORZ 或 ID_WINDOW_TILE_VERT 窗口"磁贴"菜单项的 ID 来执行此操作。

- ID_WINDOW_SPLIT 键盘拆分器的接口。

   `CView` 处理此命令为`CSplitterWnd`实现。 如果视图为拆分器窗口的一部分，此命令会将委托到实现函数`CSplitterWnd::DoKeyboardSplit`。 这将拆分器将允许键盘用户拆分或取消拆分的拆分器窗口的模式。

   如果该视图未在拆分器中，将禁用此命令。

   不建议使用此命令处理程序的自定义。

- ID_APP_ABOUT 调用关于对话框。

   应用程序的有关中没有标准实现。 默认应用程序向导创建的应用程序将创建你的应用程序的自定义对话框类，并将其用作有关框。 应用程序向导还将写入处理此命令，并调用对话框的简单命令处理程序。

   您几乎总是将实现此命令。

- ID_APP_EXIT 退出该应用程序。

   `CWinApp::OnAppExit` 通过向应用程序的主窗口发送 WM_CLOSE 消息来处理此命令。 由处理标准 （会提示输入脏文件，等等） 的应用程序的关闭`CFrameWnd`实现。

   不建议使用此命令处理程序的自定义。 重写`CWinApp::SaveAllModified`或`CFrameWnd`建议关闭逻辑。

   如果您选择实现此命令，我们建议使用此命令 id。

- 从 ID_HELP_INDEX 列出帮助主题。HLP 文件。

    > [!NOTE]
    >  你必须连接到你`CWinApp`的派生类的消息映射，以启用此功能。

   `CWinApp::OnHelpIndex` 处理此命令通过完全调用`CWinApp::WinHelp`。

   不建议使用此命令处理程序的自定义。

- ID_HELP_USING 显示如何使用帮助的帮助。

    > [!NOTE]
    >  你必须连接到你`CWinApp`的派生类的消息映射，以启用此功能。

   `CWinApp::OnHelpUsing` 处理此命令通过完全调用`CWinApp::WinHelp`。

   不建议使用此命令处理程序的自定义。

- ID_CONTEXT_HELP 进入 SHIFT-F1 帮助模式。

    > [!NOTE]
    >  你必须连接到你`CWinApp`的派生类的消息映射，以启用此功能。

   `CWinApp::OnContextHelp` 通过设置帮助模式游标中，输入模式循环并等待用户选择窗口获取有关帮助处理此命令。 请参阅[技术说明 28](../mfc/tn028-context-sensitive-help-support.md)有关 MFC 帮助实现的更多详细信息。

   不建议使用此命令处理程序的自定义。

- ID_HELP 提供当前上下文的帮助

    > [!NOTE]
    >  你必须连接到你`CWinApp`的派生类的消息映射，以启用此功能。

   `CWinApp::OnHelp` 通过获取正确帮助上下文的当前应用程序上下文来处理此命令。 这处理简单的 F1 帮助，帮助在消息框上，依此类推。 请参阅[技术说明 28](../mfc/tn028-context-sensitive-help-support.md) MFC 的详细信息帮助实现。

   不建议使用此命令处理程序的自定义。

- ID_DEFAULT_HELP 显示默认上下文的帮助

    > [!NOTE]
    >  你必须连接到你`CWinApp`的派生类的消息映射，以启用此功能。

   此命令通常映射到`CWinApp::OnHelpIndex`。

   如果需要默认帮助和帮助索引之间的差异，则可以提供不同的命令处理程序。

- ID_NEXT_PANE 将转到下一个窗格

   `CView` 处理此命令为`CSplitterWnd`实现。 如果视图为拆分器窗口的一部分，此命令会将委托到实现函数`CSplitterWnd::OnNextPaneCmd`。 这将移到下一个窗格拆分器中活动的视图。

   如果视图不在拆分器，或转到没有下一个窗格，将禁用此命令。

   不建议使用此命令处理程序的自定义。

- ID_PREV_PANE 将转到上一个窗格

   `CView` 处理此命令为`CSplitterWnd`实现。 如果视图为拆分器窗口的一部分，此命令会将委托到实现函数`CSplitterWnd::OnNextPaneCmd`。 这将活动视图拆分器中的上一个窗格。

   如果视图不在拆分器，或转到没有上一个窗格，将禁用此命令。

   不建议使用此命令处理程序的自定义。

- ID_OLE_INSERT_NEW 将插入新的 OLE 对象

   当前没有此命令的标准实现。 您必须实现此为您`CView`-派生类，以在当前选定内容处插入一个新的 OLE 项/对象。

   所有 OLE 客户端应用程序应都实现此命令。 应用程序向导，使用 OLE 选项时，将创建一个主干实现的`OnInsertObject`必须完成在视图类中。

   请参阅 MFC OLE 示例[OCLIENT](../overview/visual-cpp-samples.md)示例中为此命令的完整实现。

- ID_OLE_EDIT_LINKS 编辑 OLE 链接

   `COleDocument` 通过使用标准的 OLE 链接对话框的 MFC 提供实现来处理此命令。 通过访问此对话框中的实现`COleLinksDialog`类。 如果当前文档不包含任何链接，则禁用该命令。

   不建议使用此命令处理程序的自定义。

- ID_OLE_VERB_FIRST...OLE 谓词的的最后一个 ID 范围

   `COleDocument` 此命令 ID 范围用于当前所选 OLE 项/对象支持的谓词。 这必须是一个范围，因为一个给定的 OLE 项/对象类型可支持零个或多个自定义谓词。 在应用程序的菜单中，应具有一个菜单项与 ID_OLE_VERB_FIRST ID。 运行程序时，将使用相应的菜单动词描述 （或弹出菜单与多个谓词） 更新菜单。 OLE 菜单的管理工作由`AfxOleSetEditMenu`，完成此命令的更新命令 UI 处理程序中。

   没有显式命令处理程序来处理每个在此范围内的命令 ID。 `COleDocument::OnCmdMsg` 重写以捕获在此范围内的所有命令 Id，将其转换为从零开始的谓词数字，并启动该动词的服务器 (使用`COleClientItem::DoVerb`)。

   不建议自定义项或其他使用此命令 ID 范围。

- ID_VIEW_TOOLBAR 打开和关闭之间切换工具栏

   `CFrameWnd` 处理此命令，并更新命令 UI 处理程序切换工具栏的可见状态。 工具栏必须与子窗口 ID 的 AFX_IDW_TOOLBAR 帧的子窗口。 命令处理程序实际上会切换工具栏窗口的可见性。 `CFrameWnd::RecalcLayout` 用于在其新的状态重绘框架窗口与工具栏。 工具栏可见时，更新命令 UI 处理程序会检查菜单项。

   不建议使用此命令处理程序的自定义。 如果你想要添加的其他工具栏，你将想要克隆并修改的命令处理程序和此命令的更新命令 UI 处理程序。

- ID_VIEW_STATUS_BAR 打开和关闭之间切换状态栏

   此命令中实现`CFrameWnd`一样 ID_VIEW_TOOLBAR，除 ID (AFX_IDW_STATUS_BAR) 使用一个不同的子窗口。

## <a name="update-only-command-handlers"></a>仅更新命令处理程序

多个标准命令 Id 将用作在状态栏中的指示器。 这些使用相同更新命令 UI 处理机制以在应用程序空闲时显示其当前的可视状态。 由于用户无法选择 （即，不能推送状态栏窗格），然后它就完全没有必要让 ON_COMMAND 处理程序，为这些命令 Id。

- ID_INDICATOR_CAPS:CAP 锁指示符。

- ID_INDICATOR_NUM:NUM lock 指示器。

- ID_INDICATOR_SCRL:SCRL 锁指示符。

- ID_INDICATOR_KANA:假名锁定 （仅适用于日语系统） 的指示符。

在中实现所有这三个这些`CFrameWnd::OnUpdateKeyIndicator`，使用命令 ID 映射到相应的虚拟键的实现帮助器。 常见实现启用或禁用 （已禁用的状态窗格 = 无文本）`CCmdUI`具体取决于是否适当虚拟键当前被锁定的对象。

不建议使用此命令处理程序的自定义。

- ID_INDICATOR_EXT:扩展选择指示器。

- ID_INDICATOR_OVR:替换指示器。

- ID_INDICATOR_REC:录制指示器。

目前这些指示符没有标准实现。

如果您选择实现这些指示符，我们建议使用这些指示器 Id 和维护在状态栏中的指标的顺序 (即，按以下顺序：EXT，CAP、 NUM、 SCRL、 改写，REC）。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
