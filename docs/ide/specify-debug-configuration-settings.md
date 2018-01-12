---
title: "从现有代码新建项目调试设置 （Visual c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.importwiz.debugsettings
dev_langs: C++
ms.assetid: 607339a8-9d33-458b-8095-dc73f374e29d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ec7d357d53cb93ad5ba81c02fc3ccf1931cdd1cf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="specify-debug-configuration-settings-create-new-project-from-existing-code-files-wizard"></a>“从现有代码文件创建新项目”向导 ->“指定调试配置设置”
从现有代码文件创建新项目向导的此页用于指定调试配置项目设置。  
  
## <a name="task-list"></a>任务列表  
 [如何：通过现有代码创建 C++ 项目](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>UIElement 列表  
 **生成命令行**  
 指定生成新项目的命令行。 例如，输入编译器 （加上任何开关和自变量） 的名称，或生成脚本，你想要用于生成新项目。 启用此选项时**使用外部生成系统**中选择选项**指定项目设置**页; 否则它是不可用。  
  
 **重新生成命令行**  
 指定将重新生成新项目的命令行。 启用此选项时**使用外部生成系统**中选择选项**指定项目设置**页; 否则它是不可用。  
  
 **清除命令行**  
 指定要删除生成的新项目的生成工具的支持文件的命令行。 启用此选项时**使用外部生成系统**中选择选项**指定项目设置**页; 否则它是不可用。  
  
 **输出 （对于调试）**  
 指定新项目的调试配置的输出文件的目录路径。 启用此选项时**使用外部生成系统**中选择选项**指定项目设置**页; 否则它是不可用。  
  
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
