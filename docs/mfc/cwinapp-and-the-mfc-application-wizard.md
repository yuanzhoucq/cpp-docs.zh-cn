---
title: CWinApp 和 MFC 应用程序向导 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CWinApp
dev_langs:
- C++
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 702c20fc9f303670d2add4ebf840785acff7750d
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2018
ms.locfileid: "39026480"
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>CWinApp 和 MFC 应用程序向导
MFC 应用程序向导创建主干应用程序时, 声明应用程序类派生自[CWinApp](../mfc/reference/cwinapp-class.md)。 MFC 应用程序向导还会生成一个包含以下各项的实现文件：  
  
-   消息映射为应用程序类的。  
  
-   一个空的类的构造函数。  
  
-   声明的类对象和变量。  
  
-   标准实现你`InitInstance`成员函数。  
  
 应用程序类位于项目标头和主源代码文件中。 类和创建文件的名称基于在 MFC 应用程序向导中提供的项目名称。 若要查看这些类的代码的最简单方法是通过[类视图](http://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925)。  
  
 标准实现和消息映射提供足够用于多种用途，但你可以根据需要修改它们。 这些实现最有趣的是`InitInstance`成员函数。 通常情况下，会将代码添加到的主干实现`InitInstance`。  
  
## <a name="see-also"></a>请参阅  
 [CWinApp： 应用程序类](../mfc/cwinapp-the-application-class.md)   
 [可重写 CWinApp 成员函数](../mfc/overridable-cwinapp-member-functions.md)   
 [特殊的 CWinApp 服务](../mfc/special-cwinapp-services.md)

