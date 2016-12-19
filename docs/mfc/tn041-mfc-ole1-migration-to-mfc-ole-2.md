---
title: "TN041：MFC/OLE1 迁移到 MFC/OLE 2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "将 OLE1 转换为 OLE2"
  - "将 OLE1 迁移到 OLE2"
  - "迁移 [C++], OLE1 to OLE2"
  - "OLE1 [C++]"
  - "OLE2 [C++]"
  - "将 OLE1 迁移到 OLE2"
  - "TN041"
  - "升级 Visual C++ 应用程序, OLE1 to OLE2"
ms.assetid: 67f55552-4b04-4ddf-af0b-4d9eaf5da957
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN041：MFC/OLE1 迁移到 MFC/OLE 2
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。  因此，某些过程和主题可能已过时或不正确。  要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
## 与相关的常规迁移问题  
 一个 OLE 的设计目标在 MFC 2.5 的 2 类 \(和更高\) 是中保留 1.0 OLE 支持的 MFC 放在适当位置的许多相同结构 2.0。  因此，许多在 MFC 2.0 的 OLE 同一类保留在此 MFC 版本 \(`COleDocument`、`COleServerDoc`、`COleClientItem`，`COleServerItem`\)。  此外，许多这些类的 API 完全相同的。  但是，2 是 OLE 彻底与 OLE 1.0 种不同的外观，从而可以期望某些细节更改。  如果熟悉 MFC 2.0 "OLE1 支持，您在家会感觉与 MFC 2.0 的支持。  
  
 如果拍摄了现有 MFC\/OLE1 应用程序并添加 OLE 功能 2 到它，则应首先读取此注释。  此注释包括可能会遇到的一些常规问题，在将 OLE1 功能。MFC\/OLE 2 然后讨论找到时的问题，当移植 MFC 中包含的两个应用程序时 2.0:MFC OLE、采样和 [OCLIENT](../top/visual-cpp-samples.md) [HIERSVR](../top/visual-cpp-samples.md)。  
  
## MFC 文档\/视图结构很重要。  
 如果应用程序不使用 MFC 文档\/视图体系结构，并且要添加 2 OLE 支持到应用程序，现在是开始移动到文档\/视图。  后，应用程序使用 MFC，内置结构和组件许多 MFC 的 OLE 优点 2 类只实现。  
  
 实现一个服务器或容器不使用 MFC，结构是可能的，但建议不要使用。  
  
## 使用 MFC 实现而不是您自己  
 “MFC 罐装实现”类，如 `CToolBar`、`CStatusBar`，因此，`CScrollView` 具有 2 OLE 支持的特定内置条件代码。  因而，如果在应用程序中使用这些类将使它们受益。工作放置到通过 OLE 识别它们。  同样，可以为“卷这自己的”类此处为这些目的，但是不建议。  如果需要实现类似功能，MFC 源代码是涉及的一个非常好的引用某些 OLE 细则 \(尤其是呈现时就地激活\)。  
  
## 检查 MFC 示例代码  
 很多的 MFC 示例该包含 OLE 功能。  这些应用程序中的每个元素实现从不同的角度的 OLE:  
  
-   [HIERSVR](../top/visual-cpp-samples.md) 表示主要用作服务器应用程序。  在 MFC 2.0 包含为 MFC\/OLE1 应用程序和 MFC\/OLE 移植到 2 然后扩展了这样它实现许多 OLE 功能可以在 OLE 2。  
  
-   [OCLIENT](../top/visual-cpp-samples.md)这是一个独立容器应用程序，演示从许多位置被视为容器的 OLE 功能。  它从 MFC 2.0 还扩展迁移，然后支持许多更高级的 OLE 功能，如自定义格式剪贴板和链接到的项。  
  
-   [DRAWCLI](../top/visual-cpp-samples.md) 此应用程序实现 OLE 支持容器很类似 OCLIENT，除此之外，它这样做。现有的面向对象的绘图程序的框架内。  它显示您可以如何实现 OLE 容器支持和集成到现有的应用程序。  
  
-   [SUPERPAD](../top/visual-cpp-samples.md) 此应用程序，以及是一种好的独立应用程序，也是 OLE 服务器。  它实现的服务器数量最低支持平台派。  特殊的优点是它如何使用 OLE 剪贴板服务将数据复制到剪贴板，但使用功能内置 Windows“编辑”控件粘贴剪贴板实现功能。  这显示传统 Windows API 使用情况以及集成有趣的混合使用新的 OLE API。  
  
 有关示例应用程序的更多信息，请参见 MFC 示例的“帮助”。  
  
