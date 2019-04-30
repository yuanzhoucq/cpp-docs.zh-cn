---
title: 销毁框架窗口
ms.date: 11/04/2016
f1_keywords:
- PostNcDestroy
helpviewer_keywords:
- Default method [MFC]
- DestroyWindow method [MFC]
- frame windows [MFC], destroying
- OnNcDestroy method, and frame windows
- document frame windows [MFC], destroying
- destroying frame windows
- MFC, frame windows
- windows [MFC], destroying
- OnClose method [MFC]
- PostNcDestroy method [MFC]
ms.assetid: 5affca77-1999-4507-a2b2-9aa226611b4b
ms.openlocfilehash: b64298bd2b0f14c30c824d78947a17628adec8b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394632"
---
# <a name="destroying-frame-windows"></a>销毁框架窗口

MFC 框架管理窗口析构，以及与 framework 文档和视图相关联的窗口的创建。 如果您创建其他窗口，您有责任销毁它们。

在 framework 中，当用户关闭帧窗口时，窗口的默认[OnClose](../mfc/reference/cwnd-class.md#onclose)处理程序调用[DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow)。 当销毁 Windows 窗口时调用的最后一个成员函数是[OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy)，其中进行一些清理，调用[默认](../mfc/reference/cwnd-class.md#default)成员函数来执行 Windows 清理，最后调用虚拟成员函数[PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy)。 [CFrameWnd](../mfc/reference/cframewnd-class.md)的实现`PostNcDestroy`删除C++窗口对象。 你决不应使用C++**删除**框架窗口上的运算符。 请改用 `DestroyWindow`。

当主窗口关闭时，应用程序关闭。 如果那里修改的未保存的文档，框架将显示一个消息框，询问是否应保存文档，并可确保根据需要保存相应文档。

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [创建文档框架窗口](../mfc/creating-document-frame-windows.md)

## <a name="see-also"></a>请参阅

[使用框架窗口](../mfc/using-frame-windows.md)
