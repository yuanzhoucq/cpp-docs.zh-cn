---
title: 剪贴板： 复制和粘贴数据 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Clipboard, copying data to
- Clipboard, pasting
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f4a3ba23fbf6e9465d78b04fcd79758c7cae525
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060221"
---
# <a name="clipboard-copying-and-pasting-data"></a>剪贴板：复制和粘贴数据

本主题描述了实现到复制和粘贴剪贴板中 OLE 应用程序所需的最小工作。 建议您阅读[数据对象和数据源 (OLE)](../mfc/data-objects-and-data-sources-ole.md)继续操作之前的主题。

实现复制或粘贴之前，必须首先提供函数来处理在编辑菜单上的复制、 剪切和粘贴选项。

##  <a name="_core_copying_or_cutting_data"></a> 复制或剪切数据

#### <a name="to-copy-data-to-the-clipboard"></a>若要将数据复制到剪贴板

1. 确定要复制的数据是本机数据还是嵌入或链接项。

   - 如果数据是嵌入或链接，获取一个指向`COleClientItem`已选择的对象。

   - 如果数据是本机应用程序是一个服务器，创建一个新的对象派生自`COleServerItem`包含所选的数据。 否则，创建`COleDataSource`对象的数据。

1. 调用选定的项的`CopyToClipboard`成员函数。

1. 如果用户选择剪切操作而不是复制操作，从你的应用程序中删除所选的数据。

若要查看此序列的示例，请参阅`OnEditCut`并`OnEditCopy`函数在 MFC OLE 示例程序[OCLIENT](../visual-cpp-samples.md)并[HIERSVR](../visual-cpp-samples.md)。 请注意，这些示例维护一个指向当前所选的数据，以使其步骤 1 已完成。

##  <a name="_core_pasting_data"></a> 粘贴数据

粘贴数据会比将其复制，因为你需要选择要在将数据粘贴到你的应用程序中使用的格式更复杂。

#### <a name="to-paste-data-from-the-clipboard"></a>若要将数据从剪贴板粘贴

1. 在视图类中，实现`OnEditPaste`来处理用户从编辑菜单中选择粘贴选项。

1. 在中`OnEditPaste`函数中，创建`COleDataObject`对象，并调用其`AttachClipboard`成员函数以将此对象链接到剪贴板中的数据。

1. 调用`COleDataObject::IsDataAvailable`若要检查特定的格式是否可用。

   或者，可以使用`COleDataObject::BeginEnumFormats`寻找其他格式，直到找到最适合你的应用程序。

1. 执行格式粘贴。

此工作原理的示例，请参阅的实现`OnEditPaste`MFC OLE 示例程序中定义的视图类中的成员函数[OCLIENT](../visual-cpp-samples.md)并[HIERSVR](../visual-cpp-samples.md)。

> [!TIP]
>  分离到其自身函数粘贴操作的主要优点是拖放操作期间在应用程序中删除数据时，可以使用相同的粘贴代码。 如 OCLIENT 和 HIERSVR，你`OnDrop`函数也可以调用`DoPasteItem`，重复使用编写实现粘贴操作的代码。

若要处理编辑菜单上的选择性粘贴选项，请参阅主题[OLE 中的对话框](../mfc/dialog-boxes-in-ole.md)。

### <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [添加其他格式](../mfc/clipboard-adding-other-formats.md)

- [OLE 数据对象和数据源以及统一数据传输](../mfc/data-objects-and-data-sources-ole.md)

- [OLE 拖放](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>请参阅

[剪贴板：使用 OLE 剪贴板机制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

