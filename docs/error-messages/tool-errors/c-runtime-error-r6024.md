---
title: "C 运行时错误 R6024 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6024
dev_langs: C++
helpviewer_keywords: R6024
ms.assetid: 0fb11c0f-9b81-4cab-81bd-4785742946a5
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 98d52a7d143a1c65caee3fe68902e3a25b3a5f4c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6024"></a>C 运行时错误 R6024
_onexit/atexit 表所需的空间不足  
  
> [!NOTE]
>  如果你在上运行应用程序时遇到此错误消息，应用程序关闭，因为它存在内部内存问题。 此错误通常是通过一个极低内存条件或极少数情况下，在程序中的 bug 或它使用的 Visual c + + 库损坏引起的。  
>   
>  可以尝试以下步骤来修复此错误：  
>   
>  -   关闭其他正在运行的应用程序或重新启动计算机以释放内存。  
> -   使用**的应用和功能**或**程序和功能**页面**控制面板**来修复或重新安装该程序。  
> -   使用**的应用和功能**或**程序和功能**页面**控制面板**来修复或重新安装 Microsoft Visual c + + Redistributable 的所有副本。  
> -   检查**Windows Update**中**控制面板**软件更新。  
> -   检查应用程序的更新版本。 如果问题仍然存在，请与应用供应商联系。  
  
 **程序员提供的的信息**  
  
 发生此错误的原因时没有内存可用于`_onexit`或`atexit`函数。 通过内存不足的情况导致此错误。 你可以考虑在应用启动，以帮助在保存用户数据和执行干净的应用程序的预分配缓冲区退出中内存不足情况。