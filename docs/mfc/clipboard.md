---
title: 剪贴板
ms.date: 11/04/2016
helpviewer_keywords:
- cutting and copying data
- copying data
- Clipboard
- Clipboard, programming
- transferring data
ms.assetid: a71b2824-1f14-4914-8816-54578d73ad4e
ms.openlocfilehash: 5f4a17bedaa50913dce1f6388dfb6b8d9ecd38da
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617278"
---
# <a name="clipboard"></a>剪贴板

本系列文章介绍如何在 MFC 应用程序中实现对 Windows 剪贴板的支持。 通过两种方式使用 Windows 剪贴板：

- 实现标准编辑菜单命令，如剪切、复制和粘贴。

- 通过 OLE 拖放实现统一的数据传输。

剪贴板是在源和目标之间传输数据的标准 Windows 方法。 它在 OLE 操作中也非常有用。 随着 OLE 的出现，Windows 中有两个剪贴板机制。 标准 Windows 剪贴板 API 仍可用，但已通过 OLE 数据传输机制补充。 OLE 统一数据传输（UDT）支持剪切、复制和粘贴剪贴板，并拖放。

剪贴板是整个 Windows 会话共享的系统服务，因此它没有自己的句柄或类。 通过[CWnd](reference/cwnd-class.md)类的成员函数管理剪贴板。

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [何时使用每个剪贴板机制](clipboard-when-to-use-each-clipboard-mechanism.md)

- [使用传统的 Windows 剪贴板 API](clipboard-using-the-windows-clipboard.md)

- [使用 OLE 剪贴板机制](clipboard-using-the-ole-clipboard-mechanism.md)

- [复制和粘贴数据](clipboard-copying-and-pasting-data.md)

- [添加其他格式](clipboard-adding-other-formats.md)

- [Windows 剪贴板](/windows/win32/dataxchg/clipboard)

- [OLE 拖放](drag-and-drop-ole.md)

## <a name="see-also"></a>另请参阅

[用户界面元素](user-interface-elements-mfc.md)
