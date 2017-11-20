---
title: "C 运行时错误 R6025 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6025
dev_langs: C++
helpviewer_keywords: R6025
ms.assetid: afa06d98-9c36-445b-b3e7-b6409bc8e779
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 06fd7aa6458a3c7e89d80146ec20a0e3f7587b4b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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
  
 有关详细信息，请参阅[Microsoft 支持](http://go.microsoft.com/fwlink/?LinkId=75220)网站。