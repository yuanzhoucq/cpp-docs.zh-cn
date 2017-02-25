---
title: "如何执行默认打印 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "默认打印"
  - "默认值, 打印"
  - "打印 [MFC], default"
ms.assetid: 0f698459-0fc9-4d43-97da-29cf0f65daa2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 如何执行默认打印
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明 Windows 的MFC框架项中默认打印进程。  
  
 在 MFC 应用程序中，视图类包含所有描述代码名为 `OnDraw` 的成员函数。  `OnDraw` 采用指向 [CDC](../mfc/reference/cdc-class.md) 对象的指针作为参数。  `CDC` 对象用于表示设备上下文接收由 `OnDraw`生成的图像。  当查看文档的窗口收到 [WM\_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) 消息时，框架调用 `OnDraw` 并为该屏幕传递设备上下文 \(特定的 [CPaintDC](../mfc/reference/cpaintdc-class.md) 对象与\)。  因此，`OnDraw` 的输出访问屏幕。  
  
 在为Windows编程中，将输出发送到打印机与发送到屏幕非常相似。  这是因为Windows 图形设备接口 \(GDI\) 是硬件无关。  通过使用合适的设备上下文，你可以使用用于屏幕显示或简单打印的相同 GDI 函数。  如果 `OnDraw` 收到的 `CDC` 对象表示一台打印机，打印机将 `OnDraw` 输出。  
  
 这说明 MFC 应用程序可执行简单的打印，无需执行任何额外的工作。  框架负责显示打印对话框并创建打印机的设备上下文。  当用户选择从文件菜单中打印命令时，打印视图传递此设备上下文到在打印机上绘制文档的`OnDraw`。  
  
 但是，会在打印和显示的屏幕之间有一些重要差异。  在打印时，必须将文档分到不同的页并每次显示一个，而不是在窗口中显示任何可见部分。  作为推导，必须了解文档的范围 \(不论是字母大小、合法大小或信封\)。  可能需要输出不同方向，例如横屏或竖屏。  Microsoft 基础类库不能预测应用程序将如何处理这些问题，因此，它提供其他协议来添加这些功能。  
  
 该协议在文章 [多文档页](../mfc/multipage-documents.md)中描述。  
  
## 请参阅  
 [打印](../mfc/printing.md)