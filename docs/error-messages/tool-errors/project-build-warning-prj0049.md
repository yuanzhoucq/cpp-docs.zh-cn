---
title: "项目生成警告 PRJ0049 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- PRJ0049
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f87bc7e26fd7cc50defbc086594c92a3ea339ef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-warning-prj0049"></a>项目生成警告 PRJ0049
引用的目标\<引用 > 需要.NET Framework \<MinFrameworkVersion > 并将无法在此项目的目标框架上运行  
  
 通过使用 Visual Studio 2008 创建的应用程序可以指定哪个版本的[!INCLUDE[dnprdnshort](../../error-messages/tool-errors/includes/dnprdnshort_md.md)]它们应为目标。 如果添加对程序集或依赖于的版本的项目的引用[!INCLUDE[dnprdnshort](../../error-messages/tool-errors/includes/dnprdnshort_md.md)]晚于目标版本，你会收到此警告在编译时。  
  
### <a name="to-correct-this-warning"></a>若要更正此警告  
  
1.  选择以下选项之一：  
  
    -   更改在项目的目标的框架**属性页**对话框中，以便它晚于或等于最小的 framework 版本的所有引用的程序集和项目。 有关详细信息，请参阅[添加引用](../../ide/adding-references-in-visual-cpp-projects.md)。  
  
    -   移除对程序集或具有晚于目标框架的最小的 framework 版本的项目的引用。 这些项都标有一个警告图标，在项目的**属性页**。  
  
## <a name="see-also"></a>请参阅  
 [项目生成错误和警告 (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)