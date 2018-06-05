---
title: 如何：通过现有代码创建 C++ 项目 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++, creating projects from existing code
ms.assetid: e328a938-395c-48ea-9e35-dd433de12b31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1786e5704d7afd07576ab738d907eb841518f8be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330130"
---
# <a name="how-to-create-a-c-project-from-existing-code"></a>如何：通过现有代码创建 C++ 项目

在 Visual Studio 中，可以使用“从现有代码文件新建项目”向导将现有代码文件移植到 Visual C++ 项目中。 Visual Studio 的较旧 Express 版本中不提供该向导。 此向导创建新的解决方案和项目，它们使用 MSBuild 系统来管理源文件和生成配置。  
  
通过将现有代码文件移植到 Visual C++ 项目，即可使用内置于 IDE 的所有本机 MSBuild 项目管理功能。 如果更想使用现有的生成系统（例如 nmake 生成文件、CMake 或其他），则可以改为使用“打开文件夹”选项。 有关详细信息，请参阅 [Visual C++ 中的“打开文件夹”项目](../ide/non-msbuild-projects.md)。 通过这两个选项都可以使用 IDE 功能，例如 [IntelliSense](/visualstudio/ide/using-intellisense) 和 [项目属性](../ide/working-with-project-properties.md)。  
  
### <a name="to-create-a-c-project-from-existing-code"></a>从现有代码创建 C++ 项目  
  
1.  在“文件”菜单上，指向“新建”，然后单击“从现有代码创建项目”。  
  
1.  在“从现有代码文件创建新项目”向导的首页，在“要创建什么类型的项目”列表中选择“Visual C++”。 选择“下一步”  继续。 
  
1.  指定项目位置和源文件的目录。 有关此页面的详细信息，请参阅[“从现有代码文件创建新项目”向导 ->“指定项目位置和源文件”](../ide/specify-project-location-and-source-files.md)。 选择“下一步”  继续。  
  
1.  指定要使用的项目设置。 有关此页面的详细信息，请参阅[“从现有代码文件创建新项目”向导 ->“指定项目设置”](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)。 选择“下一步”  继续。  

1.  指定要使用的调试配置设置。 有关此页面的详细信息，请参阅[“从现有代码文件创建新项目”向导 ->“指定调试配置设置”](../ide/specify-debug-configuration-settings.md)。 选择“下一步”  继续。  

1.  指定要使用的发布配置设置。 有关此页面的详细信息，请参阅[“从现有代码文件创建新项目”向导 ->“指定发布配置设置”](../ide/specify-release-configuration.md)。 单击“完成”以生成新项目。  
  
## <a name="see-also"></a>请参阅  

[“从现有代码文件创建新项目”向导 ->“指定项目位置和源文件”](../ide/specify-project-location-and-source-files.md)   
[“从现有代码文件创建新项目”向导 ->“指定项目设置”](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)   
[“从现有代码文件创建新项目”向导 ->“指定调试配置设置”](../ide/specify-debug-configuration-settings.md)   
[指定发布配置设置，“从现有代码文件创建新项目”向导](../ide/specify-release-configuration.md)