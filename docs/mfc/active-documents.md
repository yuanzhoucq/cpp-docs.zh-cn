---
title: "活动文档 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- active documents [MFC]
- active documents [MFC], requirements
- view objects [MFC], requirements
- OLE [MFC], active documents
- views [MFC], active documents
- active documents [MFC], views
ms.assetid: 1378f18e-aaa6-420b-8501-4b974905baa0
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 52f3165f69d47f63fc52ae01bbbd1947e7755a43
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="active-documents"></a>活动文档
活动文档扩展了 OLE 的复合文档技术。 这些扩展是以管理视图的其他界面的形式提供的，因此对象可在容器中正常运行，并且保持对其显示和打印功能的控制。 此过程使在外部框架（如 Microsoft Office Binder 或 Microsoft Internet Explorer）和本机框架（如产品自己的视区）中显示文档成为可能。  
  
 本节描述实用[活动文档要求](#requirements_for_active_documents)。 活动文档拥有一组数据并对其中可保存和检索数据的存储具有访问权限。 它可以针对其数据创建和管理一个或多个视图。 除了支持 OLE 文档的通用嵌入和就地激活接口之外，活动文档还传递其功能以通过 `IOleDocument` 创建视图。 通过此接口，容器可要求创建（并且可能枚举）活动文档可显示的视图。 通过此接口，活动文档还可提供有关自身的杂项信息，如它是否支持多个视图或复杂矩形。  
  
 以下是**IOleDocument**接口。 请注意， **IEnumOleDocumentViews**接口是标准 OLE 枚举器**IOleDocumentView \*** 类型。  
  
```  
interface IOleDocument : IUnknown  
    {  
    HRESULT CreateView(  
        [in] IOleInPlaceSite *pIPSite,  
        [in] IStream *pstm,  
        [in] DWORD dwReserved,  
        [out] IOleDocumentView **ppView);  

    HRESULT GetDocMiscStatus([out] DWORD *pdwStatus);  

    HRESULT EnumViews(  
        [out] IEnumOleDocumentViews **ppEnum,  
        [out] IOleDocumentView **ppView);  
    }  
```  
  
 每个活动文档必须具有一个视图框架提供程序以及此接口。 如果文档未嵌入容器中，则活动文档服务器自身必须提供视图框架。 但是，在活动文档容器中嵌入活动文档后，容器将提供视图框架。  
  
 活动文档可以创建一个或多个类型的[视图](#requirements_for_view_objects)其数据的 （例如，正常、 概述、 页面布局，等等）。 视图的行为像通过其可查看数据的筛选器。 即使该文档具有仅一种类型的视图，可能仍想要支持多个视图作为一种支持新的窗口功能 (例如，**新窗口**项**窗口**办公室中的菜单应用程序）。  
  
##  <a name="requirements_for_active_documents"></a>活动文档需求  
 可在活动文档容器中显示的活动文档必须：  
  
-   通过实现 `IPersistStorage`，使用 OLE 的复合文件作为存储机制。  
  
-   支持 OLE 文档，包括的基础嵌入功能**从文件创建**。 这需要 `IPersistFile`、`IOleObject` 和 `IDataObject` 接口。  
  
-   支持一个或多个视图，每个视图均能就地激活。 也就是说，视图必须支持接口`IOleDocumentView`及介面`IOleInPlaceObject`和`IOleInPlaceActiveObject`(使用容器的**IOleInPlaceSite**和**IOleInPlaceFrame**接口）。  
  
-   支持标准活动文档接口 `IOleDocument`、`IOleCommandTarget` 和 `IPrint`。  
  
 这些需求中暗示了解何时以及如何使用容器端接口。  
  
##  <a name="requirements_for_view_objects"></a>视图对象需求  
 活动文档可以为其数据创建一个或多个视图。 从功能上来说，这些视图类似于特定方法上的用于显示数据的端口。 如果活动文档只支持单个视图，则可使用单个类实现活动文档及其支持的单个视图。 **Ioledocument::**返回相同对象的`IOleDocumentView`接口指针。  
  
 若要能在活动文档容器内表示，视图组件必须支持**IOleInPlaceObject**和**IOleInPlaceActiveObject**除了`IOleDocumentView`:  
  
```  
interface IOleDocumentView : IUnknown  
    {  
    HRESULT SetInPlaceSite([in] IOleInPlaceSite *pIPSite);  
    HRESULT GetInPlaceSite([out] IOleInPlaceSite **ppIPSite);  
    HRESULT GetDocument([out] IUnknown **ppunk);  
    [input_sync] HRESULT SetRect([in] LPRECT prcView);  
    HRESULT GetRect([in] LPRECT prcView);  
    [input_sync] HRESULT SetRectComplex(  
        [in] LPRECT prcView,  
        [in] LPRECT prcHScroll,  
        [in] LPRECT prcVScroll,  
        [in] LPRECT prcSizeBox);  
    HRESULT Show([in] BOOL fShow);  
    HRESULT UIActivate([in] BOOL fUIActivate);  
    HRESULT Open(void);  
    HRESULT CloseView([in] DWORD dwReserved);  
    HRESULT SaveViewState([in] IStream *pstm);  
    HRESULT ApplyViewState([in] IStream *pstm);  
    HRESULT Clone(  
        [in] IOleInPlaceSite *pIPSiteNew,  
        [out] IOleDocumentView **ppViewNew);  
    }  
```  
  
 每个视图都具有关联视图站点，其将封装视图框架和视区（窗口中的 HWND 和矩形区域）。 站点的公开此功能通过标准**IOleInPlaceSite**接口。 请注意，一个 HWND 上可具有多个视区。  
  
 通常，视图的每种类型具有不同的打印表示形式。 因此，视图和对应的视图站点应分别实现打印接口 `IPrint` 和 `IContinueCallback`。 视图框架必须通过的视图提供与协商**IPrint**当打印开始，以便正确打印页眉、 页脚、 边距和相关的元素。 视图提供程序通过 `IContinueCallback` 向框架通知打印相关事件。 有关使用这些接口的详细信息，请参阅[以编程方式打印](../mfc/programmatic-printing.md)。  
  
 请注意，如果活动文档仅支持单个视图，则可使用单个具体类实现活动文档和其支持的单个视图。 **Ioledocument::**只需返回相同对象的`IOleDocumentView`接口指针。 总之，当只需要一个视图时不必具有两个不同的对象实例。  
  
 视图对象也可以是命令目标。 通过实现`IOleCommandTarget`视图可以接收源自容器的用户界面的命令 (如**新建**，**打开**，**另存为**， **打印**上**文件**菜单; 和**复制**，**粘贴**，**撤消**上**编辑**菜单)。 有关详细信息，请参阅[消息处理和命令目标](../mfc/message-handling-and-command-targets.md)。  
  
## <a name="see-also"></a>请参阅  
 [活动文档包容](../mfc/active-document-containment.md)

