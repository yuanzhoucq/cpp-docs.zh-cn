---
title: 常规类设计理念
ms.date: 11/04/2016
helpviewer_keywords:
- designing classes [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- classes [MFC], MFC class design
- Windows API [MFC], and MFC
ms.assetid: e6861ae0-1581-4d9c-9ddf-63f9afcdb913
ms.openlocfilehash: 34a173802e3fa43615c05da4ce747592f851228f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441186"
---
# <a name="general-class-design-philosophy"></a>常规类设计理念

在语言变得很好之前C++ ，Microsoft Windows 的设计非常长。 由于成千上万的应用程序使用 C 语言 Windows 应用程序编程接口（API），因此，将在可预见的将来维护此接口。 因此C++ ，必须在过程 C 语言 API 之上构建任何 Windows 界面。 这可确保C++应用程序能够与 C 应用程序共存。

Microsoft 基础类库是一种面向 Windows 的面向对象的接口，可满足以下设计目标：

- 大大减少了编写适用于 Windows 的应用程序的工作量。

- 与 C 语言 API 的执行速度相当。

- 最小代码大小开销。

- 能够直接调用任意 Windows C 函数。

- 更轻松地将现有 C 应用C++程序转换为。

- 能够利用现有的 C 语言 Windows 编程体验基础。

- 使用C++比 with C 更简单的 Windows API。

- 更易于使用强大的复杂功能抽象，如 ActiveX 控件、数据库支持、打印、工具栏和状态栏。

- 的真正的 Windows C++ API，用于C++有效地使用语言功能。

有关 MFC 库设计的详细信息，请参阅：

- [应用程序框架](../mfc/application-framework.md)

- [与 C 语言 API 的关系](../mfc/relationship-to-the-c-language-api.md)

## <a name="see-also"></a>另请参阅

[类概述](../mfc/class-library-overview.md)
