---
title: "数据对象和数据源：操作 | Microsoft Docs"
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
  - "剪贴板 [C++], 确定可用格式"
  - "剪贴板 [C++], 传递格式信息"
  - "数据对象 [C++], 操作"
  - "数据源 [C++], 数据操作"
  - "数据源 [C++], 确定可用格式"
  - "数据源 [C++], 插入数据"
  - "延迟的呈现 [C++]"
  - "OLE [C++], 数据对象"
  - "OLE [C++], 数据源"
ms.assetid: f7f27e77-bb5d-4131-b819-d71bf929ebaf
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 数据对象和数据源：操作
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在数据对象或创建数据源之后，可以对数据执行的常见操作，如插入，并移除的数据，如何枚举格式化数据等等。  本文描述必需的最常见技术来完成的操作。  主题包括：  
  
-   [插入到数据源中的数据](#_core_inserting_data_into_a_data_source)  
  
-   [确定格式可用在数据对象](#_core_determining_the_formats_available_in_a_data_object)  
  
-   [从数据对象检索数据](#_core_retrieving_data_from_a_data_object)  
  
##  <a name="_core_inserting_data_into_a_data_source"></a> 插入到数据源中的数据  
 数据如何插入数据源确定是否提供数据立即或在需要时，然后在其中进行媒体提供。  可能性如下所示。  
  
### 提供的数据立即 \(立即呈现\)  
  
-   所提供数据的每剪贴板格式的重复调用 `COleDataSource::CacheGlobalData`。  将剪贴板格式被使用的句柄，内存中的数据，因此，可选择，描述数据的结构 **FORMATETC**。  
  
     \- 或 \-  
  
-   如果要直接使用 **STGMEDIUM** 结构。使用，则调用 `COleDataSource::CacheData` 而不是单击上半部分的 `COleDataSource::CacheGlobalData` 选项。  
  
### 提供的数据按需 \(延迟\) 的呈现  
 这是一个高级主题。  
  
-   所提供数据的每剪贴板格式的重复调用 `COleDataSource::DelayRenderData`。  将剪贴板格式被使用，且中，选择，描述数据的结构 **FORMATETC**。  当数据请求，框架调用 `COleDataSource::OnRenderData`，您必须重写此方法。  
  
     \- 或 \-  
  
-   如果使用 `CFile` 对象提供数据，请调用 `COleDataSource::DelayRenderFileData` 而不是前面的 `COleDataSource::DelayRenderData` 选项。  当数据请求，框架调用 `COleDataSource::OnRenderFileData`，您必须重写此方法。  
  
##  <a name="_core_determining_the_formats_available_in_a_data_object"></a> 确定格式可用在数据对象  
 在应用程序允许用户将该数据粘贴到之前，需要知道是否对该剪贴板中可以处理的格式。  若要执行此，应用程序应执行以下操作：  
  
1.  创建 `COleDataObject` 对象并 **FORMATETC** 结构。  
  
2.  调用数据对象的 `AttachClipboard` 成员函数关联数据对象与剪贴板上的数据。  
  
3.  执行下列操作之一：  
  
    -   调用数据对象的 `IsDataAvailable` 成员函数中是否只有所需的数据格式。  在剪贴板上的数据比应用程序的情况下，支持更格式这将节省时间。  
  
         \- 或 \-  
  
    -   调用数据对象的 `BeginEnumFormats` 成员函数开始枚举格式可用剪贴板上。  然后调用 `GetNextFormat`，直到返回剪贴板格式应用程序或支持目的格式。  
  
 如果您使用 `ON_UPDATE_COMMAND_UI`，您现在可以使用，因此，粘贴可能，粘贴在"编辑"菜单上的特定项。  为此，请调用 `CMenu::EnableMenuItem` 或 `CCmdUI::Enable`。  有关要完成工作的更多信息容器应用程序应执行与菜单项，并且，如果为，请参见 [菜单和资源：容器添加](../mfc/menus-and-resources-container-additions.md)。  
  
##  <a name="_core_retrieving_data_from_a_data_object"></a> 从数据对象检索数据  
 一旦确定的数据格式，任何仍是从数据对象检索数据。  为此，该用户决定在何处放置数据，并且，应用程序会调用适当的函数。  数据在下列媒介之一中可用：  
  
|中|调用函数|  
|-------|----------|  
|共用内存 \(`HGLOBAL`\)|`COleDataObject::GetGlobalData`|  
|文件 \(`CFile`\)|`COleDataObject::GetFileData`|  
|**STGMEDIUM** 结构 \(`IStorage`\)|`COleDataObject::GetData`|  
  
 通常，由媒体与其一起将剪贴板格式指定。  例如，**CF\_EMBEDDEDSTRUCT** 对象需要一个始终位于 **STGMEDIUM** 结构媒体的 `IStorage`。  因此，使用 `GetData`，因为它能接受 **STGMEDIUM** 结构中只有一个这些函数。  
  
 对剪贴板格式在 `IStream` 或 `HGLOBAL` 媒体的情况，框架可提供引用数据的 `CFile` 指针。  应用程序然后可以使用读取文件获取数据，方法与可能导入数据文件的方式。  实质上，这样是客户端界面到数据源中 `OnRenderData` 和 `OnRenderFileData` 例程。  
  
 用户现在可以将数据插入文档与在同一格式的其他数据。  
  
### 您想进一步了解什么？  
  
-   [拖放](../mfc/drag-and-drop-ole.md)  
  
-   [Clipboard](../mfc/clipboard.md)  
  
## 请参阅  
 [数据对象和数据源 \(OLE\)](../mfc/data-objects-and-data-sources-ole.md)   
 [COleDataObject Class](../mfc/reference/coledataobject-class.md)   
 [COleDataSource Class](../mfc/reference/coledatasource-class.md)