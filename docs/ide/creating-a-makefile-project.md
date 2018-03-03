---
title: "创建生成文件项目 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.makefile.project
dev_langs:
- C++
helpviewer_keywords:
- Makefile projects, creating
- project files [C++], Makefile projects
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5e86bedbf83cd417cfc41317e5887304cda7ee76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-makefile-project"></a>创建生成文件项目
如果你的项目是通过生成文件从命令行生成的，Visual Studio 开发环境将无法识别该项目。 若要打开并生成你的项目使用[!INCLUDE[vsUltShort](../ide/includes/vsultshort_md.md)]，Visual Studio Professional 或 Visual Studio Express for Windows Desktop，首先通过选择生成文件项目模板创建一个空项目。 然后可以从 Visual Studio 开发环境中使用该项目生成项目。  
  
 在“解决方案资源管理器”中，项目不显示文件。 项目指定生成设置，这些设置反映在项目的属性页中。  
  
 在项目中指定的输出文件对生成脚本生成的名称无效；它仅声明意图。  
  
### <a name="to-create-a-makefile-project"></a>创建生成文件项目  
  
1.  按照帮助主题中的说明[使用 Visual c + + 应用程序向导创建项目](../ide/creating-desktop-projects-by-using-application-wizards.md)。  
  
2.  在**新项目**对话框中，选择**生成文件项目**在模板窗格中，以打开向导。  
  
3.  在[应用程序设置](../ide/application-settings-makefile-project-wizard.md)页上，提供命令、 输出、 清除和重新生成信息。  
  
4.  单击**完成**要关闭向导并打开新创建的项目中**解决方案资源管理器**。  
  
 可以在项目的属性页中查看和编辑项目的属性。 请参阅[设置 Visual c + + 项目属性](../ide/working-with-project-properties.md)有关显示的属性页信息。  
  
## <a name="see-also"></a>请参阅  
 [生成文件项目向导](../ide/makefile-project-wizard.md)   
 [生成文件中的特殊字符](../build/special-characters-in-a-makefile.md)   
 [生成文件的内容](../build/contents-of-a-makefile.md)