---
title: TN041:-OLE1 迁移到 MFC-OLE 2
ms.date: 10/18/2018
f1_keywords:
- vc.mfc.ole
helpviewer_keywords:
- OLE1 [MFC]
- migrating OLE1 to OLE2
- migration [MFC], OLE1 to OLE2
- OLE2 [MFC]
- porting OLE1 to OLE2
- converting OLE1 to OLE2
- upgrading Visual C++ applications [MFC], OLE1 to OLE2
- TN041
ms.assetid: 67f55552-4b04-4ddf-af0b-4d9eaf5da957
ms.openlocfilehash: b398a1adbf2f47343eed076f32ade5bb2564cd52
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767972"
---
# <a name="tn041-mfcole1-migration-to-mfcole-2"></a>TN041:MFC/OLE1 迁移到 MFC/OLE 2

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

## <a name="general-issues-relating-to-migration"></a>与迁移有关的常规问题

MFC 2.5（及更高版本）中的 OLE 2 类的设计目的之一是保留 MFC 2.0 中提供的针对 OLE 1.0 支持的很多相同体系结构。 因此，MFC 2.0 中的很多相同的 OLE 类仍存在于此版本的 MFC 中（`COleDocument`、`COleServerDoc`、`COleClientItem` 和 `COleServerItem`）。 此外，这些类中的很多 API 完全相同。 但是，OLE 2 与 OLE 1.0 差别很大，因此您可以预料某些细节已更改。 如果您熟悉 MFC 2.0 的 OLE1 支持，则会对 MFC 的 2.0 支持感到很亲切。

如果您要采用现有 MFC/OLE1 应用程序并向其添加 OLE 2 功能，则应该先阅读本说明。 本说明介绍了一些常规问题，可能会遇到移植到 MFC/OLE 2 将 OLE1 功能时，然后讨论移植 MFC 2.0 中包含的两个应用程序时发现的问题： MFC OLE 示例[OCLIENT](../overview/visual-cpp-samples.md)和[HIERSVR](../overview/visual-cpp-samples.md)。

## <a name="mfc-documentview-architecture-is-important"></a>MFC 文档/视图体系结构很重要

如果应用程序未使用 MFC 的文档/视图体系结构，而您要将 OLE 2 支持添加到应用程序，那么现在是时候迁移到文档/视图了。 MFC 的 OLE 2 类的很多好处只能在应用程序使用 MFC 的内置体系结构和组件时实现。

在不使用 MFC 体系结构的情况下实现服务器或容器是可以的，但不建议这样做。

## <a name="use-mfc-implementation-instead-of-your-own"></a>使用 MFC 实现而不是您自己的实现

MFC 的“罐装实现”类（如 `CToolBar`、`CStatusBar` 和 `CScrollView`）具有针对 OLE 2 支持的内置专用代码。 因此，如果您可以在应用程序中使用这些类，那么您为了使它们能够识别 OLE 而做的工作将使您受益。 同样，您可以出于这些目的在此处“定制您自己的”的类，但不建议这样做。 如果需要实现类似的功能，MFC 源代码是处理 OLE 的某些细节（尤其是在就地激活方面）的绝佳参考。

## <a name="examine-the-mfc-sample-code"></a>检查 MFC 代码示例

有很多包含 OLE 功能的 MFC 示例。 以下每个应用程序采用不同的角度来实现 OLE：

- [HIERSVR](../overview/visual-cpp-samples.md)意味着主要用于充当服务器应用程序。 它作为 MFC/OLE1 应用程序包含在 MFC 2.0 中，并且已经移植到 MFC/OLE 2，然后进行了扩展以实现在 OLE 2 中可用的很多 OLE 功能。

- [OCLIENT](../overview/visual-cpp-samples.md)这是一个独立的容器应用程序，用于从容器的角度演示很多 OLE 功能。 它也已经从 MFC 2.0 移植，然后进行了扩展以支持很多更高级的 OLE 功能，如自定义剪贴板格式和指向嵌入项的链接。

- [DRAWCLI](../overview/visual-cpp-samples.md)此应用程序实现 OLE 容器支持得与 OCLIENT 的作用，不同之处在于它是现有的面向对象的绘图程序的框架内。 它向您展示如何实现 OLE 容器支持并将其集成到现有应用程序。

- [SUPERPAD](../overview/visual-cpp-samples.md)此应用程序，同时作为独立应用程序，也是 OLE 服务器。 它实现的服务器支持是高度简化的。 其中特别重要的是，它如何使用 OLE 剪贴板服务将数据复制到剪贴板，同时使用内置于 Windows“编辑”控件的功能实现剪贴板粘贴功能。 这展示了传统 Windows API 使用方法的有趣结合以及与新的 OLE API 的集成。

有关示例应用程序的详细信息，请参阅“MFC 示例帮助”。

## <a name="case-study-oclient-from-mfc-20"></a>案例研究：MFC 2.0 中的 OCLIENT