## 情况分析：从 MFC 2.0 的 OCLIENT  
 如上所述，[OCLIENT](../top/visual-cpp-samples.md) 在 MFC 2.0 包含已实现了与 MFC\/OLE1 的 OLE。  此应用程序初始转换使用 MFC\/OLE 2 类的步骤介绍。  在最初的端口完成更好 MFC\/OLE 类后，许多功能的添加。  这些功能将中；此处请参见示例有关某些高级功能的更多信息。  
  
> [!NOTE]
>  编译器错误和分步过程创建使用 Visual C\+\+ 2.0。  特定错误消息和位置更改可能与 Visual C\+\+ 4.0，但概念性信息保持有效。  
  
## 获取运行它的  
 接受的方法。MFC\/OLE 移植 OCLIENT 示例将首先生成并修复会带来明显的编译器错误。  如果拍摄从 MFC 2.0 的 OCLIENT 示例并将其编译的 MFC 下此版本的，您就不解决尽可能多的错误。  按下述发生的错误。  
  
## 编译并修复错误  
  
```  
\oclient\mainview.cpp(104) : error C2660: 'Draw' : function does not take 4 parameters  
```  
  
 第一错误相关 `COleClientItem::Draw`。  在 MFC\/OLE1 它比 MFC\/OLE 版本作为采取了多个参数。  额外的参数通常不必要和通常 NULL \(在此示例中为\)。  MFC 此版本可以自动确定 lpWBounds 的值，在绘制时的 CDC 是元文件 DC。  此外，因为框架，将同时一个“特性”pDC DC 传递参数，pFormatDC 不再是必需的。  若要解决此问题，您移除两个额外的参数调用绘制为空。  
  
```  
\oclient\mainview.cpp(273) : error C2065: 'OLE_MAXNAMESIZE' : undeclared identifier  
\oclient\mainview.cpp(273) : error C2057: expected constant expression  
\oclient\mainview.cpp(280) : error C2664: 'CreateLinkFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '  
\oclient\mainview.cpp(286) : error C2664: 'CreateFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '  
\oclient\mainview.cpp(288) : error C2664: 'CreateStaticFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '  
```  
  
 在结果中的错误从所有事实 **COleClientItem::CreateXXXX** 在 MFC\/OLE1 函数要求唯一名称传递表示项。  这是基础 OLE API 的要求。  这不是必需的。MFC\/OLE 2 OLE，因为 2 不使用 DDE 作为基础通信机制 \(名称在 DDE 对话\)。  若要解决此问题，您可以移去 **CreateNewName** 函数以及该对象的所有引用。  发现很容易了每个 MFC\/OLE 函数在此生成应通过在光标位于调用并按 F1。  
  
 上部不同的其他区域是 OLE 2 剪贴板处理。  使用 OLE1，您使用了 Windows API 与剪贴板交互的剪贴板。  OLE 2 这样做与不同的机制。  MFC\/OLE1 API，假设在剪贴板复制到剪贴板的 `COleClientItem` 对象之前处于打开状态。  它不再是必需的，并且会导致所有 MFC\/OLE 剪贴板操作失败。  当您编辑代码时移除对 **CreateNewName**时的依赖，还应移除打开并关闭 Windows 剪贴板的代码。  
  
```  
\oclient\mainview.cpp(332) : error C2065: 'AfxOleInsertDialog' : undeclared identifier  
\oclient\mainview.cpp(332) : error C2064: term does not evaluate to a function  
\oclient\mainview.cpp(344) : error C2057: expected constant expression  
\oclient\mainview.cpp(347) : error C2039: 'CreateNewObject' : is not a member of 'CRectItem'  
```  
  
 从 **CMainView::OnInsertObject** 处理程序调用这些错误的结果。  处理“插入新的命令对象”是内容大小更改位的其他区域。  在这种情况下，将使用 AppWizard 提供的原始 OLE 容器实现对于新的应用程序是最容易的。  实际上，可以在此处将迁移到其他应用程序的技术。  在 MFC\/OLE1，通过调用 **AfxOleInsertDialog** 函数显示了“插入对象”对话框。  在此版本。**COleInsertObject** 构造对话框对象并调用 `DoModal`。  另外，新的 OLE 项创建了 **CLSID** 而不是 classname 字符串。  最后结果应类似于：  
  
