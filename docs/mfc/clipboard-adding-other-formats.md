---
title: 剪贴板：添加其他格式
ms.date: 11/04/2016
helpviewer_keywords:
- formats [MFC], Clipboard
- Clipboard, formats
- custom formats, placing on Clipboard
- custom formats
- registering custom Clipboard data formats
- custom Clipboard data formats
ms.assetid: aea58159-65ed-4385-aeaa-3d9d5281903b
ms.openlocfilehash: 6f4e159cc1b6918843d4a164dcca88500eb7b038
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374608"
---
# <a name="clipboard-adding-other-formats"></a>剪贴板：添加其他格式

本主题介绍如何扩展支持的格式列表，尤其是 OLE 支持格式。 主题[剪贴板：复制和粘贴数据](../mfc/clipboard-copying-and-pasting-data.md)描述了支持从剪贴板复制和粘贴所需的最小实现。 如果这是您实现的所有格式，则剪贴板上放置的唯一格式是**CF_METAFILEPICT、CF_EMBEDSOURCE、CF_OBJECTDESCRIPTOR，** 并且可能**CF_METAFILEPICT****CF_LINKSOURCE。** **CF_OBJECTDESCRIPTOR** 大多数应用程序在剪贴板上需要比这三种格式更多的格式。

## <a name="registering-custom-formats"></a><a name="_core_registering_custom_formats"></a>注册自定义格式

要创建自己的自定义格式，请遵循注册任何自定义剪贴板格式时使用的相同过程：将格式的名称传递给**RegisterClipboard格式**函数，并将其返回值用作格式 ID。

## <a name="placing-formats-on-the-clipboard"></a><a name="_core_placing_formats_on_the_clipboard"></a>在剪贴板上放置格式

要向放置在剪贴板上的格式添加更多格式，必须覆盖从 或`OnGetClipboardData`或`COleClientItem``COleServerItem`派生的类中的函数（具体取决于要复制的数据是否为本机）。 在此函数中，应使用以下过程。

#### <a name="to-place-formats-on-the-clipboard"></a>将格式放在剪贴板上

1. 创建 `COleDataSource` 对象。

1. 将此数据源传递给一个函数，该函数通过调用`COleDataSource::CacheGlobalData`将本机数据格式添加到受支持的格式列表中。

1. 通过调用`COleDataSource::CacheGlobalData`要支持的每个标准格式来添加标准格式。

此技术用于 MFC OLE 示例程序[HIERSVR（](../overview/visual-cpp-samples.md)检查`OnGetClipboardData` **CServerItem**类的成员函数）。 此示例中的唯一区别是，步骤 3 未实现，因为 HIERSVR 不支持其他标准格式。

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [OLE 数据对象和数据源以及统一数据传输](../mfc/data-objects-and-data-sources-ole.md)

- [OLE 拖放](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>另请参阅

[剪贴板：使用 OLE 剪贴板机制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)
