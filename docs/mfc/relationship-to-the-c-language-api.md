---
title: "与 C 语言 API 的关系 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.mfc
dev_langs: C++
helpviewer_keywords:
- books [MFC], about MFC and Windows SDK
- books [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- Windows API [MFC], and MFC
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 26458242ab6afcf69d6e70065ba70e31f0adbe74
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="relationship-to-the-c-language-api"></a>与 C 语言 API 的关系
将 Microsoft 基础类 (MFC) 库与其他 Windows 类库区分开的一个特性是，它几乎完全映射到用 C 语言编写的 Windows API。 此外，您通常可以随意地将对该类库的调用与对 Windows API 的直接调用混合在一起。 但是，这种直接访问并不意味着这些类可以完全替代相应的 API。 开发人员仍有时必须进行直接调用对某些 Windows 函数，如[SetCursor](http://msdn.microsoft.com/library/windows/desktop/ms648393)和[GetSystemMetrics](http://msdn.microsoft.com/library/windows/desktop/ms724385)，例如。 一个类成员函数可以包装一个 Windows 函数（前提是这样做具有明显优点）。  
  
 由于您有时需要进行本机 Windows 函数调用，因此您应该具有访问 C 语言 Windows API 文档的权限。 此文档随 Microsoft Visual C++ 一起提供。  
  
> [!NOTE]
>  MFC 库框架的工作方式的概述，请参阅[使用类编写 Windows 应用程序到](../mfc/using-the-classes-to-write-applications-for-windows.md)。  
  
## <a name="see-also"></a>请参阅  
 [常规类设计理念](../mfc/general-class-design-philosophy.md)
