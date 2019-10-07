---
title: 与 C 语言 API 的关系
ms.date: 11/04/2016
f1_keywords:
- vc.classes.mfc
helpviewer_keywords:
- books [MFC], about MFC and Windows SDK
- books [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- Windows API [MFC], and MFC
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
ms.openlocfilehash: 8601dd034dbd73ac035084ad57c51f62e333fd32
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511865"
---
# <a name="relationship-to-the-c-language-api"></a>与 C 语言 API 的关系

将 Microsoft 基础类 (MFC) 库与其他 Windows 类库区分开的一个特性是，它几乎完全映射到用 C 语言编写的 Windows API。 此外，您通常可以随意地将对该类库的调用与对 Windows API 的直接调用混合在一起。 但是，这种直接访问并不意味着这些类可以完全替代相应的 API。 例如, 开发人员还必须偶尔对某些 Windows 函数 (如[SetCursor](/windows/win32/api/winuser/nf-winuser-setcursor)和[GetSystemMetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics)) 进行直接调用。 一个类成员函数可以包装一个 Windows 函数（前提是这样做具有明显优点）。

由于您有时需要进行本机 Windows 函数调用，因此您应该具有访问 C 语言 Windows API 文档的权限。 此文档随 Microsoft Visual C++ 一起提供。

> [!NOTE]
>  有关 MFC 库框架如何操作的概述, 请参阅[使用类编写适用于 Windows 的应用程序](../mfc/using-the-classes-to-write-applications-for-windows.md)。

## <a name="see-also"></a>请参阅

[常规类设计理念](../mfc/general-class-design-philosophy.md)
