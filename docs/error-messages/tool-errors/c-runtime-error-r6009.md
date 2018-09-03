---
title: C 运行时错误 R6009 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6009
dev_langs:
- C++
helpviewer_keywords:
- R6009
ms.assetid: edfb1f8b-3807-48f4-a994-318923b747ae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2c44c08ec3b52cc53e1b29a0ecf23606c3ec06a4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33296843"
---
# <a name="c-runtime-error-r6009"></a>C 运行时错误 R6009
环境所需的空间不足  
  
> [!NOTE]
>  如果你在上运行应用程序时遇到此错误消息，应用程序关闭，因为它存在内部内存问题。 有几个可能的原因，对于此错误，但通常因为极低内存条件，环境变量或程序中的 bug 占用太多内存。  
>   
>  可以尝试以下步骤来修复此错误：  
>   
>  -   关闭其他正在运行的应用程序或重新启动计算机以释放内存。  
> -   使用**的应用和功能**或**程序和功能**页面**控制面板**来修复或重新安装该程序。  
> -   检查**Windows Update**中**控制面板**软件更新。  
> -   检查应用程序的更新版本。 如果问题仍然存在，请与应用供应商联系。  
  
 **程序员提供的的信息**  
  
 没有足够的内存来加载程序，但没有足够内存来创建**envp**数组。  这可能导致内存严重不足条件，或按非常大的环境变量的使用情况。 请考虑以下解决方案之一：  
  
-   增加可用程序内存量。  
  
-   减少的数量和命令行自变量的大小。  
  
-   通过删除不需要的变量以减小环境大小。