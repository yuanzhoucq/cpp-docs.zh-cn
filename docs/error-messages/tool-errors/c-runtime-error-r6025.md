---
title: C 运行时错误 R6025 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6025
dev_langs:
- C++
helpviewer_keywords:
- R6025
ms.assetid: afa06d98-9c36-445b-b3e7-b6409bc8e779
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: abdbdbf918462dfb83eff07190c32af1f1b3d015
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302021"
---
# <a name="c-runtime-error-r6025"></a>C 运行时错误 R6025
纯虚函数调用  
  
> [!NOTE]
>  如果你在上运行应用程序时遇到此错误消息，应用程序关闭，因为它存在内部问题。 此错误的最常见原因是应用程序或已损坏的安装中的 bug。  
>   
>  可以尝试以下步骤来修复此错误：  
>   
>  -   使用**的应用和功能**或**程序和功能**页面**控制面板**来修复或重新安装该程序。  
> -   检查**Windows Update**中**控制面板**软件更新。  
> -   检查应用程序的更新版本。 如果问题仍然存在，请与应用供应商联系。  
  
 **程序员提供的的信息**  
  
 没有任何对象已实例化来处理纯虚函数调用。  
  
 通过调用中通过指针创建的强制转换为的类型派生的类，但实际指针到基类的抽象基类的虚函数导致此错误。 这会时发生从强制转换**void\*** 的指针到类时**void\*** 基本类的构造过程中创建了。  
  
 有关详细信息，请参阅[Microsoft 支持](http://go.microsoft.com/fwlink/p/?linkid=75220)网站。