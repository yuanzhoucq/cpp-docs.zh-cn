---
title: "常规类设计理念 |Microsoft 文档"
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
- designing classes [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- classes [MFC], MFC class design
- Windows API [MFC], and MFC
ms.assetid: e6861ae0-1581-4d9c-9ddf-63f9afcdb913
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c174b06b27e78ca61d2608b8e04205068ac436e9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="general-class-design-philosophy"></a>常规类设计理念
Microsoft Windows 旨在长时间之前的 c + + 语言被广泛接受。 因为数千个应用程序使用 C 语言 Windows 应用程序编程接口 (API)，该接口将保持为可预见未来中。 因此必须基于过程的 C 语言 API 使用任何 c + + Windows 界面。 这可保证 c + + 应用程序将能够与 C 应用程序共存。  
  
 Microsoft 基础类库是满足以下的设计目标的 Windows 的面向对象的接口：  
  
-   为 Windows 编写应用程序的工作量，大大减少。  
  
-   C 语言 API 相媲美的执行速度。  
  
-   最小代码大小开销。  
  
-   能够直接调用的任何 Windows C 函数。  
  
-   现有的 C 应用程序与 c + + 的简单地转换。  
  
-   能够利用中的现有基本的 C 语言 Windows 编程体验。  
  
-   使用与 C.比 c + + 的 Windows api 的更易于使用  
  
-   更轻松地使用但功能强大的抽象复杂 ActiveX 控件、 数据库支持、 打印、 工具栏和状态栏等功能。  
  
-   True 有效地使用 c + + 语言功能的 c + + 的 Windows API。  
  
 有关 MFC 库的设计的详细信息，请参阅：  
  
-   [应用程序框架](../mfc/application-framework.md)  
  
-   [与 C 语言 API 的关系](../mfc/relationship-to-the-c-language-api.md)  
  
## <a name="see-also"></a>请参阅  
 [类概述](../mfc/class-library-overview.md)

