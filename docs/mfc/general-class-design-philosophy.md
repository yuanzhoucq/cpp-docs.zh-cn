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
ms.openlocfilehash: cfad635c2a826c6f57e2e1513d753a4083494dee
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618785"
---
# <a name="general-class-design-philosophy"></a>常规类设计理念

在 c + + 语言变得很好之前，Microsoft Windows 的设计非常长。 由于成千上万的应用程序使用 C 语言 Windows 应用程序编程接口（API），因此，将在可预见的将来维护此接口。 因此，必须在过程 C 语言 API 之上构建任何 c + + Windows 界面。 这可以保证 c + + 应用程序能够与 C 应用程序共存。

Microsoft 基础类库是一种面向 Windows 的面向对象的接口，可满足以下设计目标：

- 大大减少了编写适用于 Windows 的应用程序的工作量。

- 与 C 语言 API 的执行速度相当。

- 最小代码大小开销。

- 能够直接调用任意 Windows C 函数。

- 更轻松地将现有 C 应用程序转换为 c + +。

- 能够利用现有的 C 语言 Windows 编程体验基础。

- 与 C + + 相比，使用 c + + 来更轻松地使用 Windows API。

- 更易于使用强大的复杂功能抽象，如 ActiveX 控件、数据库支持、打印、工具栏和状态栏。

- 适用于 c + + 的真正的 Windows API，有效地使用 c + + 语言功能。

有关 MFC 库设计的详细信息，请参阅：

- [应用程序框架](application-framework.md)

- [与 C 语言 API 的关系](relationship-to-the-c-language-api.md)

## <a name="see-also"></a>另请参阅

[类概述](class-library-overview.md)
