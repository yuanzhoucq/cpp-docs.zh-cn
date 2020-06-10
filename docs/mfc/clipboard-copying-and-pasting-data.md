---
title: 剪贴板：复制和粘贴数据
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard, copying data to
- Clipboard, pasting
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
ms.openlocfilehash: ed3056ec4fb3d3098870a03522d3bf17f41fbe34
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620708"
---
# <a name="clipboard-copying-and-pasting-data"></a>剪贴板：复制和粘贴数据

本主题介绍在 OLE 应用程序中实现从剪贴板进行复制和粘贴所需的最少工作量。 建议在继续操作之前先阅读[数据对象和数据源（OLE）](data-objects-and-data-sources-ole.md)主题。

必须先提供函数来处理 "编辑" 菜单上的 "复制"、"剪切" 和 "粘贴" 选项，然后才能实现复制或粘贴。

## <a name="copying-or-cutting-data"></a><a name="_core_copying_or_cutting_data"></a>复制或剪切数据

#### <a name="to-copy-data-to-the-clipboard"></a>将数据复制到剪贴板

1. 确定要复制的数据是本机数据还是嵌入项或链接的项。

   - 如果数据已嵌入或已链接，则获取指向 `COleClientItem` 已选择的对象的指针。

   - 如果数据是本机数据并且应用程序是服务器，则创建一个从中派生的 `COleServerItem` 包含所选数据的新的对象。 否则， `COleDataSource` 为数据创建一个对象。

1. 调用选定项的 `CopyToClipboard` 成员函数。

1. 如果用户选择了剪切操作而不是复制操作，请从您的应用程序中删除所选数据。

若要查看此序列的示例，请参阅 `OnEditCut` `OnEditCopy` MFC OLE 示例程序[OCLIENT](../overview/visual-cpp-samples.md)和[HIERSVR](../overview/visual-cpp-samples.md)中的和函数。 请注意，这些示例将保留指向当前所选数据的指针，因此，步骤1已完成。

## <a name="pasting-data"></a><a name="_core_pasting_data"></a>粘贴数据

粘贴数据比复制数据更复杂，因为需要选择在将数据粘贴到应用程序中时要使用的格式。

#### <a name="to-paste-data-from-the-clipboard"></a>从剪贴板粘贴数据

1. 在您的视图类中，实现 `OnEditPaste` 以处理用户从 "编辑" 菜单中选择 "粘贴" 选项。

1. 在 `OnEditPaste` 函数中，创建一个 `COleDataObject` 对象并调用其 `AttachClipboard` 成员函数将此对象链接到剪贴板上的数据。

1. 调用 `COleDataObject::IsDataAvailable` 以检查特定格式是否可用。

   或者，您可以使用 `COleDataObject::BeginEnumFormats` 查找其他格式，直到找到最适合您的应用程序的格式。

1. 执行格式的粘贴。

有关其工作原理的示例，请参阅 `OnEditPaste` MFC OLE 示例程序[OCLIENT](../overview/visual-cpp-samples.md)和[HIERSVR](../overview/visual-cpp-samples.md)中定义的视图类中的成员函数的实现。

> [!TIP]
> 将粘贴操作分离到其自身函数中的主要优点是，在拖放操作过程中将数据放置在应用程序中时，可以使用相同的粘贴代码。 与 OCLIENT 和 HIERSVR 一样， `OnDrop` 函数还可以调用 `DoPasteItem` ，并重复使用编写的代码来实现粘贴操作。

若要处理 "编辑" 菜单上的 "选择性粘贴" 选项，请参阅[OLE 中](dialog-boxes-in-ole.md)的主题对话框。

### <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [添加其他格式](clipboard-adding-other-formats.md)

- [OLE 数据对象和数据源以及统一数据传输](data-objects-and-data-sources-ole.md)

- [OLE 拖放](drag-and-drop-ole.md)

- [OLE](ole-background.md)

## <a name="see-also"></a>另请参阅

[剪贴板：使用 OLE 剪贴板机制](clipboard-using-the-ole-clipboard-mechanism.md)
