---
title: _crtDbgFlag | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb0c22e65c33ab8f689026e916f550280bf6a8ad
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="crtdbgflag"></a>_CRTDBG_CHECK_CRT_DF
**_crtDbgFlag** 标志由五个位域组成，这些字段可控制如何在堆的调试版本上跟踪、验证、报告和转储内存分配。 使用 [_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md) 函数设置该标志的位域。 将在 Crtdbg.h 中声明此标志及其位域。 此标志仅当已在应用程序中定义 [_DEBUG](../c-runtime-library/debug.md) 标志时才可用。  
  
 有关将此标志与其他调试函数结合使用的详细信息，请参阅[堆状态报告函数](/visualstudio/debugger/crt-debug-heap-details)。  
  
## <a name="see-also"></a>请参阅  
 [控制标志](../c-runtime-library/control-flags.md)