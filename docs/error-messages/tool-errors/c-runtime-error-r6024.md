---
title: C 运行时错误 R6024 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6024
dev_langs:
- C++
helpviewer_keywords:
- R6024
ms.assetid: 0fb11c0f-9b81-4cab-81bd-4785742946a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bcdfee9da378415afe0b88fe6eed18ec8f570d4a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
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