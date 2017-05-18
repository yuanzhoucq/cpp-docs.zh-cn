---
title: _crtDbgFlag | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _crtDbgFlag
- crtDbgFlag
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, tracking flag
- crtDbgFlag constant
- _crtDbgFlag constant
- debug heap, tracking memory on
- debug heap, control flags
- enable memory allocation tracking flag
- memory, tracking on the debug heap
ms.assetid: 9e7adb47-8ab9-4e19-81d5-e2f237979973
caps.latest.revision: 8
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
ms.openlocfilehash: 4f4c3a874d59095d620a04d5ebb6ac88e2bdfa66
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="crtdbgflag"></a>_CRTDBG_CHECK_CRT_DF
**_crtDbgFlag** 标志由五个位域组成，这些字段可控制如何在堆的调试版本上跟踪、验证、报告和转储内存分配。 使用 [_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md) 函数设置该标志的位域。 将在 Crtdbg.h 中声明此标志及其位域。 此标志仅当已在应用程序中定义 [_DEBUG](../c-runtime-library/debug.md) 标志时才可用。  
  
 有关将此标志与其他调试函数结合使用的详细信息，请参阅[堆状态报告函数](/visualstudio/debugger/crt-debug-heap-details)。  
  
## <a name="see-also"></a>另请参阅  
 [控制标志](../c-runtime-library/control-flags.md)
