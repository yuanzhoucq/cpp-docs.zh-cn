---
title: "链接器工具警告 LNK4237 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4237
dev_langs:
- C++
helpviewer_keywords:
- LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 718058dae02e9dfe9b653abea91993ec6662f5c1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4237"></a>链接器工具警告 LNK4237
指定当从 dll; 导入的 /SUBSYSTEM:NATIVE使用 /SUBSYSTEM:CONSOLE 或 /SUBSYSTEM:WINDOWS。  
  
 [/SUBSYSTEM:NATIVE](../../build/reference/subsystem-specify-subsystem.md)指定当生成 (Win32) windows 应用程序，该服务直接使用一个或多个以下：  
  
-   Kernel32.dll  
  
-   gdi32.dll  
  
-   user32.dll  
  
-   msvcrt * dll 之一。  
  
 通过不指定解决此警告**/SUBSYSTEM:NATIVE**。