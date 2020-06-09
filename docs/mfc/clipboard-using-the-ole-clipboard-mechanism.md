---
title: 剪贴板：使用 OLE 剪贴板机制
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], Clipboard
- OLE Clipboard
- Clipboard [MFC], OLE formats
- OLE Clipboard, formats
- formats [MFC], Clipboard for OLE
ms.assetid: 229cc610-5bb1-435e-bd20-2c8b9964d1af
ms.openlocfilehash: da0b99e6c9c803f3c3a4c09d67853649a4bac314
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626048"
---
# <a name="clipboard-using-the-ole-clipboard-mechanism"></a>剪贴板：使用 OLE 剪贴板机制

OLE 使用标准格式和一些 OLE 特定格式通过剪贴板传输数据。

当您在应用程序中剪切或复制数据时，数据将存储在之后将在复制操作中用到的剪贴板上。 此数据有多种格式。 当用户选择粘贴剪贴板中的数据时，应用程序可选择要使用哪种格式。 应用程序应写入才能选择提供最多信息的格式，除非用户使用“选择性粘贴”特地要求特定格式。 在继续之前，您可能需要阅读[数据对象和数据源（OLE）](data-objects-and-data-sources-ole.md)主题。 这些主题介绍了数据传输原理以及如何在应用程序中实现数据传输的基础知识。

Windows 定义了一些可用于通过剪贴板传输数据的标准格式。 这些格式包含元文件、文本、位图和其他。 OLE 也定义了一些 OLE 特定格式。 对于这些标准格式所提供的详细信息不能满足其需求的应用程序，最好注册其自己的自定义剪贴板格式。 使用 Win32 API 函数[RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)执行此操作。

例如，Microsoft Excel 将为电子表格注册一种自定义格式。 此格式传递的信息比位图（例如）传递的多。 将此数据粘贴到支持电子表格格式的应用程序中后，电子表格中的所有公式和值保持不变并且可进行更新（如有必要）。 Microsoft Excel 还会将带有格式的数据放置在剪贴板上，以便可将其作为 OLE 项粘贴。 任何 OLE 文档容器均可将此信息作为嵌入项目粘贴。 此嵌入项目可使用 Microsoft Excel 进行更改。 剪贴板还包含电子表格上选定范围的图像的简单位图。 此位图还可粘贴到 OLE 文档容器或位图编辑器（如 Paint）中。 但在位图中，无法像电子表格一样操作数据。

若要从剪贴板检索最大量的信息，应用程序应在粘贴剪贴板中的数据前检查这些自定义格式。

例如，若要启用“剪切”命令，您可编写与下类似的处理程序：

[!code-cpp[NVC_MFCListView#3](../atl/reference/codesnippet/cpp/clipboard-using-the-ole-clipboard-mechanism_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [复制和粘贴数据](clipboard-copying-and-pasting-data.md)

- [添加其他格式](clipboard-adding-other-formats.md)

- [使用 Windows 剪贴板](clipboard-using-the-windows-clipboard.md)

- [OLE](ole-background.md)

- [OLE 数据对象和数据源以及统一数据传输](data-objects-and-data-sources-ole.md)

## <a name="see-also"></a>另请参阅

[剪贴板](clipboard.md)
