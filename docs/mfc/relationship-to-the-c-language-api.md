---
title: "与 C 语言 API 的关系 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.mfc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "书籍 [C++]"
  - "书籍 [C++], 关于 MFC 和 Windows SDK"
  - "MFC [C++], Windows API"
  - "Visual C, Windows API 调用"
  - "Windows API [C++], 和 MFC"
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 与 C 语言 API 的关系
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将 Microsoft 基础类 \(MFC\) \(MFC\) 库不同窗口的类库外的唯一特性非常接近映射到 C 语言编写的 Windows API。  此外，您可以自由通常组合调用类库与直接调用到 Windows API。  该直接访问不会，然而，意味着类是完全替代的API。  开发人员还必须偶尔直接调用一些Windows功能，如 [SetCursor](http://msdn.microsoft.com/library/windows/desktop/ms648393) 和[GetSystemMetrics](http://msdn.microsoft.com/library/windows/desktop/ms724385)。  一个Windows的功能是由一个类的成员函数包裹时，才会有明显的优势来这样做。  
  
 因为你有时需要进行本机Windows函数调用，你应该可以访问C语言的Windows API文档。  此文档包含 Microsoft Visual C\+\+。  
  
> [!NOTE]
>  有关如何在MFC库运行框架的概述，请参见[使用类编写 Windows 应用程序](../mfc/using-the-classes-to-write-applications-for-windows.md)。  
  
## 请参阅  
 [常规类设计理念](../mfc/general-class-design-philosophy.md)