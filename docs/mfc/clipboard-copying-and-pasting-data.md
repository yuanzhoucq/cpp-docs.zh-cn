---
title: 剪贴板：复制和粘贴数据
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard, copying data to
- Clipboard, pasting
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
ms.openlocfilehash: 74348dd3e790cceada9aafd718464694997316ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374571"
---
# <a name="clipboard-copying-and-pasting-data"></a>剪贴板：复制和粘贴数据

本主题介绍在 OLE 应用程序中实现复制和粘贴从剪贴板所需的最小工作。 建议您在继续操作之前阅读["数据对象和数据源 （OLE）"](../mfc/data-objects-and-data-sources-ole.md)主题。

在可以实现复制或粘贴之前，必须首先提供函数来处理"编辑"菜单上的"复制"、"剪切"和"粘贴"选项。

## <a name="copying-or-cutting-data"></a><a name="_core_copying_or_cutting_data"></a>复制或切割数据

#### <a name="to-copy-data-to-the-clipboard"></a>将数据复制到剪贴板

1. 确定要复制的数据是本机数据还是嵌入或链接项。

   - 如果数据是嵌入或链接的，请获取指向已选择`COleClientItem`对象的指针。

   - 如果数据是本机数据，并且应用程序是服务器，请创建一个从`COleServerItem`包含所选数据派生的新对象。 否则，为数据`COleDataSource`创建对象。

1. 调用所选项的成员`CopyToClipboard`函数。

1. 如果用户选择了"剪切"操作而不是"复制"操作，请从应用程序中删除所选数据。

要查看此序列的示例，请参阅 MFC `OnEditCut` OLE`OnEditCopy`示例程序[OCLIENT](../overview/visual-cpp-samples.md)和[HIERSVR](../overview/visual-cpp-samples.md)中的 和 函数。 请注意，这些示例维护指向当前选定数据的指针，因此步骤 1 已完成。

## <a name="pasting-data"></a><a name="_core_pasting_data"></a>粘贴数据

粘贴数据比复制数据要复杂得多，因为您需要选择要在将数据粘贴到应用程序中的格式。

#### <a name="to-paste-data-from-the-clipboard"></a>粘贴剪贴板中的数据

1. 在视图类中，实现`OnEditPaste`处理用户从"编辑"菜单中选择"粘贴"选项。

1. 在`OnEditPaste`函数中，创建`COleDataObject`一个对象并`AttachClipboard`调用其成员函数以将此对象链接到剪贴板上的数据。

1. 调用`COleDataObject::IsDataAvailable`以检查特定格式是否可用。

   或者，您可以使用`COleDataObject::BeginEnumFormats`查找其他格式，直到找到最适合您的应用程序。

1. 执行格式的粘贴。

有关其工作原理的示例，请参阅 MFC OLE 示例`OnEditPaste`程序[OCLIENT](../overview/visual-cpp-samples.md)和[HIERSVR](../overview/visual-cpp-samples.md)中定义的视图类中成员函数的实现。

> [!TIP]
> 将粘贴操作分离到其自己的函数的主要好处是，在拖放操作期间，当数据在应用程序中丢弃时，可以使用相同的粘贴代码。 与 OCLIENT 和 HIERSVR`OnDrop`中一样`DoPasteItem`，函数还可以调用 ，重用编写的代码来实现粘贴操作。

要处理"编辑"菜单上的"粘贴特殊"选项，请参阅[OLE 中的主题对话框](../mfc/dialog-boxes-in-ole.md)。

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [添加其他格式](../mfc/clipboard-adding-other-formats.md)

- [OLE 数据对象和数据源以及统一数据传输](../mfc/data-objects-and-data-sources-ole.md)

- [OLE 拖放](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>另请参阅

[剪贴板：使用 OLE 剪贴板机制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)