与上述[OCLIENT](../overview/visual-cpp-samples.md)包含在 MFC 2.0 中，并实现了 OLE 使用 mfc/ole1。 最初将此应用程序转换为使用 MFC/OLE 2 类所采用的步骤如下所述。 初始移植完成后添加了很多功能，用来更好地演示 MFC/OLE 类。 此处将不会转换这些功能；有关这些高级功能的详细信息，请参阅示例本身。

> [!NOTE]
> 编译器错误和分步过程是使用 Visual C++ 2.0 创建的。 特定错误消息和位置在 Visual C++ 4.0 中可能已更改，但概念性信息仍然有效。

## <a name="getting-it-up-and-running"></a>开始运行

将 OCLIENT 示例移植到 MFC/OLE 所用的方法首先是生成该示例并修复会产生的明显编译器错误。 如果采用了 MFC 2.0 中的 OCLIENT 示例并在此版本的 MFC 下编译它，您就会发现没有太多要解决的错误。 下面按错误发生的顺序对其进行说明。

## <a name="compile-and-fix-errors"></a>编译和修复错误

```Output
\oclient\mainview.cpp(104) : error C2660: 'Draw' : function does not take 4 parameters
```

第一个错误涉及 `COleClientItem::Draw`。 在 MFC/OLE1 中，采用的参数的数量比 MFC/OLE 版本的更多。 额外的参数通常是不必要的，且通常为 NULL（如本示例所示）。 当要绘制到的 CDC 是元文件 DC 时，此版本的 MFC 可自动确定 lpWBounds 的值。 此外，pFormatDC 参数不再是必需的，因为框架将从传入的 pDC 的“特性 DC”生成一个参数。 因此，若要修复此问题，您只需移除针对绘图调用的两个额外的 NULL 参数即可。

```Output
\oclient\mainview.cpp(273) : error C2065: 'OLE_MAXNAMESIZE' : undeclared identifier
\oclient\mainview.cpp(273) : error C2057: expected constant expression
\oclient\mainview.cpp(280) : error C2664: 'CreateLinkFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
\oclient\mainview.cpp(286) : error C2664: 'CreateFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
\oclient\mainview.cpp(288) : error C2664: 'CreateStaticFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
```

导致上述错误的所有`COleClientItem::CreateXXXX`mfc/ole1 中的函数所需的传递的唯一名称来表示项。 这对于基础 OLE API 是必需的， 但在 MFC/OLE 2 中不是必需的，因为 OLE 2 不使用 DDE 作为基础通信机制（该名称已在 DDE 对话中使用）。 若要解决此问题，可以删除`CreateNewName`函数以及对它的所有引用。 了解每个 MFC/OLE 函数在此版本中期望的功能很容易，只需将光标放在调用上并按 F1 即可。

另一个重要的方面是 OLE 2 剪贴板处理。 在 OLE1 中，您使用了与 Windows 剪贴板交互的剪贴板 API。 在 OLE 2 中，可使用不同的机制达到此目的。 MFC/OLE1 API 假定剪贴板在将 `COleClientItem` 对象复制到剪贴板之前处于打开状态。 现在不再需要这样做，并且此做法会导致所有 MFC/OLE 剪贴板操作失败。 在编辑代码以移除依赖项上的同时`CreateNewName`，还应移除打开和关闭 Windows 剪贴板的代码。

```Output
\oclient\mainview.cpp(332) : error C2065: 'AfxOleInsertDialog' : undeclared identifier
\oclient\mainview.cpp(332) : error C2064: term does not evaluate to a function
\oclient\mainview.cpp(344) : error C2057: expected constant expression
\oclient\mainview.cpp(347) : error C2039: 'CreateNewObject' : is not a member of 'CRectItem'
```

这些错误导致`CMainView::OnInsertObject`处理程序。 处理“插入新对象”命令是另一个变化较大的方面。 在这种情况下，为新的 OLE 容器应用程序将原始实现与 AppWizard 提供的实现合并是最简单的。 事实上，这是可用来移植其他应用程序的方法。 通过调用在 mfc/ole1 中，显示"插入对象"对话框`AfxOleInsertDialog`函数。 在此版本，您构造`COleInsertObject`对话框对象并调用`DoModal`。 此外，使用创建新的 OLE 项**CLSID**而不是类名字符串。 最终结果应该类似于以下形式

```cpp
COleInsertDialog dlg;
if (dlg.DoModal() != IDOK)
    return;

BeginWaitCursor();

CRectItem* pItem = NULL;
TRY
{
    // First create the C++ object
    pItem = GetDocument()->CreateItem();
    ASSERT_VALID(pItem);

    // Initialize the item from the dialog data.
    if (!dlg.CreateItem(pItem))
        AfxThrowMemoryException();
            // any exception will do
    ASSERT_VALID(pItem);

    // run the object if appropriate
    if (dlg.GetSelectionType() == COleInsertDialog::createNewItem)
        pItem->DoVerb(OLEIVERB_SHOW, this);

    // update right away
    pItem->UpdateLink();
    pItem->UpdateItemRectFromServer();

    // set selection to newly inserted item
    SetSelection(pItem);
    pItem->Invalidate();
}
CATCH (CException, e)
{
    // clean up item
    if (pItem != NULL)
        GetDocument()->DeleteItem(pItem);

    AfxMessageBox(IDP_FAILED_TO_CREATE);
}
END_CATCH

EndWaitCursor();
```

