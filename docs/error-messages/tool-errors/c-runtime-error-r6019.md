---
title: C 运行时错误 R6019 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6019
dev_langs:
- C++
helpviewer_keywords:
- R6019
ms.assetid: 8129923e-7db2-40ee-9602-def9365f8d28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95950254d4a0611d9690b8636eb50f2fc1f0f264
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33314224"
---
# <a name="c-runtime-error-r6019"></a>C 运行时错误 R6019
无法打开控制台设备  
  
> [!NOTE]
>  如果你在上运行应用程序时遇到此错误消息，应用程序关闭，因为它试图访问控制台中，但它没有足够的权限。 有几个可能的原因，对于此错误，但是它通常是因为该程序必须运行以管理员身份，或者是一个 bug，在程序中。  
>   
>  可以尝试以下步骤来修复此错误：  
>   
>  -   以管理员身份运行程序。  
> -   使用**的应用和功能**或**程序和功能**页面**控制面板**来修复或重新安装该程序。  
> -   检查**Windows Update**中**控制面板**软件更新。  
> -   检查应用程序的更新版本。 如果问题仍然存在，请与应用供应商联系。  
  
 **程序员提供的的信息**  
  
 发生此错误是因为应用程序调用的控制台函数，但操作系统没有授予对控制台的访问。 除在调试模式下，控制台函数通常不允许 Microsoft 应用商店应用中。 如果你的应用需要管理员特权才能运行，请确保它安装默认情况下以管理员身份运行。