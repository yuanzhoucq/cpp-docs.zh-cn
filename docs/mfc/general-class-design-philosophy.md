---
title: 常规类设计理念
ms.date: 11/04/2016
f1_keywords:
- vc.classes.mfc
helpviewer_keywords:
- designing classes [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- classes [MFC], MFC class design
- Windows API [MFC], and MFC
ms.assetid: e6861ae0-1581-4d9c-9ddf-63f9afcdb913
ms.openlocfilehash: f032a4e3dd1dbb5ebed0197e2ee613b948d0b94b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618226"
---
# <a name="general-class-design-philosophy"></a>常规类设计理念

Microsoft Windows 设计很长的时间 c + + 语言被广泛接受。 由于数千个应用程序使用 C 语言 Windows 应用程序编程接口 (API)，该接口将维护可预见的未来。 因此必须基于过程的 C 语言 API 使用任何 c + + Windows 界面。 这可确保 c + + 应用程序将能够与 c 语言应用程序共存。

Microsoft 基础类库是面向对象的接口的 Windows 符合以下设计目标：

- 大大减少了为 Windows 编写应用程序的工作。

- 类似于 C 语言 API 的执行速度。

- 最少的代码大小开销。

- 若要直接调用的任何 Windows C 函数的功能。

- 更容易地转换到 c + + 的现有 c 语言应用程序。

- 能够利用现有基的 C 语言 Windows 编程体验。

- C.使用比 c + + 的 Windows api 更易于使用

- 更轻松地使用而又功能强大的抽象概念变得复杂功能，例如 ActiveX 控件、 数据库支持、 打印、 工具栏和状态栏。

- 用于有效地使用 c + + 语言功能的 c + + 的 Windows API，则返回 true。

有关 MFC 库的设计的详细信息，请参阅：

- [应用程序框架](../mfc/application-framework.md)

- [与 C 语言 API 的关系](../mfc/relationship-to-the-c-language-api.md)

## <a name="see-also"></a>请参阅

[类概述](../mfc/class-library-overview.md)

