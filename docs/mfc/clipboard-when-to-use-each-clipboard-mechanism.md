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
ms.openlocfilehash: 88fef4b9c0cf37bb475e460c212765b17d4eb634
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626007"
---
# <a name="clipboard-when-to-use-each-clipboard-mechanism"></a>剪贴板：何时使用每一剪贴板机制

使用剪贴板时，请遵循以下准则：

- 现在使用 OLE 剪贴板机制实现新功能。 虽然将保留标准剪贴板 API，但 OLE 机制是数据传输的未来。

- 如果要编写 OLE 应用程序或需要任何 OLE 功能，如拖放，请使用 OLE 剪贴板机制。

- 如果提供 OLE 格式，则使用 OLE 剪贴板机制。

## <a name="what-do-you-want-to-do"></a>要执行的操作

- [使用 OLE 剪贴板机制](clipboard-using-the-ole-clipboard-mechanism.md)

- [使用 Windows 剪贴板机制](clipboard-using-the-windows-clipboard.md)

## <a name="see-also"></a>另请参阅

[剪贴板](clipboard.md)
