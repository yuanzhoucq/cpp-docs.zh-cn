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
ms.openlocfilehash: 182abe71ccc9552c113ebb114b4351178e48b096
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58766842"
---
# <a name="clipboard-adding-other-formats"></a>剪贴板：添加其他格式

本主题说明如何扩展支持的格式，尤其是对于 OLE 支持的列表。 本主题[剪贴板：复制和粘贴数据](../mfc/clipboard-copying-and-pasting-data.md)描述了可支持从剪贴板复制和粘贴所需的最小实现。 如果这是所有实现，放置在剪贴板上的唯一格式是**CF_METAFILEPICT**， **CF_EMBEDSOURCE**， **CF_OBJECTDESCRIPTOR**，并可能**CF_LINKSOURCE**。 大多数应用程序将需要更多格式在剪贴板上的比这三个字段。

##  <a name="_core_registering_custom_formats"></a> 注册自定义格式

若要创建您自己的自定义格式，请按照相同的过程注册任何自定义剪贴板格式时，应使用： 传递到格式的名称**RegisterClipboardFormat**函数，并使用它的返回值作为格式 id。

##  <a name="_core_placing_formats_on_the_clipboard"></a> 将格式放置在剪贴板上

若要将更多格式添加到放置在剪贴板上，必须重写`OnGetClipboardData`从派生类中的函数`COleClientItem`或`COleServerItem`（具体取决于是否要复制的数据是本机的）。 在此函数中，应使用以下过程。

#### <a name="to-place-formats-on-the-clipboard"></a>若要将格式放置在剪贴板上

1. 创建 `COleDataSource` 对象。

1. 将此数据源传递到的函数，将本机数据格式添加到支持的格式列表中，通过调用`COleDataSource::CacheGlobalData`。

1. 通过调用添加标准格式`COleDataSource::CacheGlobalData`你想要支持每种标准格式。

MFC OLE 示例程序中使用此技术[HIERSVR](../overview/visual-cpp-samples.md) (检查`OnGetClipboardData`成员函数**CServerItem**类)。 在此示例中唯一的区别是第三步未实现，因为 HIERSVR 不支持任何其他标准格式。

### <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [OLE 数据对象和数据源以及统一数据传输](../mfc/data-objects-and-data-sources-ole.md)

- [OLE 拖放](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>请参阅

[剪贴板：使用 OLE 剪贴板机制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)