```  
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
    if (dlg.GetSelectionType() ==   
            COleInsertDialog::createNewItem)  
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
>  新插入的对象可能不同的应用程序\):  
  
 对包含 \<afxodlgs.h 也是必需的，包含\>**COleInsertObject** 对话框类的声明以及 MFC 提供的其他标准对话框。  
  
```  
\oclient\mainview.cpp(367) : error C2065: 'OLEVERB_PRIMARY' : undeclared identifier  
\oclient\mainview.cpp(367) : error C2660: 'DoVerb' : function does not take 1 parameters  
```  
  
 这些错误由这导致某种 OLE1 常数在 OLE 2 更改，因此，即使它们在概念中相同。  在这种情况下 **OLEVERB\_PRIMARY** 更改为 `OLEIVERB_PRIMARY`。  在 OLE1 和 OLE，当用户双击项上时，2，谓词由容器通常主要执行。  
  
 此外，`DoVerb` 现在采用额外的参数 \- 对视图 \(`CView`的指针。\*\)。  此参数仅用于实现“编辑的可视化对象”就地激活 \(或\)。  现在将为 Null 的，该参数，因为目前不实现此功能。  
  
 若要确保框架，永远不会尝试为就地激活，则应该重写 `COleClientItem::CanActivate` 如下所示：  
  
```  
BOOL CRectItem::CanActivate()  
{  
    return FALSE;  
}  
  
\oclient\rectitem.cpp(53) : error C2065: 'GetBounds' : undeclared identifier  
\oclient\rectitem.cpp(53) : error C2064: term does not evaluate to a function  
\oclient\rectitem.cpp(84) : error C2065: 'SetBounds' : undeclared identifier  
\oclient\rectitem.cpp(84) : error C2064: term does not evaluate to a function  
```  
  
 在 MFC\/OLE1 和 **SetBounds**，**COleClientItem::GetBounds** 用于查询和操作项的大小 \( **left** 和 **top** 成员始终为零\)。  在 MFC\/OLE 2 由 `COleClientItem::GetExtent` 和 `SetExtent`这更直接支持，与 **SIZE** 或 `CSize`。  
  
 新的 SetItemRectToServer 的代码和 UpdateItemRectFromServer 调用如下所示：  
  
```  
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
      SetExtent(size);  // may do a wait  
   }  
   CATCH(CException, e)  
   {  
      return FALSE;  // links will not allow SetBounds  
   }  
   END_CATCH  
   return TRUE;  
}  
  
\oclient\frame.cpp(50) : error C2039: 'InWaitForRelease' : is not a member of 'COleClientItem'  
\oclient\frame.cpp(50) : error C2065: 'InWaitForRelease' : undeclared identifier  
\oclient\frame.cpp(50) : error C2064: term does not evaluate to a function  
```  
  
 在 MFC\/OLE1 从容器的同步 API 调用，因为 OLE1 大多数情况下，本质上异步的服务器到 *模拟了*。  检查某个未处理异步调用的运行需要的在处理来自用户的命令。  MFC\/OLE1 为为此提供的 **COleClientItem::InWaitForRelease** 函数。  在 MFC\/OLE 2 这不是必要的，因此，您可以同时将 OnCommand 重写在 CMainFrame 整个。  
  
 OCLIENT 此时将编译并链接。  
  
## 其他必要的更改  
 但是将不具有进行阻止运行 OCLIENT 的，少的操作。  现在解决这些问题而不是之后最好。  
  
 首先，初始化 OLE 库是必需的。  这是以从 `InitInstance`中调用 **AfxOleInit** 完成：  
  
```  
if (!AfxOleInit())  
{  
  AfxMessageBox("Failed to initialize OLE libraries");  
  return FALSE;  
}  
```  
  
 也是一个好办法检查参数列表更改的虚函数。  一类函数是 `COleClientItem::OnChange`，将在每个 MFC\/OLE 容器应用程序。  只看联机帮助，您将看到一额外的“一”dwParam 添加了。  新的 CRectItem::OnChange 如下所示：  
  
```  
void   
CRectItem::OnChange(OLE_NOTIFICATION wNotification, DWORD dwParam)  
{  
  if (m_bTrackServerSize &&  
        !UpdateItemRectFromServer())  
  {  
    // Blank object  
    if (wNotification == OLE_CLOSED)  
    {  
      // no data received for the object - destroy it  
      ASSERT(!IsVisible());  
      GetDocument()->DeleteItem(this);  
      return;   // no update (item is gone now)  
    }  
  }  
  if (wNotification != OLE_CLOSED)  
      Dirty();  
  Invalidate();  // any change will cause a redraw  
}  
```  
  
 在 MFC\/OLE1，从 **COleClientDoc**派生类的文档容器应用程序。  在 MFC\/OLE 2 `COleDocument` 取消了此类并替换了 \(此新便于组织生成容器\/服务器应用\)。  **COleClientDoc** 具有 `#define` 映射到 `COleDocument` MFC\/OLE1 应用程序的 MFC\/OLE 简化移植到 2，如 OCLIENT。  **COleClientDoc** 提供 `COleDocument` 未提供的一个功能是标准命令消息映射项。  这样做，这样服务器应用程序，使用 `COleDocument` \(间接\)，不具有与其系统开销这些命令处理程序，除非它们是容器\/服务器应用程序。  还需要将以下代码添加到行集合中的 COM 映射：  
  
