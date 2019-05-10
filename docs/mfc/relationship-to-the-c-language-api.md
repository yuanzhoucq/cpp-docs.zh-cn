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
ms.openlocfilehash: fe83af2d05af8e3b9da8d0c62f6974b0a5410bfc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308974"
---
# <a name="relationship-to-the-c-language-api"></a>与 C 语言 API 的关系

将 Microsoft 基础类 (MFC) 库与其他 Windows 类库区分开的一个特性是，它几乎完全映射到用 C 语言编写的 Windows API。 此外，您通常可以随意地将对该类库的调用与对 Windows API 的直接调用混合在一起。 但是，这种直接访问并不意味着这些类可以完全替代相应的 API。 开发人员必须偶尔仍然会直接对进行调用某些 Windows 功能，如[SetCursor](/windows/desktop/api/winuser/nf-winuser-setcursor)并[GetSystemMetrics](/windows/desktop/api/winuser/nf-winuser-getsystemmetrics)，例如。 一个类成员函数可以包装一个 Windows 函数（前提是这样做具有明显优点）。

由于您有时需要进行本机 Windows 函数调用，因此您应该具有访问 C 语言 Windows API 文档的权限。 此文档随 Microsoft Visual C++ 一起提供。

> [!NOTE]
>  MFC 库框架的运行方式的概述，请参阅[使用为 Windows 编写应用程序类](../mfc/using-the-classes-to-write-applications-for-windows.md)。

## <a name="see-also"></a>请参阅

[常规类设计理念](../mfc/general-class-design-philosophy.md)
