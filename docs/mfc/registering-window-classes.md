---
title: 注册窗口类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- WndProc
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 00e397f8880f6f42f1930e668b64d3ba62eb2c64
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379736"
---
# <a name="registering-window-classes"></a>注册窗口类
Windows 传统编程中的窗口“类”定义了可在其中创建任何数量的窗口的“类”（不是 C++ 类）的特征。 此类型的类是一个用于创建窗口的模板或模型。  
  
## <a name="window-class-registration-in-traditional-programs-for-windows"></a>Windows 传统程序中的窗口类注册  
 适用于 Windows，无需 MFC 的传统程序中，你处理所有消息在其"窗口过程"窗口或"**WndProc**。" A **WndProc**与通过"窗口类注册"过程窗口相关联。 主窗口在 `WinMain` 函数中注册，但其他窗口类可以在应用程序中的任何位置注册。 注册取决于包含指向的指针的结构**WndProc**以及光标、 背景画笔的规范函数和等等。 作为参数，以及中调用的类的字符串名称传递结构**RegisterClass**函数。 因此，注册类可以由多个窗口共享。  
  
## <a name="window-class-registration-in-mfc-programs"></a>MFC 程序中的窗口类注册  
 相反，大多数窗口类注册活动会在 MFC 框架程序中自动完成。 如果使用 MFC，则通常使用类继承的常规 C++ 语法从现有库类派生 C++ 窗口类。 框架仍使用传统的“注册类”，并且提供了若干在需要时会为您注册的标准窗口类。 你可以通过调用注册附加的登记类[AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass)全局函数，然后将已注册的类**创建**成员函数`CWnd`。 正如这里所述，Windows 中的传统“注册类”不会与 C++ 类混淆。  
  
 有关详细信息，请参阅[技术说明 1](../mfc/tn001-window-class-registration.md)。  
  
## <a name="see-also"></a>请参阅  
 [创建窗口](../mfc/creating-windows.md)

