---
title: "C 运行时错误 R6027 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6027
dev_langs: C++
helpviewer_keywords: R6027
ms.assetid: c06a62b3-08d9-4bf5-bcad-8340ec552f69
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 080b5cdf2e68889e7d11fe14f20524f9cced03c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6027"></a>C 运行时错误 R6027
lowio 初始化所需的空间不足  
  
> [!NOTE]
>  如果你在上运行应用程序时遇到此错误消息，应用程序关闭，因为它存在内部内存问题。 有几个可能的原因，对于此错误，但通常它由极低的内存不足情况导致。 应用程序中的 bug，它使用的 Visual c + + 库损坏或驱动程序，也可以将导致该错误。  
>   
>  可以尝试以下步骤来修复此错误：  
>   
>  -   关闭其他正在运行的应用程序或重新启动计算机以释放内存。  
> -   使用**的应用和功能**或**程序和功能**页面**控制面板**来修复或重新安装该程序。  
> -   如果在另一个应用程序或驱动程序的最近安装之前运行的应用程序，使用**的应用和功能**或**程序和功能**页面**控制面板**删除新的应用程序或驱动程序，然后重试您的应用程序。  
> -   使用**的应用和功能**或**程序和功能**页面**控制面板**来修复或重新安装 Microsoft Visual c + + Redistributable 的所有副本。  
> -   检查**Windows Update**中**控制面板**软件更新。  
> -   检查应用程序的更新版本。 如果问题仍然存在，请与应用供应商联系。  
  
 **程序员提供的的信息**  
  
 当没有足够的可用内存可用于初始化 C 运行时中的低级别 I/O 支持时，将发生此错误。 在应用启动时，通常会出现此错误。 验证你的应用程序的驱动程序和它所加载的 dll 不损坏在启动堆。