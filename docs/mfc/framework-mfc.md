---
title: "框架 (MFC) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- encapsulation [MFC], Win32 API
- MFC, application framework
- wrapper classes [MFC], explained
- Win32 [MFC], API encapsulation by MFC
- application framework [MFC], about MFC application framework
- APIs [MFC], encapsulation by MFC Win32
- encapsulation [MFC]
- Windows API [MFC], encapsulation by MFC
- encapsulated Win32 API [MFC]
ms.assetid: 3be0fec8-9843-4119-ae42-ece993ef500b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c021b11809b3e6598e694fdaa46b7f829358e24f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="framework-mfc"></a>框架 (MFC)
在使用 Microsoft 基础类 (MFC) 库框架时很大程度上基于几个主要的类和 Visual C++ 工具。 一些类封装了 Win32 应用程序编程接口 (API) 的一大部分。 其他类封装了应用程序概念，如文档、视图和应用程序本身。 还有其他类封装了 OLE 功能以及 ODBC 和 DAO 数据访问功能。  
  
 例如，Win32 的窗口概念由 MFC 类 `CWnd` 封装。 也就是说，名为 `CWnd` 的 C++ 类封装或“包装”了表示 Windows 窗口的 `HWND` 句柄。 同样，`CDialog` 类封装了 Win32 对话框。  
  
 以 C++ 类 `CWnd` 为例，封装意味着它包含了 `HWND` 类型的成员变量，并且它的成员函数封装了对采用 `HWND` 作为参数的 Win32 函数的调用。 类成员函数通常具有与其所封装的 Win32 函数相同的名称。  
  
## <a name="in-this-section"></a>本节内容  
 [SDI 和 MDI](../mfc/sdi-and-mdi.md)  
  
 [文档、视图和框架](../mfc/documents-views-and-the-framework.md)  
  
 [向导和资源编辑器](../mfc/wizards-and-the-resource-editors.md)  
  
## <a name="in-related-sections"></a>相关章节  
 [基于框架生成](../mfc/building-on-the-framework.md)  
  
 [框架如何调用你的代码](../mfc/how-the-framework-calls-your-code.md)  
  
 [CWinApp：应用程序类](../mfc/cwinapp-the-application-class.md)  
  
 [文档模板和文档/视图创建过程](../mfc/document-templates-and-the-document-view-creation-process.md)  
  
 [消息处理和映射](../mfc/message-handling-and-mapping.md)  
  
 [窗口对象](../mfc/window-objects.md)  
  
## <a name="see-also"></a>请参阅  
 [使用类编写 Windows 应用程序](../mfc/using-the-classes-to-write-applications-for-windows.md)
