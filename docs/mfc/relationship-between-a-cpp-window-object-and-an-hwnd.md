---
title: C++ 窗口对象与 HWND 之间的关系
ms.date: 11/19/2018
f1_keywords:
- HWND
helpviewer_keywords:
- Windows window [MFC]
- window objects [MFC], HWND and
- HWND [MFC]
- CWnd class [MFC], HWND
- HWND, window objects [MFC]
ms.assetid: f2e76340-6691-4ee6-9424-0345634a9469
ms.openlocfilehash: fcd885fbaf7e81d68bcd51edc4b74c553f70578b
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176852"
---
# <a name="relationship-between-a-c-window-object-and-an-hwnd"></a>C++ 窗口对象与 HWND 之间的关系

在窗口*对象*是一个对象的 c + +`CWnd`类 （或派生的类） 的应用程序直接创建。 它出现，并转到应用程序的构造函数和析构函数调用的响应中。 Windows*窗口*后，就是内部 Windows 数据结构，它对应的窗口，并会占用系统资源时存在一个不透明句柄。 Windows 窗口由"窗口句柄"(`HWND`)，并创建后`CWnd`对象创建通过调用`Create`类的成员函数`CWnd`。 通过程序调用或用户的操作，可能会销毁窗口。 窗口对象中存储的窗口句柄*m_hWnd*成员变量。 下图显示了 c + + 窗口对象与 Windows 窗口之间的关系。 在讨论创建 windows[创建 Windows](../mfc/creating-windows.md)。 中介绍了销毁窗口[销毁窗口对象](../mfc/destroying-window-objects.md)。

![CWnd 窗口对象和生成的窗口](../mfc/media/vc37fj1.gif "CWnd 窗口对象和生成的窗口") <br/>
窗口对象和 Windows 窗口

## <a name="see-also"></a>请参阅

[窗口对象](../mfc/window-objects.md)
