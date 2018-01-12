---
title: "C 运行时错误 R6033 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6033
dev_langs: C++
helpviewer_keywords: R6033
ms.assetid: f9cffdc9-81bd-4a64-a698-02762cbd82c9
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9f2ef73d3cb82a65c8114d2e7f921b47ffd45d65
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6033"></a>C 运行时错误 R6033
若要使用从在本机代码初始化过程中此程序集的 MSIL 代码的尝试。 这表示你的应用程序中存在 bug。 它很可能是调用 MSIL 编译的结果 (/ clr) 函数从本机构造函数或从 DllMain。  
  
> [!NOTE]
>  如果你在上运行应用程序时遇到此错误消息，应用程序关闭，因为它存在内部问题。 通过在应用中，bug 或中的 bug 或它使用的扩展，可以导致此错误。  
>   
>  可以尝试以下步骤来修复此错误：  
>   
>  -   使用**的应用和功能**或**程序和功能**页面**控制面板**来修复或重新安装该程序。  
> -   使用**的应用和功能**或**程序和功能**页面**控制面板**删除、 修复或重新安装任何扩展或外接程序。  
> -   检查**Windows Update**中**控制面板**软件更新。  
> -   检查应用程序的更新版本。 如果问题仍然存在，请与应用供应商联系。  
  
 **程序员提供的的信息**  
  
 此诊断指示在加载程序锁期间执行了 MSIL 指令。 如果你已使用 /clr 标志编译本机 c + + 便会出现此问题。 仅对包含托管的代码模块使用 /clr 标志。 有关详细信息，请参阅[初始化混合程序集的](../../dotnet/initialization-of-mixed-assemblies.md)。