---
title: 帮助文件（HTML 帮助）| Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- file types [C++], HTML Help files
ms.assetid: d30a1b1b-318f-4a78-8b60-93da53a224a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d180fe4f9cf1baf26b27423ffda975bfe0fe85ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325070"
---
# <a name="help-files-html-help"></a>帮助文件（HTML 帮助）
在 MFC 应用程序向导的[高级功能](../mfc/reference/advanced-features-mfc-application-wizard.md)页中，选中“上下文相关帮助”复选框，然后选择“HTML 帮助格式”，将 HTML 帮助类型的帮助支持添加到应用程序时将创建以下文件。  
  
|文件名|目录位置|解决方案资源管理器位置|描述|  
|---------------|------------------------|--------------------------------|-----------------|  
|Projname.hhp|Projname\hlp|HTML 帮助文件|帮助项目文件。 它包含将帮助文件编译为 .hxs 文件或 .chm 文件所需的数据。|  
|Projname.hhk|Projname\hlp|HTML 帮助文件|包含帮助主题的索引。|  
|Projname.hhc|Projname\hlp|HTML 帮助文件|帮助项目的内容。|  
|Makehtmlhelp.bat|Projname|源文件|编译项目时，系统使用它来生成帮助项目。|  
|Afxcore.htm|Projname\hlp|HTML 帮助主题|包含标准 MFC 命令和屏幕对象的标准帮助主题。 将你自己的帮助主题添加到此文件。|  
|Afxprint.htm|Projname\hlp|HTML 帮助主题|包含打印命令的帮助主题。|  
|*.jpg; \*.gif|Projname\hlp\Images|资源文件|包含所生成的不同帮助文件主题的图像。|  
  
## <a name="see-also"></a>请参阅  
 [为 Visual C++ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)