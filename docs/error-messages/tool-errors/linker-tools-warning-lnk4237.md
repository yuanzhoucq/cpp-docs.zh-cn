---
title: 链接器工具警告 LNK4237 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4237
dev_langs:
- C++
helpviewer_keywords:
- LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5acccf52d3738985c7a83432342952af03bf78b4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4237"></a>链接器工具警告 LNK4237
指定当从 dll; 导入的 /SUBSYSTEM:NATIVE使用 /SUBSYSTEM:CONSOLE 或 /SUBSYSTEM:WINDOWS。  
  
 [/SUBSYSTEM:NATIVE](../../build/reference/subsystem-specify-subsystem.md)指定当生成 (Win32) windows 应用程序，该服务直接使用一个或多个以下：  
  
-   Kernel32.dll  
  
-   gdi32.dll  
  
-   user32.dll  
  
-   msvcrt * dll 之一。  
  
 通过不指定解决此警告 **/SUBSYSTEM:NATIVE**。