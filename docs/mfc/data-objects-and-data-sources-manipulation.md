---
title: 数据对象和数据源：操作
ms.date: 11/04/2016
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
ms.openlocfilehash: 81dfe911866c4d1ba1720ee2c9854076c499f0a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241544"
---
# <a name="data-objects-and-data-sources-manipulation"></a>数据对象和数据源：操作

创建数据对象或数据源后，可以执行大量的数据，例如插入和删除数据，枚举数据采用的格式和的详细信息上的常规操作。 本文介绍完成最常见的操作所需的技术。 包括以下主题：

- [将数据插入到数据源](#_core_inserting_data_into_a_data_source)

- [确定数据对象中的可用格式](#_core_determining_the_formats_available_in_a_data_object)

- [从数据对象中检索数据](#_core_retrieving_data_from_a_data_object)

##  <a name="_core_inserting_data_into_a_data_source"></a> 将数据插入到数据源

如何将数据插入到数据源取决于是否立即提供数据或按需，和何种介质中提供。 可能的值如下所示。

### <a name="supplying-data-immediately-immediate-rendering"></a>立即提供数据 （立即呈现）

- 调用`COleDataSource::CacheGlobalData`重复的每种剪贴板格式，在其中你所提供的数据。 传递要使用的剪贴板格式的句柄包含数据的内存和 （可选） **FORMATETC**描述数据结构。

     或

- 如果想要直接使用**STGMEDIUM**结构，则调用`COleDataSource::CacheData`而不是`COleDataSource::CacheGlobalData`在上面的选项。

### <a name="supplying-data-on-demand-delayed-rendering"></a>提供按需 （延迟的呈现） 的数据

这是一个高级的主题。

- 调用`COleDataSource::DelayRenderData`重复的每种剪贴板格式，在其中你所提供的数据。 传递要使用的剪贴板格式和 （可选） **FORMATETC**描述数据结构。 当请求数据时，框架将调用`COleDataSource::OnRenderData`，后者必须重写。

     或

- 如果您使用`CFile`要提供的数据对象调用`COleDataSource::DelayRenderFileData`而不是`COleDataSource::DelayRenderData`前一选项。 当请求数据时，框架将调用`COleDataSource::OnRenderFileData`，后者必须重写。

##  <a name="_core_determining_the_formats_available_in_a_data_object"></a> 确定数据对象中的可用格式

应用程序允许用户将数据粘贴到它之前，它需要知道它可以处理在剪贴板上是否存在格式。 若要执行此操作，你的应用程序应执行以下操作：

1. 创建`COleDataObject`对象和一个**FORMATETC**结构。

1. 调用数据对象的`AttachClipboard`成员函数以将数据对象与剪贴板上的数据相关联。

1. 执行下列操作之一：

   - 调用数据对象的`IsDataAvailable`成员函数，如果有一个或两个格式化您的需要。 这样做可以节约时间，在其中剪贴板中的数据支持而与应用程序的更多格式的情况下。

         -or-

   - 调用数据对象的`BeginEnumFormats`成员函数以开始枚举的格式可在剪贴板上。 然后，调用`GetNextFormat`直到剪贴板返回一种格式应用程序支持或有没有更多的格式。

如果使用的**ON_UPDATE_COMMAND_UI**，你现在可以启用粘贴以及可能的编辑菜单上的选择性粘贴项目。 若要执行此操作，调用`CMenu::EnableMenuItem`或`CCmdUI::Enable`。 详细了解哪些容器应用程序应与菜单项和时，请参阅[菜单和资源：添加容器](../mfc/menus-and-resources-container-additions.md)。

##  <a name="_core_retrieving_data_from_a_data_object"></a> 从数据对象中检索数据

一旦您已决定了数据格式，所有的就是此数据对象中检索数据。 若要执行此操作，用户可以决定在何处放置数据，并在应用程序调用相应的函数。 数据可以使用以下介质之一：

|中等|要调用函数|
|------------|----------------------|
|全局内存 (`HGLOBAL`)|`COleDataObject::GetGlobalData`|
|文件 (`CFile`)|`COleDataObject::GetFileData`|
|**STGMEDIUM**结构 (`IStorage`)|`COleDataObject::GetData`|

通常情况下，将其剪贴板格式以及指定介质。 例如， **CF_EMBEDDEDSTRUCT**对象始终处于`IStorage`要求的中等**STGMEDIUM**结构。 因此，您将使用`GetData`因为它是可以接受这些函数仅之一**STGMEDIUM**结构。

有关中的剪贴板格式的情况下`IStream`或`HGLOBAL`框架可以提供中型`CFile`引用的数据的指针。 应用程序然后可以使用读取来获取在很大程度的数据相同的方式，因为它可能会从文件导入数据文件。 实际上，这是客户端的接口`OnRenderData`和`OnRenderFileData`数据源中的例程。

用户可以现在将数据插入到文档如同对任何其他数据格式相同。

### <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [拖放功能](../mfc/drag-and-drop-ole.md)

- [剪贴板](../mfc/clipboard.md)

## <a name="see-also"></a>请参阅

[数据对象和数据源 (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[COleDataObject 类](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource 类](../mfc/reference/coledatasource-class.md)