> [!NOTE]
> “插入新对象”可能对您的应用程序不同：

它也是包括所需\<afxodlgs.h >，其中包含的声明`COleInsertObject`对话框类，以及 MFC 提供的其他标准对话框。

```Output
\oclient\mainview.cpp(367) : error C2065: 'OLEVERB_PRIMARY' : undeclared identifier
\oclient\mainview.cpp(367) : error C2660: 'DoVerb' : function does not take 1 parameters
```

这些错误是因为某些 OLE1 常量在 OLE 2 中已发生更改（尽管它们在概念上是相同的）导致的。 在这种情况下`OLEVERB_PRIMARY`已更改为`OLEIVERB_PRIMARY`。 在 OLE1 和 OLE 2 中，当用户双击某个项时，主谓词通常由容器执行。

此外，`DoVerb` 现在还采用了额外的参数 - 指向视图 (`CView`*) 的指针。 此参数仅用于实现“可视化编辑”（或就地激活）。 现在，您可以将该参数设置为 Null，因为您此时不想实现此功能。

若要确保框架从不尝试就地激活，您应该重写 `COleClientItem::CanActivate`，如下所示：

```cpp
BOOL CRectItem::CanActivate()
{
    return FALSE;
}
```

```Output
\oclient\rectitem.cpp(53) : error C2065: 'GetBounds' : undeclared identifier
\oclient\rectitem.cpp(53) : error C2064: term does not evaluate to a function
\oclient\rectitem.cpp(84) : error C2065: 'SetBounds' : undeclared identifier
\oclient\rectitem.cpp(84) : error C2064: term does not evaluate to a function
```

在 mfc/ole1 中，`COleClientItem::GetBounds`并`SetBounds`用来查询和操作项的范围 (`left`和`top`成员都始终是零)。 在 MFC/OLE 2 中支持此功能更直接地`COleClientItem::GetExtent`和`SetExtent`，其处理**大小**或`CSize`相反。

新的 SetItemRectToServer 的代码以及 UpdateItemRectFromServer 调用如下所示：

```cpp
BOOL CRectItem::UpdateItemRectFromServer()
{
    ASSERT(m_bTrackServerSize);
    CSize size;
    if (!GetExtent(&size))
        return FALSE;    // blank

    // map from HIMETRIC to screen coordinates
    {
        CClientDC screenDC(NULL);
        screenDC.SetMapMode(MM_HIMETRIC);
        screenDC.LPtoDP(&size);
    }
    // just set the item size
    if (m_rect.Size() != size)
    {
        // invalidate the old size/position
        Invalidate();
        m_rect.right = m_rect.left + size.cx;
        m_rect.bottom = m_rect.top + size.cy;
        // as well as the new size/position
        Invalidate();
    }
    return TRUE;
}

BOOL CRectItem::SetItemRectToServer()
{
    // set the official bounds for the embedded item
    CSize size = m_rect.Size();
    {
        CClientDC screenDC(NULL);
        screenDC.SetMapMode(MM_HIMETRIC);
        screenDC.DPtoLP(&size);
    }
    TRY
    {
        SetExtent(size);    // may do a wait
    }
    CATCH(CException, e)
    {
        return FALSE;  // links will not allow SetBounds
    }
    END_CATCH
    return TRUE;
}
```

```Output
\oclient\frame.cpp(50) : error C2039: 'InWaitForRelease' : is not a member of 'COleClientItem'
\oclient\frame.cpp(50) : error C2065: 'InWaitForRelease' : undeclared identifier
\oclient\frame.cpp(50) : error C2064: term does not evaluate to a function
```

在 mfc/ole1 中同步 API 调用从容器到服务器是*模拟*，这是因为 ole1 在本质上是异步的在许多情况下。 在处理来自用户的命令前必须检查正在进行的未处理异步调用。 Mfc/ole1 提供`COleClientItem::InWaitForRelease`函数用于执行此操作。 在 MFC/OLE 2 中，这不是必需的，因此您可以完全避免在 CMainFrame 中重写 OnCommand。

此时，OCLIENT 将执行编译和链接。

## <a name="other-necessary-changes"></a>其他必要更改

但是，几乎没有什么未完成的工作将会阻止 OCLIENT 运行。 现在修复这些问题比之后修复更好。

首先，初始化 OLE 库是必需的。 这是通过调用`AfxOleInit`从`InitInstance`:

```cpp
if (!AfxOleInit())
{
    AfxMessageBox("Failed to initialize OLE libraries");
    return FALSE;
}
```

检查虚函数中是否发生参数列表更改也是个好办法。 其中一个此类函数是在每个 MFC/OLE 容器应用程序中重写的 `COleClientItem::OnChange`。 如果查看联机帮助，您将看到添加了一个额外的“DWORD dwParam”。 新的 CRectItem::OnChange 如下所示：

