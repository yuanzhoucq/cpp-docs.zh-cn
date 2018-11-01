---
title: TN070：MFC 窗口类名称
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.classes
helpviewer_keywords:
- window class names [MFC]
- TN070 [MFC]
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
ms.openlocfilehash: d59dc052cc253c8d036de0559018065e4ba7457d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533609"
---
# <a name="tn070-mfc-window-class-names"></a>TN070：MFC 窗口类名称

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

MFC 窗口使用可反映窗口功能的动态创建的类名。 MFC 动态生成框架窗口、视图以及由应用程序生成的弹出式窗口的类名。 MFC 应用程序生成的对话框和控件具有上述窗口类的 Windows 提供的类名。

可以通过注册您自己的窗口类并使用它的重写中替换动态提供的类名[PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow)。 其 MFC 提供的类名适合下列两种形式之一：

```
Afx:%x:%x
Afx:%x:%x:%x:%x:%x
```

替换为十六进制数字`%x`字符中的从的数据填充[WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576)结构。 MFC 使用此方法，以便需要相同的多个 c + + 类**WNDCLASS**结构可以共享相同的已注册的窗口类。 在大多数简单的 Win32 应用程序，MFC 应用程序只能有一个**WNDPROC**，因此可以轻松地共享**WNDCLASS**结构以节省时间和内存。 上面显示的 `%x` 字符的可替换值如下所示：

- **WNDCLASS.hInstance**

- **WNDCLASS.style**

- **WNDCLASS.hCursor**

- **WNDCLASS.hbrBackground**

- **WNDCLASS.hIcon**

第一种形式 (`Afx:%x:%x`) 时使用**hCursor**， **hbrBackground**，并且**hIcon**同时**NULL**。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)<br/>
[TN020：ID 命名和编号约定](../mfc/tn020-id-naming-and-numbering-conventions.md)

