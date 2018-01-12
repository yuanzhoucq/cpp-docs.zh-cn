---
title: "C 运行时错误 R6018 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6018
dev_langs: C++
helpviewer_keywords: R6018
ms.assetid: f6dd40d1-a119-4d8b-b39e-97350ea23349
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0102739bb4fa8961e089d348e1ff93f62fdde6b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6018"></a>C 运行时错误 R6018
意外的堆错误  
  
> [!NOTE]
>  如果你在上运行应用程序时遇到此错误消息，应用程序关闭，因为它存在内部问题。 有几个可能的原因，对于此错误，但通常因为在应用程序的代码缺陷。  
>   
>  可以尝试以下步骤来修复此错误：  
>   
>  -   使用**的应用和功能**或**程序和功能**页面**控制面板**来修复或重新安装该程序。  
> -   检查**Windows Update**中**控制面板**软件更新。  
> -   检查应用程序的更新版本。 如果问题仍然存在，请与应用供应商联系。  
  
 **程序员提供的的信息**  
  
 程序执行内存管理操作时遇到意外的错误。  
  
 通常，如果程序无意中更改了运行时堆数据，则会发生此错误。 但是，它可能还会引起的运行时或操作系统代码中的内部错误。  
  
 若要解决此问题，检查你的代码中的堆损坏 bug。 有关详细信息和示例，请参阅[CRT 调试堆详细信息](/visualstudio/debugger/crt-debug-heap-details)。 接下来，检查您的应用程序部署使用最新可再发行文件。 有关信息，请参阅[Visual c + + 中的部署](../../ide/deployment-in-visual-cpp.md)。