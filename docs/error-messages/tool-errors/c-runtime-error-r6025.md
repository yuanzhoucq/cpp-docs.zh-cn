---
title: C 运行时错误 R6025 |Microsoft Docs
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
ms.openlocfilehash: b774c5f99387ca4403941d1461593bef8801e5de
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220627"
---
# <a name="c-runtime-error-r6025"></a>C 运行时错误 R6025
纯虚函数调用  
  
> [!NOTE]
>  如果运行应用时遇到此错误消息，该应用已关闭，因为它具有内部问题。 此错误的最常见原因是应用程序中或已损坏的安装中的 bug。  
>   
>  可以尝试以下步骤来修复此错误：  
>   
>  -   使用**应用程序和功能**或**程序和功能**页**控制面板**来修复或重新安装该程序。  
> -   检查**Windows Update**中**控制面板**的软件更新。  
> -   检查应用程序的更新版本。 如果问题仍然存在，请与应用供应商联系。  
  
 **程序员提供的的信息**  
  
 实例化没有对象，来处理纯虚函数调用。  
  
 通过在通过指针创建的强制转换为派生类的类型，但实际指向基类的抽象基类中调用虚拟函数导致此错误。 可能会发生此转换从**void** <strong>\*</strong>为指向一个类时**void** <strong>\*</strong>是在基类的构造过程中创建。  
  
 有关详细信息，请参阅[Microsoft 支持部门](http://go.microsoft.com/fwlink/p/?linkid=75220)网站。