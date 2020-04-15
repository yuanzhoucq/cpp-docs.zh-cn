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
ms.openlocfilehash: a08b6ff274c73d301c156d65aa56fbecca49128c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370552"
---
# <a name="data-objects-and-data-sources-manipulation"></a>数据对象和数据源：操作

创建数据对象或数据源后，可以对数据执行许多常见操作，例如插入和删除数据、枚举数据中的格式等。 本文介绍了完成最常见操作所需的技术。 主题包括：

- [将数据插入数据源](#_core_inserting_data_into_a_data_source)

- [确定数据对象中可用的格式](#_core_determining_the_formats_available_in_a_data_object)

- [从数据对象检索数据](#_core_retrieving_data_from_a_data_object)

## <a name="inserting-data-into-a-data-source"></a><a name="_core_inserting_data_into_a_data_source"></a>将数据插入数据源

数据如何插入到数据源取决于数据是立即提供还是按需提供，以及数据在哪个介质中提供。 可能性如下。

### <a name="supplying-data-immediately-immediate-rendering"></a>立即提供数据（立即呈现）

- 重复`COleDataSource::CacheGlobalData`调用提供数据的每个剪贴板格式。 传递要使用的剪贴板格式、包含数据的内存的句柄，以及描述数据的**FORMATETC**结构。

     -或-

- 如果要直接使用**STGMEDIUM**结构，请调用`COleDataSource::CacheData`而不是`COleDataSource::CacheGlobalData`在上面的选项中。

### <a name="supplying-data-on-demand-delayed-rendering"></a>按需提供数据（延迟渲染）

这是一个高级主题。

- 重复`COleDataSource::DelayRenderData`调用提供数据的每个剪贴板格式。 传递要使用的剪贴板格式，以及（可选）描述数据的**FORMATETC**结构。 请求数据时，框架将调用`COleDataSource::OnRenderData`必须覆盖的 。

     -或-

- 如果使用`CFile`对象提供数据，请调用`COleDataSource::DelayRenderFileData`而不是`COleDataSource::DelayRenderData`在前面的选项中。 请求数据时，框架将调用`COleDataSource::OnRenderFileData`必须覆盖的 。

## <a name="determining-the-formats-available-in-a-data-object"></a><a name="_core_determining_the_formats_available_in_a_data_object"></a>确定数据对象中可用的格式

在应用程序允许用户将数据粘贴到其中之前，它需要知道剪贴板上是否有可以处理的格式。 为此，应用程序应执行以下操作：

1. 创建`COleDataObject`对象和**FORMATETC**结构。

1. 调用数据对象`AttachClipboard`的成员函数，将数据对象与剪贴板上的数据相关联。

1. 执行下列操作之一：

   - 如果只需要一种或两`IsDataAvailable`种格式，请调用数据对象的成员函数。 如果剪贴板上的数据支持格式明显多于应用程序，这将节省您的时间。

     \- 或 -

   - 调用数据对象`BeginEnumFormats`的成员函数开始枚举剪贴板上可用的格式。 然后调用`GetNextFormat`，直到剪贴板返回应用程序支持的格式或没有更多格式。

如果使用**ON_UPDATE_COMMAND_UI**，现在可以启用"粘贴"，并可能在"编辑"菜单上粘贴特殊项目。 为此，请调用 任`CMenu::EnableMenuItem`一`CCmdUI::Enable`或 。 有关容器应用程序应如何处理菜单项以及何时执行的详细信息，请参阅[菜单和资源：容器添加](../mfc/menus-and-resources-container-additions.md)。

## <a name="retrieving-data-from-a-data-object"></a><a name="_core_retrieving_data_from_a_data_object"></a>从数据对象检索数据

决定数据格式后，剩下的就是从数据对象中检索数据。 为此，用户决定将数据放在何处，应用程序调用相应的函数。 数据将在以下介质之一提供：

|中型|调用函数|
|------------|----------------------|
|全局内存`HGLOBAL`（ ）|`COleDataObject::GetGlobalData`|
|文件`CFile`（ ）|`COleDataObject::GetFileData`|
|**STGMEDIUM**结构`IStorage`（ ）|`COleDataObject::GetData`|

通常，媒体将与其剪贴板格式一起指定。 例如 **，CF_EMBEDDEDSTRUCT**对象始终位于需要`IStorage`**STGMEDIUM**结构的介质中。 因此，您将使用`GetData`，因为它是这些函数中唯一可以接受**STGMEDIUM**结构的功能。

对于剪贴板格式处于`IStream`或`HGLOBAL`介质中的情况，框架可以提供引用数据的`CFile`指针。 然后，应用程序可以使用文件读取来获取数据的方式与从文件导入数据的方式大致相同。 本质上，这是数据源中 和`OnRenderData``OnRenderFileData`例程的客户端接口。

用户现在可以像将相同格式的任何其他数据一样将数据插入到文档中。

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [拖放](../mfc/drag-and-drop-ole.md)

- [剪贴板](../mfc/clipboard.md)

## <a name="see-also"></a>另请参阅

[数据对象和数据源 （OLE）](../mfc/data-objects-and-data-sources-ole.md)<br/>
[COleDataObject 类](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource 类](../mfc/reference/coledatasource-class.md)
