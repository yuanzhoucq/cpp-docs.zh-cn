---
title: 数据对象和数据源： 操作 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data objects [MFC], manipulating
- data sources [MFC], data operations
- data sources [MFC], inserting data
- Clipboard [MFC], determining available formats
- OLE [MFC], data objects
- Clipboard [MFC], passing format information
- data sources [MFC], determining available formats
- delayed rendering [MFC]
- OLE [MFC], data sources
ms.assetid: f7f27e77-bb5d-4131-b819-d71bf929ebaf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f276e85be33f3042b19ab7dc6158a4e9f856fb2e
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929856"
---
# <a name="data-objects-and-data-sources-manipulation"></a>数据对象和数据源：操作
已创建的数据对象或数据源后，你可以执行大量的数据，例如插入和删除数据，枚举数据采用的格式和的详细信息的常见操作。 本指南介绍了完成最常见的操作所需的技术。 包括以下主题：  
  
-   [将数据插入到数据源](#_core_inserting_data_into_a_data_source)  
  
-   [确定数据对象中可用的格式](#_core_determining_the_formats_available_in_a_data_object)  
  
-   [从数据对象中检索数据](#_core_retrieving_data_from_a_data_object)  
  
##  <a name="_core_inserting_data_into_a_data_source"></a> 将数据插入到数据源  
 如何将数据插入到数据源取决于是否立即提供数据或按需、 和何种介质中提供。 可能的匹配项如下所示。  
  
### <a name="supplying-data-immediately-immediate-rendering"></a>立即提供数据 （即时呈现）  
  
-   调用`COleDataSource::CacheGlobalData`重复的每种剪贴板格式，在其中你所提供的数据。 传递的剪贴板格式，才能使用包含数据的内存的句柄和 （可选） **FORMATETC**描述数据结构。  
  
     或  
  
-   如果你想要直接使用**STGMEDIUM**调用的结构，`COleDataSource::CacheData`而不是`COleDataSource::CacheGlobalData`在上面的选项。  
  
### <a name="supplying-data-on-demand-delayed-rendering"></a>提供按需 （延迟呈现） 的数据  
 这是一个高级的主题。  
  
-   调用`COleDataSource::DelayRenderData`重复的每种剪贴板格式，在其中你所提供的数据。 传递要使用的剪贴板格式和 （可选） **FORMATETC**描述数据结构。 当请求数据时，框架将调用`COleDataSource::OnRenderData`，后者必须重写。  
  
     或  
  
-   如果你使用`CFile`对象提供数据，调用`COleDataSource::DelayRenderFileData`而不是`COleDataSource::DelayRenderData`在上个选项。 当请求数据时，框架将调用`COleDataSource::OnRenderFileData`，后者必须重写。  
  
##  <a name="_core_determining_the_formats_available_in_a_data_object"></a> 确定数据对象中可用的格式  
 应用程序允许用户将数据粘贴到它之前，它需要知道它可以处理到剪贴板上是否存在格式。 若要执行此操作，你的应用程序应执行以下操作：  
  
1.  创建`COleDataObject`对象和一个**FORMATETC**结构。  
  
2.  调用数据对象的`AttachClipboard`成员函数以将数据对象与剪贴板上的数据相关联。  
  
3.  执行下列操作之一：  
  
    -   调用数据对象的`IsDataAvailable`成员函数，如果有一个或两个格式化你需要。 这样做可以节约时间，在其中剪贴板上的数据支持比你的应用程序的更多格式的情况下。  
  
         或  
  
    -   调用数据对象的`BeginEnumFormats`成员函数开始枚举在剪贴板上可用的格式。 然后调用`GetNextFormat`直到剪贴板返回一种格式支持你的应用程序或有没有更多的格式。  
  
 如果你使用**ON_UPDATE_COMMAND_UI**，你现在可以启用粘贴，而且可能在编辑菜单上的选择性粘贴项。 若要执行此操作，调用`CMenu::EnableMenuItem`或`CCmdUI::Enable`。 有关哪些容器应用程序应使用菜单项执行的操作和时，请参阅[菜单和资源： 容器添加](../mfc/menus-and-resources-container-additions.md)。  
  
##  <a name="_core_retrieving_data_from_a_data_object"></a> 从数据对象中检索数据  
 一旦你已决定数据格式，那么保持是此数据对象中检索数据。 若要执行此操作，用户可以决定在何处放置数据，并在应用程序调用相应的函数。 数据将可在以下的媒体之一：  
  
|中等|函数调用|  
|------------|----------------------|  
|全局内存 (`HGLOBAL`)|`COleDataObject::GetGlobalData`|  
|文件 (`CFile`)|`COleDataObject::GetFileData`|  
|**STGMEDIUM**结构 (`IStorage`)|`COleDataObject::GetData`|  
  
 通常情况下，该媒体将随其剪贴板格式一起指定。 例如， **CF_EMBEDDEDSTRUCT**对象将始终在`IStorage`介质中需要**STGMEDIUM**结构。 因此，将使用`GetData`因为它是可以接受这些函数只有一个**STGMEDIUM**结构。  
  
 对于情况剪贴板格式中`IStream`或`HGLOBAL`中等规模，可以提供框架`CFile`引用的数据的指针。 然后，应用程序可以使用读取获取在很大程度的数据相同的方式，因为它可能会从文件导入数据文件。 从根本上来说，这是客户端接口`OnRenderData`和`OnRenderFileData`数据源中的例程。  
  
 用户可以现在插入到文档中的数据就像任何其他数据相同的格式。  
  
### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [拖放](../mfc/drag-and-drop-ole.md)  
  
-   [剪贴板](../mfc/clipboard.md)  
  
## <a name="see-also"></a>请参阅  
 [数据对象和数据源 (OLE)](../mfc/data-objects-and-data-sources-ole.md)   
 [COleDataObject 类](../mfc/reference/coledataobject-class.md)   
 [COleDataSource 类](../mfc/reference/coledatasource-class.md)
