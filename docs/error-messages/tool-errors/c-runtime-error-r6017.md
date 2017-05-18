---
title: "C 运行时错误 R6017 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6017
dev_langs:
- C++
helpviewer_keywords:
- R6017
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6cad5222fb0d97594d5b13b5cf8903eb2934ee88
ms.openlocfilehash: 903d440dbedbe704ae28be643337619ca1e09c69
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="c-runtime-error-r6017"></a>C 运行时错误 R6017
意外的多线程锁定错误  
  
> [!NOTE]
>  如果在运行应用程序时遇到此错误消息，该应用程序关闭，因为它具有内部问题。 有多种原因引起此错误，但通常由应用程序的代码中有缺陷。  
>   
>  可以尝试以下步骤来修复此错误：  
>   
>  -   使用**应用程序和功能**或**程序和功能**页**控制面板**修复或重新安装该程序。  
> -   检查**Windows Update**中**控制面板**为软件更新。  
> -   检查应用程序的更新版本。 如果问题仍然存在，请与应用程序供应商联系。  
  
 **程序员提供的的信息**  
  
 进程在尝试访问系统资源上的 C 运行时多线程锁定时接收到意外的错误。 如果该进程会无意中改变了运行时堆数据，通常会出现此错误。 但是，它可以也可能导致由运行时库或操作系统代码中出现内部错误。  
  
 若要解决此问题，检查在代码中的堆损坏错误。 有关详细信息和示例，请参阅[CRT 调试堆详细信息](/visualstudio/debugger/crt-debug-heap-details)。 接下来，检查您的应用程序的部署使用最新可再发行组件。 有关信息，请参阅[Visual c + + 中的部署](../../ide/deployment-in-visual-cpp.md)。
