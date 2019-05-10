---
title: 剪贴板：何时使用每一剪贴板机制
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], Clipboard
- OLE Clipboard, guidelines
- Clipboard [MFC], mechanisms
- OLE Clipboard, formats
- formats [MFC], Clipboard for OLE
- Clipboard [MFC], formats
ms.assetid: fd071996-ef8c-488b-81bd-89057095a201
ms.openlocfilehash: f92a9a29da7f417d5ea5860c18e6ae1d9b20a05e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327042"
---
# <a name="clipboard-when-to-use-each-clipboard-mechanism"></a>剪贴板：何时使用每一剪贴板机制

请遵循以下准则中使用剪贴板：

- 使用 OLE 剪贴板机制现在在将来启用新功能。 而将维护标准的剪贴板 API，OLE 机制是未来的数据传输。

- 如果你正在编写 OLE 应用程序或您希望的任何 OLE 功能，如拖放，请使用 OLE 剪贴板机制。

- 如果你要提供 OLE 格式，请使用 OLE 剪贴板机制。

## <a name="what-do-you-want-to-do"></a>你想要做什么

- [使用 OLE 剪贴板机制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

- [使用 Windows 剪贴板机制](../mfc/clipboard-using-the-windows-clipboard.md)

## <a name="see-also"></a>请参阅

[剪贴板](../mfc/clipboard.md)