```cpp
void
CRectItem::OnChange(OLE_NOTIFICATION wNotification, DWORD dwParam)
{
    if (m_bTrackServerSize && !UpdateItemRectFromServer())
    {
        // Blank object
        if (wNotification == OLE_CLOSED)
        {
            // no data received for the object - destroy it
            ASSERT(!IsVisible());
            GetDocument()->DeleteItem(this);
            return; // no update (item is gone now)
        }
    }
    if (wNotification != OLE_CLOSED)
        Dirty();
    Invalidate();
    // any change will cause a redraw
}
```

在 mfc/ole1 中，容器应用程序派生文档类从`COleClientDoc`。 在 MFC/OLE 2 中，此类已移除，由 `COleDocument` 取代（此新组织使得生成容器/服务器应用重写更简单）。 没有 **#define**映射`COleClientDoc`到`COleDocument`以简化 mfc/ole1 应用程序到 MFC/OLE 2，如 OCLIENT 的移植。 未提供的功能之一`COleDocument`提供`COleClientDoc`是标准命令消息映射条目。 这样做是为了使服务器应用程序（也使用间接地 `COleDocument`）不会负担这些命令处理程序的开销（除非它们是容器/服务器应用程序）。 您还需要将以下条目添加到 CMainDoc 消息映射：

```cpp
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE, OnUpdatePasteMenu)
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE_LINK, OnUpdatePasteLinkMenu)
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_LINKS, OnUpdateEditLinksMenu)
ON_COMMAND(ID_OLE_EDIT_LINKS, COleDocument::OnEditLinks)
ON_UPDATE_COMMAND_UI(ID_OLE_VERB_FIRST, OnUpdateObjectVerbMenu)
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_CONVERT, OnUpdateObjectVerbMenu)
ON_COMMAND(ID_OLE_EDIT_CONVERT, OnEditConvert)
```

所有这些命令的实现都在 `COleDocument` 中，它是您的文档的基类。

此时，OCLIENT 是一个功能性 OLE 容器应用程序。 可以插入任何类型的项（OLE1 或 OLE 2）。 由于支持就地激活的必要代码未实现，项将在单独的窗口中进行编辑，这与 OLE1 非常类似。 下一节将讨论支持就地编辑（有时称为“可视化编辑”）的必要更改。

## <a name="adding-visual-editing"></a>添加“可视化编辑”

OLE 最有趣的功能之一是就地激活（也称为“可视化编辑”）。 此功能可让服务器接管容器的一部分用户界面，以便为用户提供更无缝的编辑界面。 若要向 OCLIENT 实现就地激活，则需要添加一些特殊资源和一些附加代码。 这些资源和代码通常由 AppWizard 提供 — 事实上，此处的很多代码是直接通过“容器”支持从新的 AppWizard 应用程序借用的。

