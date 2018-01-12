---
title: "如何： 通过现有代码创建 c + + 项目 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: C++, creating projects from existing code
ms.assetid: e328a938-395c-48ea-9e35-dd433de12b31
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d6781709c105c606f6ceb856654525385738c1ca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-a-c-project-from-existing-code"></a>如何：通过现有代码创建 C++ 项目

在 Visual Studio 中，你可以将现有代码文件移植到 Visual c + + 项目通过使用**从现有代码文件创建新项目**向导。 此向导不是较旧的 Express 版本的 Visual Studio 中提供的。 此向导将创建一个新解决方案和项目使用 MSBuild 系统来管理你的源文件并生成配置。  
  
将现有代码文件移植到 Visual c + + 项目，可使用所有 IDE 中内置的本机 MSBuild 项目管理功能。 如果你希望使用现有的生成系统，如 nmake 生成文件、 CMake 或替代，你可以使用打开文件夹选项。 有关详细信息，请参阅 [Visual C++ 中的“打开文件夹”项目](../ide/non-msbuild-projects.md)。 这两个选项让你使用 IDE 功能，如[IntelliSense](/visualstudio/ide/using-intellisense)和[项目属性](../ide/working-with-project-properties.md)。  
  
### <a name="to-create-a-c-project-from-existing-code"></a>从现有代码创建 C++ 项目  
  
1.  上**文件**菜单上，指向**新建**，然后单击**从现有代码创建项目**。  
  
1.  第一页上**从现有代码文件创建新项目**向导中，选择**Visual c + +**中**要创建什么类型的项目**列表。 选择“下一步”  继续。 
  
1.  指定项目位置和源文件的目录。 有关此页上的详细信息，请参阅[指定项目位置和源文件，创建新从现有代码文件项目向导](../ide/specify-project-location-and-source-files.md)。 选择“下一步”  继续。  
  
1.  指定要使用的项目设置。 有关此页上的详细信息，请参阅[指定项目设置、 创建新从现有代码文件项目向导](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)。 选择“下一步”  继续。  

1.  指定要使用的调试配置设置。 有关此页上的详细信息，请参阅[指定调试配置设置，创建新项目从现有代码文件向导](../ide/specify-debug-configuration-settings.md)。 选择“下一步”  继续。  

1.  指定要使用的发布配置设置。 有关此页上的详细信息，请参阅[指定发布配置设置，创建新项目从现有代码文件向导](../ide/specify-release-configuration.md)。 选择**完成**以生成新项目。  
  
## <a name="see-also"></a>请参阅  

[指定项目位置和源文件，从现有代码文件向导创建新项目](../ide/specify-project-location-and-source-files.md)   
[指定项目设置，可从现有代码文件向导创建新项目](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)   
[指定调试配置设置、 从现有代码文件向导创建新项目](../ide/specify-debug-configuration-settings.md)   
[指定发布配置设置，“从现有代码文件创建新项目”向导](../ide/specify-release-configuration.md)