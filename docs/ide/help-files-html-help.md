---
title: "帮助文件 （HTML 帮助） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: file types [C++], HTML Help files
ms.assetid: d30a1b1b-318f-4a78-8b60-93da53a224a8
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c96cd6ad904439f556f2baa51602353ea00c5ac7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="help-files-html-help"></a>帮助文件（HTML 帮助）
当你将 HTML 帮助类型的帮助支持通过选择添加到你的应用程序创建以下文件**上下文相关帮助**复选框，然后选择**HTML 帮助格式**中[高级功能](../mfc/reference/advanced-features-mfc-application-wizard.md)MFC 应用程序向导页。  
  
|文件名|目录位置|解决方案资源管理器位置|描述|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Projname*.hhp|*Projname*\hlp|HTML 帮助文件|帮助项目文件。 它包含编译成.hxs 文件的帮助文件或.chm 文件所需的数据。|  
|*Projname*.hhk|*Projname*\hlp|HTML 帮助文件|包含帮助主题的索引。|  
|*Projname*.hhc|*Projname*\hlp|HTML 帮助文件|帮助项目的内容。|  
|Makehtmlhelp.bat|*Projname*|源文件|系统使用它来编译项目时生成的帮助项目。|  
|Afxcore.htm|*Projname*\hlp|HTML 帮助主题|包含标准 MFC 命令和屏幕对象的标准帮助主题。 添加到此文件的帮助主题。|  
|Afxprint.htm|*Projname*\hlp|HTML 帮助主题|包含打印命令的帮助主题。|  
|*.jpg;\*.gif|*Projname*\hlp\Images|资源文件|包含有关不同的生成的帮助文件的主题的图像。|  
  
## <a name="see-also"></a>请参阅  
 [为 Visual C++ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)