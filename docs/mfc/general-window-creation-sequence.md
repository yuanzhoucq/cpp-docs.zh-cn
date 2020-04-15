---
title: 常用窗口创建序列
ms.date: 11/04/2016
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
ms.openlocfilehash: fb10ced78e230316a6e2982f24c1fb6e2e52ed8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364271"
---
# <a name="general-window-creation-sequence"></a>常用窗口创建序列

当您创建自己的窗口（如子窗口）时，框架使用的过程与[文档/视图创建](../mfc/document-view-creation.md)中所述的过程大致相同。

MFC提供的所有窗口类采用[两阶段结构](../mfc/one-stage-and-two-stage-construction-of-objects.md)。 也就是说，在调用C++**新**运算符期间，构造函数分配并初始化C++对象，但不会创建相应的 Windows 窗口。 之后，通过调用窗口对象的["创建](../mfc/reference/cwnd-class.md#create)成员"函数来完成此操作。

成员`Create`函数使 Windows 窗口并将其`HWND`存储在C++对象的公共数据成员[m_hWnd](../mfc/reference/cwnd-class.md#m_hwnd)。 `Create`对创建参数具有完全的灵活性。 在调用`Create`之前，您可能希望使用全局函数[AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass)注册窗口类，以便为框架设置图标和类样式。

对于框架窗口，可以使用[LoadFrame](../mfc/reference/cframewnd-class.md#loadframe)成员函数而不是`Create`。 `LoadFrame`使用较少的参数使 Windows 窗口。 它从资源获取许多默认值，包括框架的标题、图标、快捷键表和菜单。

> [!NOTE]
> 您的图标、快捷键表和菜单资源必须具有通用资源 ID（如**IDR_MAINFRAME，** 以便由 LoadFrame 加载它们。

## <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [窗口对象](../mfc/window-objects.md)

- [注册窗口"类"](../mfc/registering-window-classes.md)

- [销毁窗口对象](../mfc/destroying-window-objects.md)

- [创建文档框架窗口](../mfc/creating-document-frame-windows.md)

## <a name="see-also"></a>另请参阅

[创建窗口](../mfc/creating-windows.md)
