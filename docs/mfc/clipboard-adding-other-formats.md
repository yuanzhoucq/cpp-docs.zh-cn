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
ms.openlocfilehash: 52089364a6be423c69a7031cd0d99e1924de1444
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626065"
---
# <a name="clipboard-adding-other-formats"></a>剪贴板：添加其他格式

本主题说明如何扩展受支持格式的列表，特别是对于 OLE 支持。 主题[剪贴板：复制和粘贴数据](clipboard-copying-and-pasting-data.md)介绍支持从剪贴板复制和粘贴所需的最小实现。 如果这是你要实现的所有格式，则剪贴板上的唯一格式**CF_METAFILEPICT**、 **CF_EMBEDSOURCE**、 **CF_OBJECTDESCRIPTOR**，可能**CF_LINKSOURCE**。 大多数应用程序在剪贴板上所需的格式与这三个不同。

## <a name="registering-custom-formats"></a><a name="_core_registering_custom_formats"></a>注册自定义格式

若要创建自己的自定义格式，请执行注册任何自定义剪贴板格式时使用的相同过程：将格式名称传递给**RegisterClipboardFormat**函数，并使用其返回值作为格式 ID。

## <a name="placing-formats-on-the-clipboard"></a><a name="_core_placing_formats_on_the_clipboard"></a>在剪贴板上放置格式

若要在剪贴板上添加更多格式，必须重写 `OnGetClipboardData` 从或派生的类中的函数 `COleClientItem` `COleServerItem` （取决于要复制的数据是否为本机数据）。 在此函数中，应使用以下过程。

#### <a name="to-place-formats-on-the-clipboard"></a>在剪贴板上设置格式

1. 创建 `COleDataSource` 对象。

1. 将此数据源传递到一个函数，该函数通过调用将本机数据格式添加到支持的格式列表中 `COleDataSource::CacheGlobalData` 。

1. 通过 `COleDataSource::CacheGlobalData` 为要支持的每种标准格式调用来添加标准格式。

此方法用于 MFC OLE 示例程序[HIERSVR](../overview/visual-cpp-samples.md) （检查 `OnGetClipboardData` **CServerItem**类的成员函数）。 此示例的唯一区别在于，步骤3未实现，因为 HIERSVR 不支持其他标准格式。

### <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [OLE 数据对象和数据源以及统一数据传输](data-objects-and-data-sources-ole.md)

- [OLE 拖放](drag-and-drop-ole.md)

- [OLE](ole-background.md)

## <a name="see-also"></a>另请参阅

[剪贴板：使用 OLE 剪贴板机制](clipboard-using-the-ole-clipboard-mechanism.md)
