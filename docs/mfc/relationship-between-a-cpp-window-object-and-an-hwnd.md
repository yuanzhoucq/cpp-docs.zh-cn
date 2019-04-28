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
ms.openlocfilehash: 8cf8856be7166768c507932184e257cf69b0eb35
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62309316"
---
# <a name="relationship-between-a-c-window-object-and-an-hwnd"></a>C++ 窗口对象与 HWND 之间的关系

在窗口*对象*是一个对象的C++`CWnd`类 （或派生的类） 的应用程序直接创建。 它出现，并转到应用程序的构造函数和析构函数调用的响应中。 Windows*窗口*后，就是内部 Windows 数据结构，它对应的窗口，并会占用系统资源时存在一个不透明句柄。 Windows 窗口由"窗口句柄"(`HWND`)，并创建后`CWnd`对象创建通过调用`Create`类的成员函数`CWnd`。 通过程序调用或用户的操作，可能会销毁窗口。 窗口对象中存储的窗口句柄*m_hWnd*成员变量。 下图显示了之间的关系C++窗口对象和 Windows 窗口。 在讨论创建 windows[创建 Windows](../mfc/creating-windows.md)。 中介绍了销毁窗口[销毁窗口对象](../mfc/destroying-window-objects.md)。

![CWnd 窗口对象和生成的窗口](../mfc/media/vc37fj1.gif "CWnd 窗口对象和生成的窗口") <br/>
窗口对象和 Windows 窗口

## <a name="see-also"></a>请参阅

[窗口对象](../mfc/window-objects.md)
