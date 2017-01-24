---
title: "活动文档 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "活动文档 [C++]"
  - "活动文档 [C++], 要求"
  - "活动文档 [C++], 视图"
  - "OLE [C++], 活动文档"
  - "视图对象, 要求"
  - "视图 [C++], 活动文档"
ms.assetid: 1378f18e-aaa6-420b-8501-4b974905baa0
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 活动文档
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

活动文档扩展 OLE 组合文档技术。  在管理视图的附加接口窗体中提供这些扩展，因此对象可以在该容器中运行，仍保留控制其显示和打印函数的控制。  此过程可以显示在文档外部帧 \(例如 Microsoft Office 活页夹或 Microsoft Internet Explorer\) 和在本机帧 \(如产品的视区\)。  
  
 本节描述功能性的 [活动文档的要求](#requirements_for_active_documents)。  活动文档拥有一组数据并在保存和检索数据的地方存储。  可以创建和管理在其数据的一个或多个视图。  除了支持 OLE 文档通常嵌入和就地激活接口外，对活动文档通信其功能通过 `IOleDocument`创建视图。  通过这个接口，容器可以要求创建 \(可能枚举\) 文档显示活动的视图。  通过此接口，活动文档还提供有关其自身的杂项信息，如它是否支持多视图或复杂矩形。  
  
 以下为 **IOleDocument** 接口。  注意 **IEnumOleDocumentViews** 接口是 **IOleDocumentView \*** 类型的标准 OLE 枚举器。  
  
 `interface IOleDocument : IUnknown`  
  
 `{`  
  
 `HRESULT CreateView(`  
  
 `[in] IOleInPlaceSite *pIPSite,`  
  
 `[in] IStream *pstm,`  
  
 `[in] DWORD dwReserved,`  
  
 `[out] IOleDocumentView **ppView);`  
  
 `HRESULT GetDocMiscStatus([out] DWORD *pdwStatus);`  
  
 `HRESULT EnumViews(`  
  
 `[out] IEnumOleDocumentViews **ppEnum,`  
  
 `[out] IOleDocumentView **ppView);`  
  
 `}`  
  
 每个活动文档必须有与此接口的视图框架提供程序。  如果文档未嵌入容器中，活动文档服务器必须提供视图框架。  但是，在活动文档容器中当活动文档嵌入时，容器提供视图框架。  
  
 活动文档创建了一个或多个其数据的数据[视图](#requirements_for_view_objects) 类型 \(例如，常规、大纲，页面布局，等等\)。  视图像筛选器一样通过它可以显示数据。  即使将文档只有视图一种类型，您可能仍要支持多视图作为支持新窗口功能的方法 \(例如，Office 应用程序中，在 **窗口** 菜单的的**新建窗口** 项 \)。  
  
##  <a name="requirements_for_active_documents"></a> 需要活动文档  
 在活动文档容器中显示活动的文档必须：  
  
-   使用 OLE 的复合文件作为存储机制通过实现 `IPersistStorage`。  
  
-   支持 OLE 文档基础的嵌入功能，包括 **Create From File**。  这需要 `IPersistFile`接口、`IOleObject`和 `IDataObject`。  
  
-   支持一个或多个视图，每一个能够就地激活上。  即视图必须支持 `IOleDocumentView` 接口以及 `IOleInPlaceObject` 和 `IOleInPlaceActiveObject` \(使用容器的 **IOleInPlaceSite** 和 **IOleInPlaceFrame** 接口\)。  
  
-   支持标准活动文档界面 \(MDI\) `IOleDocument`、`IOleCommandTarget`和 `IPrint`。  
  
 了解使用容器主端接口时间以及这些要求表示。  
  
##  <a name="requirements_for_view_objects"></a> 要求视图对象  
 活动文档可以创建其数据的一个或多个视图。  从功能上来说，这些视图与到特定方法上的端口显示的数据相似。  如果活动文档只支持单个视图，使用单个类可以实现活动文档和该文档的单个视图。  **IOleDocument::CreateView** 返回相同的对象的 `IOleDocumentView` 接口指针。  
  
 除了 `IOleDocumentView`以外，在活动文档容器中，表示视图组件必须支持 **IOleInPlaceObject** 和 **IOleInPlaceActiveObject** :  
  
 `interface IOleDocumentView : IUnknown`  
  
 `{`  
  
 `HRESULT SetInPlaceSite([in] IOleInPlaceSite *pIPSite);`  
  
 `HRESULT GetInPlaceSite([out] IOleInPlaceSite **ppIPSite);`  
  
 `HRESULT GetDocument([out] IUnknown **ppunk);`  
  
 `[input_sync] HRESULT SetRect([in] LPRECT prcView);`  
  
 `HRESULT GetRect([in] LPRECT prcView);`  
  
 `[input_sync] HRESULT SetRectComplex(`  
  
 `[in] LPRECT prcView,`  
  
 `[in] LPRECT prcHScroll,`  
  
 `[in] LPRECT prcVScroll,`  
  
 `[in] LPRECT prcSizeBox);`  
  
 `HRESULT Show([in] BOOL fShow);`  
  
 `HRESULT UIActivate([in] BOOL fUIActivate);`  
  
 `HRESULT Open(void);`  
  
 `HRESULT CloseView([in] DWORD dwReserved);`  
  
 `HRESULT SaveViewState([in] IStream *pstm);`  
  
 `HRESULT ApplyViewState([in] IStream *pstm);`  
  
 `HRESULT Clone(`  
  
 `[in] IOleInPlaceSite *pIPSiteNew,`  
  
 `[out] IOleDocumentView **ppViewNew);`  
  
 `}`  
  
 每个视图都具有关联视图站点，封装视图帧和视和视图区域 \(窗口中的矩形区域\) 。  网站公开此功能，尽管标准 **IOleInPlaceSite** 接口。  记录在单个 HWND上拥有不止一个的视图端口是可能的。  
  
 通常，视图的每种类型具有不同的打印表示。  因此，如果分别是 `IPrint` 和 `IContinueCallback`，视图和对应的视图站点应实现打印接口。  当打印开始时，通过 **IPrint** 视图框架必须与视图提供程序协调，以便标题、脚注、边距和相关元素正确打印。  通过 `IContinueCallback`视图提供程序通知打印相关事件的框架。  有关这些接口的更多信息，请参见[以编程方式打印](../mfc/programmatic-printing.md)。  
  
 注意，如果活动文档只支持单个视图，使用单个具体类可以实现活动文档和该文档的单个视图。  **IOleDocument::CreateView** 返回相同的对象的 `IOleDocumentView` 接口指针。  为简单起见，当只需要一个视图时不需要具有两个不同对象实例。  
  
 视图对象也可以是命令目标。  通过实现 `IOleCommandTarget` 视图中接收自在容器的用户界面的命令 \(如，在 **文件** 菜单上的 **新建**，**打开**，**另存为**， **打印** ;在 **编辑** 菜单上的 **复制**、**粘贴撤消**，\)。  有关详细信息，请参阅[消息处理和命令目标](../mfc/message-handling-and-command-targets.md)。  
  
## 请参阅  
 [活动文档包容](../mfc/active-document-containment.md)