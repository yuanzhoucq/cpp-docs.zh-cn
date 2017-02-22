---
title: "COleClientItem Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleClientItem"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "client items and OLE containers"
  - "COleClientItem class"
  - "container interface class"
  - "OLE client item class"
  - "OLE containers, client items"
  - "OLE containers, 接口类"
ms.assetid: 7f571b7c-2758-4839-847a-0cf1ef643128
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# COleClientItem Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

定义容器接口OLE项。  
  
## 语法  
  
```  
class COleClientItem : public CDocItem  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleClientItem::COleClientItem](../Topic/COleClientItem::COleClientItem.md)|构造 `COleClientItem` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleClientItem::Activate](../Topic/COleClientItem::Activate.md)|打开操作的OLE项并执行指定的谓词。|  
|[COleClientItem::ActivateAs](../Topic/COleClientItem::ActivateAs.md)|激活该项目为其他类型。|  
|[COleClientItem::AttachDataObject](../Topic/COleClientItem::AttachDataObject.md)|访问OLE对象的数据。|  
|[COleClientItem::CanCreateFromData](../Topic/COleClientItem::CanCreateFromData.md)|指示容器应用程序是否可以创建嵌入对象。|  
|[COleClientItem::CanCreateLinkFromData](../Topic/COleClientItem::CanCreateLinkFromData.md)|指示容器应用程序是否可以创建链接对象。|  
|[COleClientItem::CanPaste](../Topic/COleClientItem::CanPaste.md)|指示剪贴板是否包含可嵌入或静态OLE项。|  
|[COleClientItem::CanPasteLink](../Topic/COleClientItem::CanPasteLink.md)|指示剪贴板是否包含一个可连接的OLE项。|  
|[COleClientItem::Close](../Topic/COleClientItem::Close.md)|关闭一个到服务器的链接，但不销毁OLE项。|  
|[COleClientItem::ConvertTo](../Topic/COleClientItem::ConvertTo.md)|转换项目转换为另一种类型。|  
|[COleClientItem::CopyToClipboard](../Topic/COleClientItem::CopyToClipboard.md)|OLE项复制到剪贴板。|  
|[COleClientItem::CreateCloneFrom](../Topic/COleClientItem::CreateCloneFrom.md)|创建现有项目的副本。|  
|[COleClientItem::CreateFromClipboard](../Topic/COleClientItem::CreateFromClipboard.md)|创建从剪贴板中嵌入项。|  
|[COleClientItem::CreateFromData](../Topic/COleClientItem::CreateFromData.md)|创建从数据对象的一个嵌入项。|  
|[COleClientItem::CreateFromFile](../Topic/COleClientItem::CreateFromFile.md)|创建嵌入项从文件。|  
|[COleClientItem::CreateLinkFromClipboard](../Topic/COleClientItem::CreateLinkFromClipboard.md)|创建从剪贴板中链接的项目。|  
|[COleClientItem::CreateLinkFromData](../Topic/COleClientItem::CreateLinkFromData.md)|创建从数据对象中链接的项目。|  
|[COleClientItem::CreateLinkFromFile](../Topic/COleClientItem::CreateLinkFromFile.md)|创建链接的项将从文件。|  
|[COleClientItem::CreateNewItem](../Topic/COleClientItem::CreateNewItem.md)|通过生成服务器应用程序创建一个新的嵌入项。|  
|[COleClientItem::CreateStaticFromClipboard](../Topic/COleClientItem::CreateStaticFromClipboard.md)|创建从剪贴板的静态项。|  
|[COleClientItem::CreateStaticFromData](../Topic/COleClientItem::CreateStaticFromData.md)|创建从数据对象的静态项。|  
|[COleClientItem::Deactivate](../Topic/COleClientItem::Deactivate.md)|停用该项目。|  
|[COleClientItem::DeactivateUI](../Topic/COleClientItem::DeactivateUI.md)|还原容器应用程序的用户界面到其原始状态。|  
|[COleClientItem::Delete](../Topic/COleClientItem::Delete.md)|如果它是链接的项目中，删除或关闭OLE项。|  
|[COleClientItem::DoDragDrop](../Topic/COleClientItem::DoDragDrop.md)|执行拖放操作。|  
|[COleClientItem::DoVerb](../Topic/COleClientItem::DoVerb.md)|执行指定的谓词。|  
|[COleClientItem::Draw](../Topic/COleClientItem::Draw.md)|绘制OLE项。|  
|[COleClientItem::GetActiveView](../Topic/COleClientItem::GetActiveView.md)|获取项目就地激活的视图。|  
|[COleClientItem::GetCachedExtent](../Topic/COleClientItem::GetCachedExtent.md)|返回OLE项的矩形区域。|  
|[COleClientItem::GetClassID](../Topic/COleClientItem::GetClassID.md)|获取当前项目的选件类ID.|  
|[COleClientItem::GetClipboardData](../Topic/COleClientItem::GetClipboardData.md)|获取在剪贴板将放在通过调用 `CopyToClipboard` 成员函数的数据。|  
|[COleClientItem::GetDocument](../Topic/COleClientItem::GetDocument.md)|返回包含当前项目的 `COleDocument` 对象。|  
|[COleClientItem::GetDrawAspect](../Topic/COleClientItem::GetDrawAspect.md)|获取呈现的项目的当前视图。|  
|[COleClientItem::GetExtent](../Topic/COleClientItem::GetExtent.md)|返回OLE项的矩形区域。|  
|[COleClientItem::GetIconFromRegistry](../Topic/COleClientItem::GetIconFromRegistry.md)|Retrives到图标的句柄与特定CLSID的服务器。|  
|[COleClientItem::GetIconicMetafile](../Topic/COleClientItem::GetIconicMetafile.md)|获取该图元文件用于绘制项的图标。|  
|[COleClientItem::GetInPlaceWindow](../Topic/COleClientItem::GetInPlaceWindow.md)|返回指向项目的就地编辑窗口。|  
|[COleClientItem::GetItemState](../Topic/COleClientItem::GetItemState.md)|获取项的当前状态。|  
|[COleClientItem::GetLastStatus](../Topic/COleClientItem::GetLastStatus.md)|返回最后OLE操作的状态。|  
|[COleClientItem::GetLinkUpdateOptions](../Topic/COleClientItem::GetLinkUpdateOptions.md)|返回一个链接的项目\(高级功能\)更新模式。|  
|[COleClientItem::GetType](../Topic/COleClientItem::GetType.md)|返回类型\(嵌入链接，或静态\)的OLE项。|  
|[COleClientItem::GetUserType](../Topic/COleClientItem::GetUserType.md)|获取描述项类型的字符串。|  
|[COleClientItem::IsInPlaceActive](../Topic/COleClientItem::IsInPlaceActive.md)|如果项目是就地活动状态，返回 `TRUE`。|  
|[COleClientItem::IsLinkUpToDate](../Topic/COleClientItem::IsLinkUpToDate.md)|如果链接项的最新与其源文档，返回 **TRUE**。|  
|[COleClientItem::IsModified](../Topic/COleClientItem::IsModified.md)|返回 `TRUE`，如果修改项目，则它上次保存了。|  
|[COleClientItem::IsOpen](../Topic/COleClientItem::IsOpen.md)|如果项目中当前打开服务器应用程序，返回 `TRUE`。|  
|[COleClientItem::IsRunning](../Topic/COleClientItem::IsRunning.md)|如果项目的服务器应用程序运行，返回 `TRUE`。|  
|[COleClientItem::OnActivate](../Topic/COleClientItem::OnActivate.md)|调用由框架通知项目激活它。|  
|[COleClientItem::OnActivateUI](../Topic/COleClientItem::OnActivateUI.md)|调用由框架通知项目激活它应显示其用户界面。|  
|[COleClientItem::OnChange](../Topic/COleClientItem::OnChange.md)|调用，当服务器更改OLE项。  需要的实现。|  
|[COleClientItem::OnDeactivate](../Topic/COleClientItem::OnDeactivate.md)|调用由结构，当停用项目。|  
|[COleClientItem::OnDeactivateUI](../Topic/COleClientItem::OnDeactivateUI.md)|调用由结构，当服务器移除了就地用户界面。|  
|[COleClientItem::OnGetClipboardData](../Topic/COleClientItem::OnGetClipboardData.md)|调用由框架获取要复制的数据保存到剪贴板。|  
|[COleClientItem::OnInsertMenus](../Topic/COleClientItem::OnInsertMenus.md)|调用由框架创建复合菜单。|  
|[COleClientItem::OnRemoveMenus](../Topic/COleClientItem::OnRemoveMenus.md)|调用由框架从复合菜单移除容器的菜单。|  
|[COleClientItem::OnSetMenu](../Topic/COleClientItem::OnSetMenu.md)|调用framework安装和移除复合菜单。|  
|[COleClientItem::OnShowControlBars](../Topic/COleClientItem::OnShowControlBars.md)|调用由结构显示和隐藏控件条。|  
|[COleClientItem::OnUpdateFrameTitle](../Topic/COleClientItem::OnUpdateFrameTitle.md)|调用由框架更新框架窗口的标题栏。|  
|[COleClientItem::ReactivateAndUndo](../Topic/COleClientItem::ReactivateAndUndo.md)|重新激活项和移除最后就地编辑操作。|  
|[COleClientItem::Release](../Topic/COleClientItem::Release.md)|如果它是打开的，随OLE链接项的连接并将其关闭。  不销毁客户端项目。|  
|[COleClientItem::Reload](../Topic/COleClientItem::Reload.md)|在调用后重新加载项目。`ActivateAs`。|  
|[COleClientItem::Run](../Topic/COleClientItem::Run.md)|运行应用程序与该项目。|  
|[COleClientItem::SetDrawAspect](../Topic/COleClientItem::SetDrawAspect.md)|设置呈现的项目的当前视图。|  
|[COleClientItem::SetExtent](../Topic/COleClientItem::SetExtent.md)|设置OLE项的边框。|  
|[COleClientItem::SetHostNames](../Topic/COleClientItem::SetHostNames.md)|设置服务器显示，编辑OLE项时的名称。|  
|[COleClientItem::SetIconicMetafile](../Topic/COleClientItem::SetIconicMetafile.md)|该图元文件用于绘制项的图标使用的缓存。|  
|[COleClientItem::SetItemRects](../Topic/COleClientItem::SetItemRects.md)|设置项目的边框。|  
|[COleClientItem::SetLinkUpdateOptions](../Topic/COleClientItem::SetLinkUpdateOptions.md)|设置一个链接的项目\(高级功能\)更新模式。|  
|[COleClientItem::SetPrintDevice](../Topic/COleClientItem::SetPrintDevice.md)|将此客户端项目的输出目标设备。|  
|[COleClientItem::UpdateLink](../Topic/COleClientItem::UpdateLink.md)|更新项目的表示缓存。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[COleClientItem::CanActivate](../Topic/COleClientItem::CanActivate.md)|调用由框架确定就地激活是否允许。|  
|[COleClientItem::OnChangeItemPosition](../Topic/COleClientItem::OnChangeItemPosition.md)|调用由框架，该项目的位置更改。|  
|[COleClientItem::OnDeactivateAndUndo](../Topic/COleClientItem::OnDeactivateAndUndo.md)|调用由框架在启动后取消。|  
|[COleClientItem::OnDiscardUndoState](../Topic/COleClientItem::OnDiscardUndoState.md)|调用由框架放弃该项的撤消状态信息。|  
|[COleClientItem::OnGetClipRect](../Topic/COleClientItem::OnGetClipRect.md)|调用由框架获取项目的矩形剪辑协调。|  
|[COleClientItem::OnGetItemPosition](../Topic/COleClientItem::OnGetItemPosition.md)|调用由框架获取项的位置相对于视图。|  
|[COleClientItem::OnGetWindowContext](../Topic/COleClientItem::OnGetWindowContext.md)|调用由结构，当就地激活项目。|  
|[COleClientItem::OnScrollBy](../Topic/COleClientItem::OnScrollBy.md)|调用由框架移动项到视图。|  
|[COleClientItem::OnShowItem](../Topic/COleClientItem::OnShowItem.md)|调用由结构显示OLE项。|  
  
## 备注  
 OLE项表示数据，创建，并维护由服务器应用程序，可以“无缝”合并到文档中，以便向用户显示单文件。  结果为“多文档”组成的OLE项，并包含文档。  
  
 可以嵌入到OLE项或链接。  如果嵌入它，为复合文档的一部分，其数据存储区。  如果该链接，其数据存储为服务器应用程序创建的一个单独的文件中，因此，该文件的一个链接在多个文档存储。  任何OLE项包含指定应调用编辑这些服务器应用程序的信息。  
  
 `COleClientItem` 定义调用以响应来自服务器应用程序的请求的若干可重写的函数;这些overridables通常作为通知。  这允许服务器应用程序通知用户进行，编辑OLE项的容器更改，或者检索在编辑过程中所需的信息。  
  
 `COleClientItem` 可用于 [COleDocument](../../mfc/reference/coledocument-class.md)、 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)或 [COleServerDoc](../../mfc/reference/coleserverdoc-class.md) 选件类。  若要使用 `COleClientItem`，从中派生选件类并实现 [OnChange](../Topic/COleClientItem::OnChange.md) 成员函数，定义容器如何响应所做的更改到项目。  若要支持就地激活，请重写 [OnGetItemPosition](../Topic/COleClientItem::OnGetItemPosition.md) 成员函数。  此功能提供有关OLE项的显示位置的信息。  
  
 有关使用容器接口的更多信息，请参见位于 [容器:实现容器](../../mfc/containers-implementing-a-container.md) 和 [启动](../../mfc/activation-cpp.md)。  
  
> [!NOTE]
>  [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] 引用嵌入的资源和链接的项目为“对象”是指项类型为“选件类”。此引用使用术语“项”与相应的C\+\+对象区分OLE实体和该术语“type”的C\+\+选件类区分OLE类别。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 `COleClientItem`  
  
## 要求  
 **Header:** afxole.h  
  
## 请参阅  
 [MFC示例MFCBIND](../../top/visual-cpp-samples.md)   
 [MFC示例OCLIENT](../../top/visual-cpp-samples.md)   
 [CDocItem Class](../../mfc/reference/cdocitem-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleServerItem Class](../../mfc/reference/coleserveritem-class.md)