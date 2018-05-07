---
title: C 运行时错误 R6026 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6026
dev_langs:
- C++
helpviewer_keywords:
- R6026
ms.assetid: 7ea751f8-fc20-46ab-99ef-84c95ca0b6b4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7c8bea41b946db67ce24a52393d87873926f3f8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="c-runtime-error-r6026"></a>C 运行时错误 R6026
stdio 初始化所需的空间不足  
  
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
  
 没有足够可用内存以初始化 C 运行时中的标准 I/O 支持时发生此错误。 在应用启动时，通常会出现此错误。 验证你的应用程序的驱动程序和它所加载的 dll 不损坏在启动堆。