首先，当存在处于就地活动状态的项时，必须添加要使用的菜单资源。 您可以复制 IDR_OCLITYPE 资源并删除除“文件”和“窗口”弹出项之外的所有资源，以便在 Visual C++ 中创建此额外菜单资源。 文件和窗口弹出窗口，以指示组的分隔之间插入两个分隔条 (它应如下所示：文件&#124;&#124;窗口)。 有关这些分隔条的含义以及服务器和容器菜单如何合并的详细信息请参阅[菜单和资源：菜单合并](../mfc/menus-and-resources-menu-merging.md)。

创建这些菜单后，您需要通知框架。 此操作在将文档模板添加 InitInstance 中的文档模板列表前通过调用文档模板的 `CDocTemplate::SetContainerInfo` 完成。 注册文档模板的新代码如下所示：

```cpp
CDocTemplate* pTemplate = new CMultiDocTemplate(
    IDR_OLECLITYPE,
    RUNTIME_CLASS(CMainDoc),
    RUNTIME_CLASS(CMDIChildWnd), // standard MDI child frame
    RUNTIME_CLASS(CMainView));

pTemplate->SetContainerInfo(IDR_OLECLITYPE_INPLACE);

AddDocTemplate(pTemplate);
```

IDR_OLECLITYPE_INPLACE 资源是在 Visual C++ 中创建的特殊就地资源。

若要实现就地激活，`CView` (CMainView) 派生类以及 `COleClientItem` 派生类 (CRectItem) 中有一些项需要更改。 所有这些重写都由 AppWizard 提供，并且大部分实现将直接来自默认 AppWizard 应用程序。

在此移植的第一个步骤中，通过重写 `COleClientItem::CanActivate` 完全禁用了就地激活。 应移除此重写以允许就地激活。 此外，将 NULL 传递给了对 `DoVerb` 的所有调用（下面显示了其中两个），因为只有就地激活才需要提供视图。 若要完全实现就地激活，必须将正确的视图传入 `DoVerb` 调用。 这些调用之一就是`CMainView::OnInsertObject`:

```cpp
pItem->DoVerb(OLEIVERB_SHOW, this);
```

另一个示例是`CMainView::OnLButtonDblClk`:

```cpp
m_pSelection->DoVerb(OLEIVERB_PRIMARY, this);
```

必须重写 `COleClientItem::OnGetItemPosition`。 这将告知服务器，当就地激活项后要相对于容器的窗口放置服务器窗口的位置。 对于 OCLIENT，实现是无关紧要的：

```cpp
void CRectItem::OnGetItemPosition(CRect& rPosition)
{
    rPosition = m_rect;
}
```

大多数服务器还实现了称为“就地调整大小”的功能。 这样，当用户编辑项时，将移动服务器窗口并调整其大小。 容器必须参与此操作，因为移动窗口或调整其大小通常会影响容器文档本身中的位置和大小。 OCLIENT 的实现会将 m_rect 保留的内部矩形与新的位置和大小同步。

```cpp
BOOL CRectItem::OnChangeItemPosition(const CRect& rectPos)
{
    ASSERT_VALID(this);

    if (!COleClientItem::OnChangeItemPosition(rectPos))
        return FALSE;

    Invalidate();
    m_rect = rectPos;
    Invalidate();
    GetDocument()->SetModifiedFlag();

    return TRUE;
}
```

此时，这里有足够的代码来支持就地激活项和处理活动项的大小调整和移动，但没有代码支持用户退出编辑会话。 尽管某些服务器将自行提供此功能通过处理 esc 键，但建议容器提供两种方式停用某项：（1） 通过单击在项的外部和 （2） 通过按 ESC 键。

对于按 Esc 键的情况，请使用 Visual C++ 添加将 VK_ESCAPE 键映射到命令的快捷键，ID_CANCEL_EDIT 将被添加到资源。 此命令的处理程序如下：

```cpp
// The following command handler provides the standard
// keyboard user interface to cancel an in-place
// editing session.void CMainView::OnCancelEdit()
{
    // Close any in-place active item on this view.
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL)
        pActiveItem->Close();
    ASSERT(GetDocument()->GetInPlaceActiveItem(this) == NULL);
}
```

若要处理这种情况，则当用户单击项之外，您的启动中添加以下代码`CMainView::SetSelection`:

```cpp
if (pNewSel != m_pSelection || pNewSel == NULL)
{
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL&& pActiveItem != pNewSel)
        pActiveItem->Close();
}
```

当项处于就地活动状态时，它应该具有焦点。 若要确保如此，您应适当地处理 OnSetFocus，使得您的视图接收焦点时焦点总是转移到活动项：

```cpp
// Special handling of OnSetFocus and OnSize are required
// when an object is being edited in-place.
void CMainView::OnSetFocus(CWnd* pOldWnd)
{
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);

    if (pActiveItem != NULL &&
        pActiveItem->GetItemState() == COleClientItem::activeUIState)
    {
        // need to set focus to this item if it is same view
        CWnd* pWnd = pActiveItem->GetInPlaceWindow();
        if (pWnd != NULL)
        {
            pWnd->SetFocus();   // don't call the base class
            return;
        }
    }

    CView::OnSetFocus(pOldWnd);
}
```

在调整视图的大小时，您需要向活动项通知剪辑矩形已更改。 为此，您应为 `OnSize` 提供一个处理程序：

```cpp
void CMainView::OnSize(UINT nType, int cx, int cy)
{
    CView::OnSize(nType, cx, cy);
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL)
        pActiveItem->SetItemRects();
}
```

## <a name="case-study-hiersvr-from-mfc-20"></a>案例研究：MFC 2.0 中的 HIERSVR

[HIERSVR](../overview/visual-cpp-samples.md)还包含在 MFC 2.0 并实现了使用 mfc/ole1 OLE。 本说明简要介绍此应用程序最初转换为使用 MFC/OLE 2 类所采用的步骤。 初始移植完成后添加了很多功能，用来更好地演示 MFC/OLE 2 类。 此处将不会转换这些功能；有关这些高级功能的详细信息，请参阅示例本身。

> [!NOTE]
> 编译器错误和分步过程是使用 Visual C++ 2.0 创建的。 特定错误消息和位置在 Visual C++ 4.0 中可能已更改，但概念性信息仍然有效。

## <a name="getting-it-up-and-running"></a>开始运行

将 HIERSVR 示例移植到 MFC/OLE 所用的方法首先是生成该示例并修复会产生的明显编译器错误。 如果采用了 MFC 2.0 中的 HIERSVR 示例并在此版本的 MFC 下编译它，您就会发现没有太多要解决的错误（尽管比使用 OCLIENT 示例时多）。 下面按错误通常发生的顺序对其进行说明。

## <a name="compile-and-fix-errors"></a>编译和修复错误

```Output
\hiersvr\hiersvr.cpp(83) : error C2039: 'RunEmbedded' : is not a member of 'COleTemplateServer'
```

这里的第一个错误指出了与服务器的 `InitInstance` 函数有关的较大问题。 OLE 服务器所需的初始化可能是您必须对 MFC/OLE1 应用程序执行以使它运行的最大更改之一。 最有用的做法是查看 AppWizard 为 OLE 服务器创建了什么并根据需要修改代码。 下面是要记住的一些要点：

必须通过调用初始化 OLE 库 `AfxOleInit`

对文档模板对象调用 SetServerInfo 以设置使用 `CDocTemplate` 构造函数无法设置的服务器资源句柄和运行时类信息。

如果命令行上存在 /Embedding，则不显示应用程序的主窗口。

你将需要**GUID**为您的文档。 这是文档类型（128 位）的唯一标识符。 AppWizard 将为你创建一个 GUID，因此，如果你使用此处所述的从 AppWizard 生成的服务器应用程序复制新代码的方法，则只需“窃用”该应用程序中的 GUID。 如果未使用此方法，则可以在 BIN 目录中使用 GUIDGEN.EXE 实用工具。

必须通过调用 `COleTemplateServer` 对象将您的 `COleTemplateServer::ConnectTemplate` 对象“连接”到文档模板。

应在应用程序独立运行时更新系统注册表。 这样，当用户移动应用程序的 .EXE 时，从注册表的新位置运行注册表可将 Windows 系统注册数据库更新为指向新位置。

基于 AppWizard 为 `InitInstance` 创建的项应用所有这些更改后，HIERSVR的 `InitInstance`（以及相关 GUID）应如下所示：

```cpp
// this is the GUID for HIERSVR documents
static const GUID BASED_CODE clsid =
{ 0xA0A16360L, 0xC19B, 0x101A, { 0x8C, 0xE5, 0x00, 0xDD, 0x01, 0x11, 0x3F, 0x12 } };

/////////////////////////////////////////////////////////////////////////////
// COLEServerApp initialization

BOOL COLEServerApp::InitInstance()
{
    // OLE 2 initialization
    if (!AfxOleInit())
    {
        AfxMessageBox("Initialization of the OLE failed!");
        return FALSE;
    }

    // Standard initialization
    LoadStdProfileSettings();   // Load standard INI file options

    // Register document templates
    CDocTemplate* pDocTemplate;
    pDocTemplate = new CMultiDocTemplate(IDR_HIERSVRTYPE,
        RUNTIME_CLASS(CServerDoc),
        RUNTIME_CLASS(CMDIChildWnd),
        RUNTIME_CLASS(CServerView));
    pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB);
    AddDocTemplate(pDocTemplate);

    // create main MDI Frame window
    CMainFrame* pMainFrame = new CMainFrame;
    if (!pMainFrame->LoadFrame(IDR_MAINFRAME))
        return FALSE;
    m_pMainWnd = pMainFrame;

    SetDialogBkColor(); // gray look

    // enable file manager drag/drop and DDE Execute open
    m_pMainWnd->DragAcceptFiles();
    EnableShellOpen();

    m_server.ConnectTemplate(clsid, pDocTemplate, FALSE);
    COleTemplateServer::RegisterAll();

    // try to launch as an OLE server
    if (RunEmbedded())
    {
        // "short-circuit" initialization -- run as server!
        return TRUE;
    }
    m_server.UpdateRegistry();
    RegisterShellFileTypes();

    // not run as OLE server, so show the main window
    if (m_lpCmdLine[0] == '\0')
    {
        // create a new (empty) document
        OnFileNew();
    }
    else
    {
        // open an existing document
        OpenDocumentFile(m_lpCmdLine);
    }

    pMainFrame->ShowWindow(m_nCmdShow);
    pMainFrame->UpdateWindow();

    return TRUE;
}
```

您将注意到，上述代码引用了新的资源 ID IDR_HIERSVRTYPE_SRVR_EMB。 这是要在编辑了嵌入其他容器的文档时使用的菜单资源。 在 MFC/OLE1 中，专用于编辑嵌入项的菜单项是即时修改的。 通过在编辑嵌入项（而不是编辑基于文件的文档）时使用完全不同的菜单结构，为这两个不同的模式提供不同的用户界面就容易得多。 正如您稍后会看到的，就地编辑嵌入对象时将使用完全不同的菜单资源。

若要创建此资源，请将资源脚本加载到 Visual C++ 中并复制现有 IDR_HIERSVRTYPE 菜单资源。 将新资源重命名为 IDR_HIERSVRTYPE_SRVR_EMB（这是 AppWizard 所用的同一命名约定）。 接下来将更改为"文件更新;"的"文件另存"为其指定命令 ID ID_FILE_UPDATE。 此外"文件另存为"更改为"文件副本另存为";为其指定命令 ID ID_FILE_SAVE_COPY_AS。 框架将提供这两个命令的实现。

```Output
\hiersvr\svritem.h(60) : error C2433: 'OLESTATUS' : 'virtual' not permitted on data declarations
\hiersvr\svritem.h(60) : error C2501: 'OLESTATUS' : missing decl-specifiers
\hiersvr\svritem.h(60) : error C2146: syntax error : missing ';' before identifier 'OnSetData'
\hiersvr\svritem.h(60) : error C2061: syntax error : identifier 'OLECLIPFORMAT'
\hiersvr\svritem.h(60) : error C2501: 'OnSetData' : missing decl-specifiers
```

有多个错误的重写`OnSetData`，因为它指**OLESTATUS**类型。 **OLESTATUS**是 OLE1 返回错误的方法。 这已更改为**HRESULT**在 OLE 2 中，尽管 MFC 通常将转换**HRESULT**到`COleException`包含错误。 在这种特定情况下，不必再重写 `OnSetData`，因此最简单的操作是移除它。

```Output
\hiersvr\svritem.cpp(30) : error C2660: 'COleServerItem::COleServerItem' : function does not take 1 parameters
```

`COleServerItem` 构造函数采用了额外的“BOOL”参数。 此标志确定如何对 `COleServerItem` 对象执行内存管理。 通过将它设置为 TRUE，框架将处理这些对象的内存管理 - 在它们不再必需时进行删除。 使用 HIERSVR `CServerItem` (派生自`COleServerItem`) 对象作为其本机数据，因此将此标志设置为 FALSE 的一部分。 这样，HIERSVR 便能确定每个服务器项何时删除。

```Output
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class
```

正如这些错误暗示的，存在尚未在 CServerItem 中重写的“纯虚”函数。 导致此问题的原因最可能是 OnDraw 的参数列表已更改。 若要解决此错误，请更改`CServerItem::OnDraw`（以及 svritem.h 中的声明），如下所示：

```cpp
BOOL CServerItem::OnDraw(CDC* pDC, CSize& rSize)
{
    // request from OLE to draw node
    pDC->SetMapMode(MM_TEXT); // always in pixels
    return DoDraw(pDC, CPoint(0, 0), FALSE);
}
```

新参数为“rSize”。 这使您可以在方便时填写绘图的大小。 此大小必须在**HIMETRIC**。 在这种情况下，填写此值不方便，因此框架调用 `OnGetExtent` 来检索范围。 为了让此操作生效，您必须实现 `OnGetExtent`：

```cpp
BOOL CServerItem::OnGetExtent(DVASPECT dwDrawAspect, CSize& rSize)
{
    if (dwDrawAspect != DVASPECT_CONTENT)
        return COleServerItem::OnGetExtent(dwDrawAspect, rSize);

    rSize = CalcNodeSize();
    return TRUE;
}
```

```Output
\hiersvr\svritem.cpp(104) : error C2065: 'm_rectBounds' : undeclared identifier
\hiersvr\svritem.cpp(104) : error C2228: left of '.SetRect' must have class/struct/union type
\hiersvr\svritem.cpp(106) : error C2664: 'void __pascal __far DPtoLP(struct ::tagPOINT __far *,
    int)__far const ' : cannot convert parameter 1 from 'int __far *' to 'struct ::tagPOINT __far *'
```

在 cserveritem:: Calcnodesize 函数中的项大小转换为**HIMETRIC**并存储在*掉*。 未记录*掉*的成员`COleServerItem`不存在 (已通过部分替换*m_sizeExtent*，但此成员在 OLE 2 中具有比略有不同的使用*掉*未在 OLE1 中)。 而不是设置**HIMETRIC**大小为此成员变量，将返回它。 此返回值在之前实现的 `OnGetExtent` 中使用。

```cpp
CSize CServerItem::CalcNodeSize()
{
    CClientDC dcScreen(NULL);

    m_sizeNode = dcScreen.GetTextExtent(m_strDescription,
        m_strDescription.GetLength());
    m_sizeNode += CSize(CX_INSET * 2, CY_INSET * 2);

    // set suggested HIMETRIC size
    CSize size(m_sizeNode.cx, m_sizeNode.cy);
    dcScreen.SetMapMode(MM_HIMETRIC);
    dcScreen.DPtoLP(&size);
    return size;
}
```

CServerItem 还将重写`COleServerItem::OnGetTextData`。 此函数在 MFC/OLE 中已过时，已由其他机制取代。 MFC 3.0 版的 MFC OLE 示例[HIERSVR](../overview/visual-cpp-samples.md)实现此功能通过重写`COleServerItem::OnRenderFileData`。 此功能对此基本移植并不重要，因此您可以取消 OnGetTextData 重写。

尚未解决的 svritem.cpp 中有很多错误。 它们不是“真正”的错误，而只是由前面的错误导致的错误。

```Output
\hiersvr\svrview.cpp(325) : error C2660: 'CopyToClipboard' : function does not take 2 parameters
```

`COleServerItem::CopyToClipboard` 不再支持`bIncludeNative`标志。 将总是复制本机数据（服务器项的 Serialize 函数写出的数据），因此您应移除第一个参数。 此外，当发生错误而不是返回 FALSE 时，`CopyToClipboard` 将引发异常。 请按如下方式更改 CServerView::OnEditCopy 的代码：

```cpp
void CServerView::OnEditCopy()
{
    if (m_pSelectedNode == NULL)
        AfxThrowNotSupportedException();

    TRY
    {
        m_pSelectedNode->CopyToClipboard(TRUE);
    }
    CATCH_ALL(e)
    {
        AfxMessageBox("Copy to clipboard failed");
    }
    END_CATCH_ALL
}
```

尽管 MFC 2.0 版的 HIERSVR 的编译比同一版本的 OCLIENT 的编译引起的错误更多，但实际上变化较少。

此时，HIERSVR 将进行编译和链接并充当 OLE 服务器，但不使用就地编辑功能（将在下一步实现）。

## <a name="adding-visual-editing"></a>添加“可视化编辑”

若要将“可视化编辑”（或称为就地激活）添加到此服务器应用程序，您只需注意几件事：

- 您需要在项处于就地活动状态时使用的特殊菜单资源。

- 此应用程序包含一个工具栏，因此您需要一个只有常用工具栏的一部分的工具栏以便与服务器（与前面提到的菜单资源匹配）提供的菜单命令匹配。

- 您需要派生自 `COleIPFrameWnd` 的提供就地用户界面的新类（与 CMainFrame 非常相似，它派生自 `CMDIFrameWnd`，提供了 MDI 用户界面）。

- 您需要向框架告知这些特殊资源和类。

菜单资源很容易创建。 运行 Visual C++，将菜单资源 IDR_HIERSVRTYPE 复制到名为 IDR_HIERSVRTYPE_SRVR_IP 的菜单资源。 修改菜单，以便只保留“编辑”和“帮助”菜单弹出项。 在编辑和帮助菜单之间菜单中添加两个分隔符 (它应如下所示：编辑&#124;&#124;帮助)。 有关这些分隔条的含义以及服务器和容器菜单如何合并的详细信息，请参阅[菜单和资源：菜单合并](../mfc/menus-and-resources-menu-merging.md)。

子集工具栏的位图创建起来很轻松：在选中“服务器”选项的情况下从新的 AppWizard 生成的应用程序中复制位图。 此位图随后会导入 Visual C++。 请确保为位图提供 ID IDR_HIERSVRTYPE_SRVR_IP。

派生自 `COleIPFrameWnd` 的类也可以使用服务器支持从 AppWizard 生成的应用程序中复制。 请复制 IPFRAME.CPP 和 IPFRAME.H 这两个文件并将其添加到项目。 确保 `LoadBitmap` 调用引用了上一步中创建的位图 IDR_HIERSVRTYPE_SRVR_IP。

现在所有新资源和类都已创建，请添加必要的代码，以便让框架知道这些（并知道此应用程序现在支持就地编辑）。 此操作通过将更多参数添加到 `SetServerInfo` 函数中的 `InitInstance` 调用完成：

```cpp
pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB,
    IDR_HIERSVRTYPE_SRVR_IP,
    RUNTIME_CLASS(CInPlaceFrame));
```

现在已做好在也支持就地激活的任何容器中就地运行的准备。 但是，代码中还隐藏了一个小 Bug。 HIERSVR 支持用户按鼠标右键时显示的上下文菜单。 此菜单在 HIERSVR 完全打开时有用，但在编辑就地嵌入时不起作用。 原因可能在于 CServerView::OnRButtonDown 中的这一行代码：

```cpp
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,
    point.x,
    point.y,
    AfxGetApp()->m_pMainWnd);
```

请注意，对引用`AfxGetApp()->m_pMainWnd`。 当服务器已就地激活时，它有一个主窗口，并且 m_pMainWnd 已设置，但它通常不可见。 此外，此窗口是指*主要*窗口中的应用程序，MDI 框架窗口出现时服务器完全打开或独立运行。 此窗口不引用活动框架窗口，后者在就地激活后是派生自 `COleIPFrameWnd` 的框架窗口。 为了在就地编辑时获得正确的活动窗口，此版本的 MFC 添加了一个新函数 `AfxGetMainWnd`。 通常情况下，应使用此函数，而不是`AfxGetApp()->m_pMainWnd`。 此代码需要进行以下更改：

```cpp
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,
    point.x,
    point.y,
    AfxGetMainWnd());
```

现在您至少为 OLE 服务器启用了功能性就地激活。 但是，MFC/OLE 2 还有很多 MFC/OLE1 中没有的功能。 若要获得您可能想实现的功能的更多想法，请参阅 HIERSVR 示例。 下面列出了 HIERSVR 实现的一部分功能：

- 缩放，用于与容器真正所见即所得的行为。

- 拖动/放置和自定义剪贴板格式。

- 在选项更改时滚动容器窗口。

MFC 3.0 中的 HIERSVR 示例也为其服务器项使用了稍微不同的设计。 这有助于节约内存和提高链接的灵活性。 2.0 版的 HIERSVR 树中的每个节点*是一个* `COleServerItem`。 `COleServerItem` 承担的开销稍微高于这些节点严格需要的开销，但 `COleServerItem` 对每个活动链接是必需的。 但对于大多数部件，任何给定时间的活动链接都非常少。 为了提高此过程的效率，此版本的 MFC 中的 HIERSVR 将节点从 `COleServerItem` 中分离出来。 它同时具有 CServerNode 和`CServerItem`类。 `CServerItem` (派生自`COleServerItem`) 仅在必要时创建。 一旦容器停止将该特定链接用于该特定节点，与 CServerNode 关联的 CServerItem 对象将会删除。 此设计更有效且更灵活。 其灵活性在处理多项选择链接时能体现出来。 这两个版本的 HIERSVR 都不支持多重选择，但使用 MFC 3.0 版的 HIERSVR 添加（和支持指向此类选择的链接）会更容易，因为 `COleServerItem` 是从本机数据分离出来的。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
