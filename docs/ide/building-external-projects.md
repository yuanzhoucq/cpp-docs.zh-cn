---
title: "生成外部项目 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- external projects
- Visual C++ projects, external projects
- builds [C++], external projects
- projects [C++], external projects
- Makefile projects, external projects
ms.assetid: 650b7803-ea91-489d-bee3-8f3e990e223c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 16b73349a220f392730dd5526fd5f3d59e59754d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="building-external-projects"></a>生成外部项目
外部项目是使用生成文件或处于 （外或外部的） 之外的其他功能的 Visual c + + 项目的 Visual c + + 开发环境。  
  
 如果你有一个外部项目 （例如，生成文件项目），你想要在 Visual c + + 开发环境中生成，创建生成文件项目并指定你的项目的生成文件的应用程序向导在生成命令和输出。 有关详细信息，请参阅[创建生成文件项目](../ide/creating-a-makefile-project.md)。  
  
 请注意 Visual c + + 不再支持从开发环境中导出的活动项目的生成文件的功能。 使用[Devenv 命令行开关](/visualstudio/ide/reference/devenv-command-line-switches)来生成在命令行 Visual Studio 项目。  
  
## <a name="see-also"></a>请参阅  
 [在 Visual Studio 中生成 C++ 项目](../ide/building-cpp-projects-in-visual-studio.md)