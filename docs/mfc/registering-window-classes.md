---
title: 注册窗口类
ms.date: 11/04/2016
f1_keywords:
- WndProc
helpviewer_keywords:
- window classes [MFC], registering
- registry [MFC], registering classes
- AfxRegisterWndClass method [MFC]
- MFC, windows
- WinMain method [MFC], and registering window classes
- WndProc method [MFC]
- classes [MFC], registering window classes
- WinMain method [MFC]
- registering window classes [MFC]
ms.assetid: 30994bc4-a362-43da-bcc5-1bf67a3fc929
ms.openlocfilehash: c1fc6628b2b5e8e6fa657f4cf99be2256377a5b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540577"
---
# <a name="registering-window-classes"></a>注册窗口类

Windows 传统编程中的窗口“类”定义了可在其中创建任何数量的窗口的“类”（不是 C++ 类）的特征。 此类型的类是一个用于创建窗口的模板或模型。

## <a name="window-class-registration-in-traditional-programs-for-windows"></a>Windows 传统程序中的窗口类注册

对于 Windows，而不使用 MFC 的传统程序中处理所有消息到在其"窗口过程"窗口或"`WndProc`。"一个`WndProc`通过"窗口类注册"过程与窗口相关联。 主窗口在 `WinMain` 函数中注册，但其他窗口类可以在应用程序中的任何位置注册。 注册取决于包含指向指针的结构`WndProc`以及光标、 背景画笔的规范函数等。 作为参数，以及对先前调用中的类的字符串名称传递结构`RegisterClass`函数。 因此，注册类可以由多个窗口共享。

## <a name="window-class-registration-in-mfc-programs"></a>MFC 程序中的窗口类注册

相反，大多数窗口类注册活动会在 MFC 框架程序中自动完成。 如果使用 MFC，则通常使用类继承的常规 C++ 语法从现有库类派生 C++ 窗口类。 框架仍使用传统的“注册类”，并且提供了若干在需要时会为您注册的标准窗口类。 可以通过调用注册其他注册类[AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass)全局函数，然后将传递到注册的类`Create`成员函数的`CWnd`。 正如这里所述，Windows 中的传统“注册类”不会与 C++ 类混淆。

有关详细信息，请参阅[技术说明 1](../mfc/tn001-window-class-registration.md)。

## <a name="see-also"></a>请参阅

[创建窗口](../mfc/creating-windows.md)

