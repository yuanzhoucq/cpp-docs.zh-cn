---
title: "控制标志 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.flags
dev_langs:
- C++
helpviewer_keywords:
- flags, control
- heap allocation, control flags
- debug heap, control flags
ms.assetid: 8dbd24a5-0633-42d1-9771-776db338465f
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 9e8d2030edb3c048ec67ddd5a7b0782d2bbfdd9a
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="control-flags"></a>控制标志
Microsoft C 运行库的调试版本使用下列标志控制堆分配和报告过程。 有关详细信息，请参阅 [CRT 调试方法](/visualstudio/debugger/crt-debugging-techniques)。  
  
|Flag|说明|  
|----------|-----------------|  
|[_CRTDBG_MAP_ALLOC](../c-runtime-library/crtdbg-map-alloc.md)|将基堆函数映射到其对应的调试版本|  
|[_DEBUG](../c-runtime-library/debug.md)|支持使用运行时函数的调试版本|  
|[_crtDbgFlag](../c-runtime-library/crtdbgflag.md)|控制调试堆管理器如何跟踪分配|  
  
 这些标志可以使用 /D 命令行选项或 `#define` 指令定义。 如果标志是使用 `#define` 定义的，则指令必须在标头文件包含例程声明的语句之前显示。  
  
## <a name="see-also"></a>另请参阅  
 [全局变量和标准类型](../c-runtime-library/global-variables-and-standard-types.md)