```  
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE, OnUpdatePasteMenu)  
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE_LINK, OnUpdatePasteLinkMenu)  
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_LINKS, OnUpdateEditLinksMenu)  
ON_COMMAND(ID_OLE_EDIT_LINKS, COleDocument::OnEditLinks)  
ON_UPDATE_COMMAND_UI(ID_OLE_VERB_FIRST, OnUpdateObjectVerbMenu)  
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_CONVERT, OnUpdateObjectVerbMenu)  
ON_COMMAND(ID_OLE_EDIT_CONVERT, OnEditConvert)  
```  
  
 所有的实现这些命令在 `COleDocument`文档，是的基类。  
  
 此时，OCLIENT 是一个功能 OLE 容器应用程序。  可以插入任何类型的项 \(OLE1 或 OLE 2\)。  由于支持就地激活的必需代码不实现，项在单独窗口编辑非常类似。OLE1 的。  下一节讨论的必要更改实现就地编辑 \(有时称为“编辑的可视化对象”\)。  
  
## 添加“可视化编辑”  
 一个 OLE 有趣的功能是就地激活编辑 \(或的“可视化”\)。  此功能允许服务器接收应用容器的用户界面的部分提供了一个更全面的编辑界面。  若要实现就地激活。OCLIENT，某些特定资源需要添加，以及某些附加代码。  AppWizard 通常提供这些资源和代码 \- 事实上，许多此处的代码直接利用“容器”支持的新 AppWizard 应用程序中借用了。  
  
 首先，添加将使用菜单资源的需要，在处于就地活动的项。  可以通过复制 IDR\_OCLITYPE 资源并删除所有文件，但和弹出窗口创建在 Visual C\+\+ 中进行这一额外的菜单资源。  分隔两条之间插入文件和弹出窗口之间指明组 \(其分开应如下：文件&#124;&#124;窗口\)。  有关内容的更多信息这些分隔符表示和服务器和容器如何合并菜单看到“菜单和资源：包含”*OLE 2 类的*菜单。  
  
 一旦排列这些菜单创建，需要通知框架它们。  这由调用文档模板的 `CDocTemplate::SetContainerInfo` 完成，然后才能添加到中 InitInstance 之前的文档模板的列表。  注册文档模板的新代码如下所示：  
  
```  
CDocTemplate* pTemplate = new CMultiDocTemplate(  
    IDR_OLECLITYPE,  
    RUNTIME_CLASS(CMainDoc),  
    RUNTIME_CLASS(CMDIChildWnd),    // standard MDI child frame  
    RUNTIME_CLASS(CMainView));  
pTemplate->SetContainerInfo(IDR_OLECLITYPE_INPLACE);  
AddDocTemplate(pTemplate);  
```  
  
 IDR\_OLECLITYPE\_INPLACE 资源是 Visual C\+\+ 创建的就地特定资源。  
  
 若要启用就地激活，`CView` 中有一些事项 \(CMainView\) 派生类以及 `COleClientItem` 派生类 \(CRectItem\) 需要更改。  AppWizard 提供所有这些重写，并且大部分实现将直接来自 AppWizard 默认应用程序。  
  
 此端口第一步，就地激活通过重写 `COleClientItem::CanActivate`完全禁用。  应移除此重写允许就地激活。  此外，传递给 null 对 `DoVerb` 的所有调用 \(有两个元素\)，因为提供视图对于就地激活才是必需的。  完全实现就地激活，将 `DoVerb` 调用的正确的视图是必需的。  这些调用之一在 **CMainView::OnInsertObject**:  
  
```  
pItem->DoVerb(OLEIVERB_SHOW, this);  
```  
  
 另中 **CMainView::OnLButtonDblClk**:  
  
```  
m_pSelection->DoVerb(OLEIVERB_PRIMARY, this);  
```  
  
 重写 `COleClientItem::OnGetItemPosition`是必需的。  就地，当激活时的项，就知道在何处放置服务器窗口相对于容器的窗口。  在 OCLIENT，实现是无足轻重的：  
  
```  
void CRectItem::OnGetItemPosition(CRect& rPosition)  
{  
    rPosition = m_rect;  
}  
```  
  
 多数服务器还实现哪些调用“就地调整大小”。当用户编辑项时，这样服务器窗口大小和移动。  容器必须参与此操作，因为移动或调整窗口通常影响位置和大小容器文档中。  OCLIENT 的实现与同步新的位置和大小的 m\_rect 维护的矩形内部。  
  
```  
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
  
 此时，可项足够的代码处于就地激活和处理大小和移动项，当处于活动状态时，但代码不允许用户退出编辑会话。  虽然某些服务器通过处理转义键提供此功能建议，容器提供两种活动项：\(1\) 通过单击在项以及 \(2\) 按 Escape 键。  
  
 对于转义密钥，请映射添加 VK\_ESCAPE 键的命令使用 Visual C\+\+ 的快捷键，ID\_CANCEL\_EDIT 添加到 Resources。  此命令的处理程序如下：  
  
```  
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
  
 若要在处理用户项之外单击的情况，添加以下代码。**CMainView::SetSelection**开始：  
  
```  
if (pNewSel != m_pSelection || pNewSel == NULL)  
{  
    COleClientItem* pActiveItem =   
        GetDocument()->GetInPlaceActiveItem(this);  
    if (pActiveItem != NULL && pActiveItem != pNewSel)  
        pActiveItem->Close();  
}  
  
```  
  
 当项处于就地活动时，它应具有焦点。  为确定这一点是在处理 OnSetFocus 的情况，以便始终焦点转移到活动项，则视图获得焦点时：  
  
```  
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
            pWnd->SetFocus();  // don't call the base class  
            return;  
        }  
    }  
  
    CView::OnSetFocus(pOldWnd);  
}  
```  
  
 在视图调整时，需要通知活动项剪切矩形更改。  为此为 `OnSize`提供一处理程序：  
  
```  
void CMainView::OnSize(UINT nType, int cx, int cy)  
{  
    CView::OnSize(nType, cx, cy);  
    COleClientItem* pActiveItem =   
        GetDocument()->GetInPlaceActiveItem(this);  
    if (pActiveItem != NULL)  
        pActiveItem->SetItemRects();  
}  
```  
  
## 情况分析：从 MFC 2.0 的文本  
 [HIERSVR](../top/visual-cpp-samples.md) 在 MFC 2.0 还包含已实现了与 MFC\/OLE1 的 OLE。  此注释简要描述此应用程序初始转换使用 MFC\/OLE 2 类的步骤。  在最初的端口完成更好 MFC\/OLE2 类后，许多功能的添加。  这些功能将中；此处请参见示例有关某些高级功能的更多信息。  
  
> [!NOTE]
>  编译器错误和分步过程创建使用 Visual C\+\+ 2.0。  特定错误消息和位置更改可能与 Visual C\+\+ 4.0，但概念性信息保持有效。  
  
## 获取运行它的  
 接受的方法。MFC\/OLE 移植 HIERSVR 示例将首先生成并修复会带来明显的编译器错误。  如果拍摄从 MFC 2.0 的 HIERSVR 示例并将其编译 MFC，此版本下您查看未解析的许多错误 \(虽然有多于与 OCLIENT 示例\)。  按下述经常发生的错误。  
  
## 编译并修复错误  
  
```  
\hiersvr\hiersvr.cpp(83) : error C2039: 'RunEmbedded' : is not a member of 'COleTemplateServer'  
```  
  
 此第一错误指出使用 `InitInstance` 函数的更大的问题服务器。  对于 OLE 服务器所需的初始化可能是您对 MFC\/OLE1 应用程序获取运行它的一个最大的更改。  所要做的最好的事情是查看哪些 AppWizard 为 OLE 服务器创建并根据需要修改代码。  这是面向要记住的那些点：  
  
 通过调用 **AfxOleInit**初始化 OLE 库是必需的。  
  
 在文档模板对象的调用 SetServerInfo 到您不能设置与 `CDocTemplate` 构造函数的集合服务器资源句柄和运行时类信息。  
  
 如果 \/Embedding 位于命令行，请不显示应用程序的主窗口。  
  
 需要文档的 **GUID**。  这是文件类型的唯一标识符\(128 位\)。  AppWizard 将为您创建一个，因此，如果您使用方法此处描述将新的 AppWizard 生成的服务器应用的新代码，可以“仅指偷窃”该应用程序的 GUID。  否则，可以在 Bin 目录 GUIDGEN.EXE 可以使用实用工具。  
  
 是必需通过调用 `COleTemplateServer::ConnectTemplate`”连接”到文档模板的 `COleTemplateServer` 对象。  
  
 在应用程序运行的独立时，更新系统注册表。  这样，当用户移动应用程序的 .exe，请从其新位置更新 Windows 系统注册数据库为指向新位置。  
  
 在应用之后这些基于的任何更改有关 AppWizard 为 \( `InitInstance`，`InitInstance` 以及相关 GUID\) 导致 HIERSVR 中应如下所示：  
  
```  
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
    LoadStdProfileSettings(); // Load standard INI file options   
  
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
  
    SetDialogBkColor();   // gray look  
  
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
  
 您将注意上面代码引用新的资源 ID，IDR\_HIERSVRTYPE\_SRVR\_EMB。  这是将使用菜单资源，在其他容器时嵌入文档的编辑。  在特定于 MFC\/OLE1 编辑嵌入式项即时修改定义菜单项。  使用完全不同的菜单结构，当编辑嵌入式项而不是编辑基于文件的文档使更易于为这两个不同模式提供的用户界面。  正如你稍后会看到的，使用完全不同菜单资源，以及在编辑时的就地嵌入对象。  
  
 若要创建该资源，请加载资源脚本到 Visual C\+\+ 将现有 IDR\_HIERSVRTYPE 菜单资源。  重命名新资源重命名为 IDR\_HIERSVRTYPE\_SRVR\_EMB \(这是 AppWizard\) 使用相同的命名约定。  接下来将“保存文件”改成“文件更新”;命令 ID 的 **ID\_FILE\_UPDATE**。  同时将“文件另存为”文件副本保存”;为命令 ID 的 **ID\_FILE\_SAVE\_COPY\_AS**。  框架提供这两个命令的实现。  
  
```  
\hiersvr\svritem.h(60) : error C2433: 'OLESTATUS' : 'virtual' not permitted on data declarations  
\hiersvr\svritem.h(60) : error C2501: 'OLESTATUS' : missing decl-specifiers  
\hiersvr\svritem.h(60) : error C2146: syntax error : missing ';' before identifier 'OnSetData'  
\hiersvr\svritem.h(60) : error C2061: syntax error : identifier 'OLECLIPFORMAT'  
\hiersvr\svritem.h(60) : error C2501: 'OnSetData' : missing decl-specifiers  
```  
  
 因为它是引用 **OLESTATUS** 类型，存在很多错误的根源于 `OnSetData`重写。  **OLESTATUS** 是一种 OLE1 返回的错误。  此更改在 OLE 2 的 `HRESULT`，尽管通常，MFC `HRESULT` 转换为包含错误的 `COleException`。  在这种特定情况下，`OnSetData` 方法不再是必需的，因此，为了执行的最简单的方法是将其移除。  
  
```  
\hiersvr\svritem.cpp(30) : error C2660: 'COleServerItem::COleServerItem' : function does not take 1 parameters  
```  
  
 `COleServerItem` 构造函数采用额外的 'BOOL' 参数。  此标志确定内存管理如何对 `COleServerItem` 对象完成。  通过将其设置为 true，则框架处理这些对象内存管理\) 删除它们，在它们不再是必需的。  HIERSVR 使用 **CServerItem** \(派生自 `COleServerItem`\) 作为其本机数据的一部分对象，这样，将此标志设置为错误。  这样一来 HIERSVR 确定每个服务器项目时删除。  
  
```  
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class  
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class  
```  
  
 由于这些错误意味着，具有未在 CServerItem 重写的数组“纯虚函数”。  这可能由一事实使的 OnDraw 的参数列表更改。  修复此错误，请将 **CServerItem::OnDraw** 更改如下 \(以及 svritem.h 的声明\):  
  
```  
BOOL CServerItem::OnDraw(CDC* pDC, CSize& rSize)  
{  
    // request from OLE to draw node  
    pDC->SetMapMode(MM_TEXT); // always in pixels  
    return DoDraw(pDC, CPoint(0,0), FALSE);  
}  
```  
  
 新参数为 'rSize' 。  如果可以的话允许您绘制的范围填充。  此范围必须在 **HIMETRIC**。  在这种情况下，填写此值不方便，以便框架调用 `OnGetExtent` 检索范围。  对于工作的上下文，则必须实现 `OnGetExtent`:  
  
```  
BOOL CServerItem::OnGetExtent(DVASPECT dwDrawAspect, CSize& rSize)  
{  
    if (dwDrawAspect != DVASPECT_CONTENT)  
        return COleServerItem::OnGetExtent(dwDrawAspect, rSize);  
  
    rSize = CalcNodeSize();  
    return TRUE;  
}  
  
\hiersvr\svritem.cpp(104) : error C2065: 'm_rectBounds' : undeclared identifier  
\hiersvr\svritem.cpp(104) : error C2228: left of '.SetRect' must have class/struct/union type  
\hiersvr\svritem.cpp(106) : error C2664: 'void __pascal __far DPtoLP(struct ::tagPOINT __far *,int )__far const ' : cannot convert parameter 1 from 'int __far *' to 'struct ::tagPOINT __far *'  
```  
  
 在函数 CServerItem::CalcNodeSize 项的大小。**m\_rectBounds**转换为 **HIMETRIC** 并存储。  `COleServerItem` 的使用未证明的 '**m\_rectBounds**' 成员不存在 \(它被 `m_sizeExtent`部分替换了，但 2 OLE 在此成员比 **m\_rectBounds** 在 OLE1 执行\) 有一些不同的用法。  除了 **HIMETRIC** 设置范围为该成员变量中，则返回它。  此返回值在 `OnGetExtent`之前实现。  
  
```  
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
  
 CServerItem 还重写 **COleServerItem::OnGetTextData**。  此函数已过时，MFC\/OLE由不同的机制来替换。  MFC OLE 示例 [HIERSVR](../top/visual-cpp-samples.md) 的 MFC 3.0 版通过重写 `COleServerItem::OnRenderFileData`实现此功能。  此功能为此基本的端口并不重要，因此，您可以取消 OnGetTextData 重写。  
  
 在未解决的 svritem.cpp 的许多错误。  由前面的错误引起的错误不是真的错误。  
  
```  
\hiersvr\svrview.cpp(325) : error C2660: 'CopyToClipboard' : function does not take 2 parameters  
```  
  
 `COleServerItem::CopyToClipboard` 不再支持“bIncludeNative”标志。  本机数据 \(服务器项目使用的数据序列化函数\) 总是复制，因此，您移除第一个参数。  此外，`CopyToClipboard` 将引发异常，在出现错误而不是返回错误。  更改 CServerView::OnEditCopy 的代码如下：  
  
```  
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
  
 尽管比为 OCLIENT 具有一个或多个错误引起 HIERSVR MFC 2.0 版编译的同一版本，实际上有少量更改。  
  
 HIERSVR 此时将编译并链接和功能为 OLE 服务器，但无需编辑功能，接下来将要实现。  
  
## 添加“可视化编辑”  
 若要添加“编辑的可视化”\(或就地激活\) 到此服务器应用，必须处理的某些事件：  
  
-   当项目处于就地活动时，需要使用特殊菜单资源。  
  
-   此应用程序包含一个工具栏，因此，需要使用正则工具栏的一个子集的工具栏与菜单命令可从服务器 \(符合上述菜单资源\)。  
  
-   就地需要提供用户界面从 `COleIPFrameWnd` 派生的新类 \(就像 CMainFrame，从 `CMDIFrameWnd`派生，MDI 提供用户界面\)。  
  
-   需要通知这些特定资源和类的框架。  
  
 菜单资源是轻松地创建。  运行 Visual C\+\+，复制菜单资源 IDR\_HIERSVRTYPE 给调用 IDR\_HIERSVRTYPE\_SRVR\_IP 的菜单资源。  修改菜单，以便只编辑和帮助菜单弹出菜单保留。  添加两分隔符到堆栈 \(它帮助编辑和菜单之间的菜单应如下：编辑&#124;&#124;帮助\)。  有关内容的更多信息这些分隔符表示和服务器和容器如何合并菜单看到“菜单和资源"：包含*OLE 2 类的*菜单。  
  
 子集的工具栏位图可以轻松地通过副本创建一个与检查的“服务器”选项的新 AppWizard 生成的应用程序。  此位图会导入到 Visual C\+\+。  确保为 IDR\_HIERSVRTYPE\_SRVR\_IP 位图 ID。  
  
 从 `COleIPFrameWnd` 派生的类可以使用支持从服务器中 AppWizard 生成的应用程序副本。  复制两个文件 IPFRAME.CPP和 IPFRAME.H 并将它们添加到项目。  确保 `LoadBitmap` 调用引用 IDR\_HIERSVRTYPE\_SRVR\_IP，在上一步创建的位图。  
  
 既然所有新资源和类创建的，请将添加必要的代码，以便框架知道这些 \(并且知道此应用程序现在支持就地编辑\)。  这是由添加一些参数完成到 `InitInstance` 函数中 `SetServerInfo` 调用：  
  
```  
pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB,  
    IDR_HIERSVRTYPE_SRVR_IP, RUNTIME_CLASS(CInPlaceFrame));  
