---
title: "在以前的运行时版本上运行的 c + + clr 应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- applications [C++], runtime version specified
- versions [C++]
- app.config files, runtime version specified
- compatibility [C++], runtime version specified
- backward compatibility [C++], runtime version specified
- application deployment [C++], runtime version specified
- common language runtime [C++], version specified
- deploying applications [C++], runtime version specified
ms.assetid: 940171b7-6937-4b14-8e87-c199e23f4f2e
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1f64c0dc31be260332d4d79e8fa38d63bbf6357c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="running-a-c-clr-application-on-a-previous-runtime-version"></a>在以前版本的运行时上运行 C++ /clr 应用程序
除非另行指定，生成的 c + +.NET Framework 应用程序以在编译器用于生成应用程序的公共语言运行时 (CLR) 版本上运行。 但是，很可能为提供所需的功能的任何其他版本上运行的运行时的一个版本生成的.exe 应用程序。  
  
 若要完成此操作，提供一个包含中的运行时版本信息的 app.config 文件`supportedRuntime`标记。  
  
 在运行时，app.config 文件必须具有窗体的名称*文件名.ext*.config，其中*文件名.ext*是启动了应用程序的可执行文件的名称，并且它必须是所在的目录可执行文件。 例如，如果你的应用程序名为 TestApp.exe，app.config 文件将被命名为 TestApp.exe.config。  
  
 如果指定多个运行时版本，并且具有多个安装的运行时版本的计算机上运行应用程序，应用程序将使用指定的配置文件中且已安装的第一个版本。  
  
 有关详细信息，请参阅[如何： 配置应用以面向.NET Framework 版本](http://msdn.microsoft.com/en-us/5247b307-89ca-417b-8dd0-e8f9bd2f4717)。  
  
 在版本 1.0 或 1.1 版的 CLR，由 Visual c + + 生成的应用程序上运行编译器必须编译使用[/clr:initialAppDomain](../build/reference/clr-common-language-runtime-compilation.md)。  
  
## <a name="see-also"></a>请参阅  
 [部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)