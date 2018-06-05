---
title: 生成外部项目 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- external projects
- Visual C++ projects, external projects
- builds [C++], external projects
- projects [C++], external projects
- Makefile projects, external projects
ms.assetid: 650b7803-ea91-489d-bee3-8f3e990e223c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97b6aa1e5939afe55644df6529bf75ba043f20bb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330341"
---
# <a name="building-external-projects"></a>生成外部项目
外部项目是一个 Visual C++ 项目，它使用生成文件或 Visual C++ 开发环境外部的其他工具。  
  
 如果有要在 Visual C++ 开发环境中生成的外部项目（例如生成文件项目），请创建一个生成文件项目并在生成文件应用程序向导中指定项目的生成命令和输出。 有关详细信息，请参阅[创建生成文件项目](../ide/creating-a-makefile-project.md)。  
  
 请注意，Visual C++ 不再支持从开发环境导出活动项目的生成文件的功能。 使用 [Devenv 命令行开关](/visualstudio/ide/reference/devenv-command-line-switches)在命令行中生成 Visual Studio 项目。  
  
## <a name="see-also"></a>请参阅  
 [在 Visual Studio 中生成 C++ 项目](../ide/building-cpp-projects-in-visual-studio.md)