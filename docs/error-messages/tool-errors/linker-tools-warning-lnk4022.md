---
title: "链接器工具警告 LNK4022 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4022
dev_langs: C++
helpviewer_keywords: LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9e35974a72de349f94f2189f676b6dc955c48fab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4022"></a>链接器工具警告 LNK4022
找不到符号 symbol 的唯一匹配项  
  
 给定的未修饰符号链接或 LIB 找到多个匹配项，无法解析多义性。 会不生成任何输出文件 （.exe、.dll、.exp 或.lib）。 此警告后跟一个警告[LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md)每个重复的符号和最后跟错误[LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md)。  
  
 若要防止出现此警告，请以修饰形式指定符号。 运行[DUMPBIN](../../build/reference/dumpbin-options.md)上的对象，若要查看修饰名。