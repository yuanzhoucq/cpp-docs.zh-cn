---
title: "_CRTDBG_MAP_ALLOC | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRTDBG_MAP_ALLOC
- _CRTDBG_MAP_ALLOC
dev_langs:
- C++
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- memory allocation, in debug builds
- CRTDBG_MAP_ALLOC macro
ms.assetid: 435242b8-caea-4063-b765-4a608200312b
caps.latest.revision: 8
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 709ba57e3cca392d2440c7ad528125dc31070cac
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="crtdbgmapalloc"></a>_CRTDBG_MAP_ALLOC
在应用程序的调试版本中定义 **_CRTDBG_MAP_ALLOC** 标志时，堆函数的基础版本将直接映射到其调试版本。 该标志在 Crtdbg.h 中用于执行映射。 此标志仅当已在应用程序中定义 [_DEBUG](../c-runtime-library/debug.md) 标志时才可用。  
  
 有关使用堆函数的调试版本和基础版本的更多信息，请参阅[使用调试版本与基础版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。  
  
## <a name="see-also"></a>另请参阅  
 [控制标志](../c-runtime-library/control-flags.md)
