---
title: C 运行时错误 R6002 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6002
dev_langs:
- C++
helpviewer_keywords:
- R6002
ms.assetid: 8fbbe65a-9c43-459e-8342-e1f6d1cef7d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50a970ecea4fdd7d397c09672b0548be947cab1e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298559"
---
# <a name="c-runtime-error-r6002"></a>C 运行时错误 R6002
未加载的浮点支持  
  
 必需的浮点库未链接。  
  
> [!NOTE]
>  如果你在上运行应用程序时遇到此错误消息，应用程序关闭，因为它存在内部问题。 有几个可能的原因，对于此错误，但通常因为通过应用程序的代码中有缺陷，或尝试运行的应用程序不为你特定计算机的处理器生成。  
>   
>  可以尝试以下步骤来修复此错误：  
>   
>  -   使用**的应用和功能**或**程序和功能**页面**控制面板**来修复或重新安装该程序。  
> -   检查**Windows Update**中**控制面板**软件更新。  
> -   检查应用程序的更新版本。 如果问题仍然存在，请与应用供应商联系。  
  
 **程序员提供的的信息**  
  
 当未链接的浮点库，可以在应用程序中出现此错误。 请检查这些原因之一：  
  
-   格式字符串`printf_s`或`scanf_s`函数包含浮点格式规范中，并且该程序未包含任何浮点值或变量。 若要解决此问题，使用浮点自变量对应于浮点格式规范中，或在程序中的其他地方执行浮点赋值。 这将导致要加载的浮点支持。  
  
-   编译器通过加载浮点支持仅在必要时，最小化程序的大小。 编译器无法检测浮点运算或浮点格式规范在格式字符串中，因此它不会加载必要的浮点例程。 若要解决此问题，使用浮点格式规范和提供浮点自变量，或在程序中的其他地方执行浮点赋值。 这将导致要加载的浮点支持。  
  
-   在混合语言程序中，当程序进行链接时在 FORTRAN 库之前指定的 C 库。 重新链接和上一次指定的 C 库。