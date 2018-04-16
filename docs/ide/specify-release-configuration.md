---
title: "从现有代码新建项目版本配置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.importwiz.releasesettings
dev_langs:
- C++
ms.assetid: 3e2fc73c-bdbd-4790-b2bd-d31731f0cece
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ff208af8bb89dbcb7df00b37ce542a5adae5fa23
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="specify-release-configuration-settings-create-new-project-from-existing-code-files-wizard"></a>“从现有代码文件创建新项目”向导 ->“指定发布配置设置”
从现有代码文件创建新项目向导的此页用于指定发布配置项目设置。  
  
## <a name="task-list"></a>任务列表  
 [如何：通过现有代码创建 C++ 项目](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>UIElement 列表  
 **调试配置相同**  
 指定此向导将生成版本配置项目设置相同调试配置项目设置。 默认情况下选中此选项。 此页上的所有其他选项不处于非活动状态，除非取消选中此框。  
  
 **生成命令行**  
 指定生成新项目的命令行。 输入的编译器加上任何开关或你想要用于生成新项目的自变量的名称。 启用此选项时**使用外部生成系统**中选择选项**指定项目设置**页。  
  
 **重新生成命令行**  
 指定将重新生成新项目的命令行。 启用此选项时**使用外部生成系统**中选择选项**指定项目设置**页。  
  
 **清除命令行**  
 指定要删除生成的新项目的生成工具的支持文件的命令行。 启用此选项时**使用外部生成系统**中选择选项**指定项目设置**页。  
  
 **输出 （对于调试）**  
 指定新项目的调试配置的输出文件的目录路径。 启用此选项时**使用外部生成系统**中选择选项**指定项目设置**页。  
  
 **预处理器定义 (/ D)**  
 定义新项目的预处理器符号。 有关详细信息，请参阅 [/D (Preprocessor Definitions)](../build/reference/d-preprocessor-definitions.md)。  
  
 **包括搜索路径 (/ 我)**  
 指定要添加到的编译器将搜索的目录列表若要解析的文件引用传递到新项目中的预处理器指令的目录路径。 有关详细信息，请参阅 [/I（附加包含目录）](../build/reference/i-additional-include-directories.md)。  
  
 **强制包含的文件 (/FI)**  
 指定要处理时生成新项目的标头文件。 有关详细信息，请参阅 [/FI（命名强制包含文件）](../build/reference/fi-name-forced-include-file.md)。  
  
 **.NET 程序集搜索路径 (/ AI)**  
 指定传递给新的项目中的预处理器指令的编译器将搜索若要解决.NET 程序集引用的目录路径。 有关详细信息，请参阅 [/AI（指定元数据目录）](../build/reference/ai-specify-metadata-directories.md)。  
  
 **强制使用.NET 程序集 (/ FU)**  
 指定要处理在生成新项目时的.NET 程序集。 有关详细信息，请参阅 [/FU（命名强制 #using 文件）](../build/reference/fu-name-forced-hash-using-file.md)。  
  
## <a name="see-also"></a>请参阅  
 [指定项目设置，“从现有代码文件创建新项目”向导](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)