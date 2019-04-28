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
ms.openlocfilehash: 4dfa11c73703f5f2d3d17f8278610d32178af679
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219614"
---
# <a name="general-class-design-philosophy"></a>常规类设计理念

Microsoft Windows 多长时间之后设计C++语言被广泛接受。 由于数千个应用程序使用 C 语言 Windows 应用程序编程接口 (API)，该接口将维护可预见的未来。 任何C++Windows 界面因此必须基于过程的 C 语言 API。 这可保证C++应用程序将能够与 c 语言应用程序共存。

Microsoft 基础类库是面向对象的接口的 Windows 符合以下设计目标：

- 大大减少了为 Windows 编写应用程序的工作。

- 类似于 C 语言 API 的执行速度。

- 最少的代码大小开销。

- 若要直接调用的任何 Windows C 函数的功能。

- 更容易地转换到现有的 C 应用程序C++。

- 能够利用现有基的 C 语言 Windows 编程体验。

- 更轻松地使用 Windows APIC++比使用 c。

- 更轻松地使用而又功能强大的抽象概念变得复杂功能，例如 ActiveX 控件、 数据库支持、 打印、 工具栏和状态栏。

- True 为 Windows API C++ ，它有效地使用C++语言功能。

有关 MFC 库的设计的详细信息，请参阅：

- [应用程序框架](../mfc/application-framework.md)

- [与 C 语言 API 的关系](../mfc/relationship-to-the-c-language-api.md)

## <a name="see-also"></a>请参阅

[类概述](../mfc/class-library-overview.md)
