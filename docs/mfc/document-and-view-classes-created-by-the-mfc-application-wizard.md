---
title: "文档和查看 MFC 应用程序向导创建的类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- document classes [MFC]
- document classes [MFC], created by application wizards
- application wizards [MFC], document/view classes created
- view classes [MFC], created by application wizards
ms.assetid: 70c34a60-2701-4981-acea-c08a5787d8e6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7cddf8b72e9927a298cbd39d4f9790965e4b8f74
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="document-and-view-classes-created-by-the-mfc-application-wizard"></a>MFC 应用程序向导创建的文档和视图类
MFC 应用程序向导为您创建了主干文档和视图类，从而让您在程序开发中抢占先机。 然后，你可以[将命令和消息映射到这些类](../mfc/reference/mapping-messages-to-functions.md)并使用 Visual c + + 源代码编辑器编写其成员函数。  
  
 MFC 应用程序向导创建的文档类派生自类[CDocument](../mfc/reference/cdocument-class.md)。 视图类派生自[CView](../mfc/reference/cview-class.md)。 应用程序向导为这些类提供的名称以及包含这些类的文件基于您在“应用程序向导”对话框中提供的项目名称。 在应用程序向导中，您可以使用“生成的类”页修改默认名称。  
  
 某些应用程序可能需要多个文档类、视图类或框架窗口类。 有关详细信息，请参阅[多文档类型、 视图和框架窗口](../mfc/multiple-document-types-views-and-frame-windows.md)。  
  
## <a name="see-also"></a>请参阅  
 [文档/视图体系结构](../mfc/document-view-architecture.md)

