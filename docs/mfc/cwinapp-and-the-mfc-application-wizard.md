---
title: "CWinApp 和 MFC 应用程序向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CWinApp
dev_langs:
- C++
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 603504025bf4069f7a56b705e50a176975dbf244
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>CWinApp 和 MFC 应用程序向导
MFC 应用程序向导创建主干应用程序时, 声明应用程序类派生自[CWinApp](../mfc/reference/cwinapp-class.md)。 MFC 应用程序向导还会生成实现文件包含以下各项：  
  
-   消息映射的应用程序类。  
  
-   空类的构造函数。  
  
-   声明的类对象和变量。  
  
-   标准实现你`InitInstance`成员函数。  
  
 应用程序类位于项目标头和主源代码文件中。 类和创建的文件的名称基于在 MFC 应用程序向导中提供的项目名称。 若要查看这些类的代码的最简单方法是通过[类视图](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)。  
  
 标准实现和消息映射提供足够用于多种用途，但你可以根据需要修改它们。 这些实现的有趣的是`InitInstance`成员函数。 通常情况下，你将在其中将代码添加到的主干实现`InitInstance`。  
  
## <a name="see-also"></a>请参阅  
 [CWinApp： 应用程序类](../mfc/cwinapp-the-application-class.md)   
 [可重写 CWinApp 成员函数](../mfc/overridable-cwinapp-member-functions.md)   
 [特殊的 CWinApp 服务](../mfc/special-cwinapp-services.md)

