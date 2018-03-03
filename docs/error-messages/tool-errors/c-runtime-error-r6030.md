---
title: "C 运行时错误 R6030 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6030
dev_langs:
- C++
helpviewer_keywords:
- R6030
ms.assetid: 0238a6c3-a033-4046-8adc-f8f99d961153
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7bc7c5db2b486ef051975c0e8d31d6c24ca5aa6a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6030"></a>C 运行时错误 R6030
未初始化的 CRT  
  
> [!NOTE]
>  如果你在上运行应用程序时遇到此错误消息，应用程序关闭，因为它存在内部问题。 此问题是最常见的原因，某些安全软件程序或极少数情况下，该程序中的 bug。  
>   
>  可以尝试以下步骤来修复此错误：  
>   
>  -   您的安全软件可能有特定说明如何减轻此问题。 检查详细信息的安全软件供应商的网站。 或者，检查有更新版本的安全软件，或尝试不同的安全软件。  
> -   使用**的应用和功能**或**程序和功能**页面**控制面板**来修复或重新安装该程序。  
> -   检查**Windows Update**中**控制面板**软件更新。  
> -   检查应用程序的更新版本。 如果问题仍然存在，请与应用供应商联系。  
  
 **程序员提供的的信息**  
  
 如果你正在使用 C 运行时 (CRT)，但未执行 CRT 启动代码，则会发生此错误。 就可能出现此错误，如果链接器切换[/ENTRY](../../build/reference/entry-entry-point-symbol.md)用于重写的默认开始地址，通常**mainCRTStartup**， **wmainCRTStartup**为控制台 EXE， **WinMainCRTStartup**或**wWinMainCRTStartup**的 Windows EXE，或**_DllMainCRTStartup** dll。 除非在启动时调用上述函数之一，C 运行时将不会初始化。 启动将调用这些函数通常默认情况下当你链接到 C 运行时库，并使用普通**主要**， **wmain**， **WinMain**，或**DllMain**入口点。  
  
 还有可能另一个程序使用代码注入技术来捕获某些 DLL 库调用时收到此错误。 某些具有侵入性安全程序使用此技术。 在 Visual Studio 2015 之前的 Visual c + + 版本中，可以使用静态链接的 CRT 库来解决此问题，但不是建议这样做出于安全和应用程序更新的原因。 更正此问题可能需要最终用户操作。