```  
  
 它现在准备好进行同样在支持就地激活的所有容器。  但是，仍有潜在代码中的一小 Bug。  HIERSVR 支持上下文菜单上，显示用户按下鼠标右键。  此菜单工作，在 HIERSVR 完全打开，但是，在嵌入就地编辑不起作用。  原因可以固定到下此行代码在 CServerView::OnRButtonDown:  
  
```  
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,  
    point.x, point.y, AfxGetApp()->m_pMainWnd);  
```  
  
 请注意对 **AfxGetApp\(\)\-m\_pMainWnd\>**的引用。  如果服务器处于就地激活时，其主窗口，并 m\_pMainWnd 设置，但是，它通常不可见。  此外，此窗口是指应用程序的 *主窗口*，显示的 MDI 框架窗口的服务器是完全独立打开或中运行。  不引用激活就是从 `COleIPFrameWnd`派生出来的框架窗口的活动框架窗口\)。  获取右侧的活动窗口，即使就地编辑，MFC 此版本添加一个新函数，`AfxGetMainWnd`。  通常，应使用此函数而不是 **AfxGetApp\(\)\-m\_pMainWnd\>**。  此代码需要更改如下：  
  
```  
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,  
    point.x, point.y, AfxGetMainWnd());  
```  
  
 现在您有用于就地激活功能最低限度上启用的 OLE 服务器。  但是，仍存在许多功能适用于不在 MFC\/OLE1 的 MFC\/OLE 2。  对于您可能想实现的功能的详细概念参见 HIERSVR 示例。  某些功能 HIERSVR 实现如下所示：  
  
-   缩放为 true WYSISYG 行为相对于容器。  
  
-   拖放和自定义格式剪贴板。  
  
-   滚动容器窗口作为更改。  
  
 在 MFC 3.0 的 HIERSVR 示例为服务器项目还使用一个有些不同的设计。  这有助于保留内存并使链接更加灵活。  HIERSVR 2.0 版在树 *属于* `COleServerItem`中的每个节点。  `COleServerItem` 大于为这些节点具有更多的开销中的每绝对必需的，但是，`COleServerItem` 对每个父子链接是必需的。  但是，大多部件在指定后有极少数活动链接。  为了使此过程更加高效，在此 MFC 版本的 HIERSVR 将从 `COleServerItem`节点。  它具有 CServerNode 和一个 **CServerItem** 类。  **CServerItem** \(从 `COleServerItem`派生\) 根据只需创建。  一旦使用此特定链接的容器 \(或容器\) 终止为特定的节点，CServerItem 对象与 CServerNode 删除。  此设计是更高效且更灵活。  其灵活性中，当处理多选择链接时。  二者没有 HIERSVR 支持多重选择，这两类版本，而不是更容易添加 \(和到这样选择的连接\) 与支持 HIERSVR MFC 3.0 版，因为 `COleServerItem` 是从本机数据分隔。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)