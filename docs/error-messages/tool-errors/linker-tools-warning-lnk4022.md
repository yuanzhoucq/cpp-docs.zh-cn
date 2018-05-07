---
title: 链接器工具警告 LNK4022 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4022
dev_langs:
- C++
helpviewer_keywords:
- LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cffb9c4c67bc3003b8dcdda0ad3a2e8d55abe932
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4022"></a>链接器工具警告 LNK4022
找不到符号 symbol 的唯一匹配项  
  
 给定的未修饰符号链接或 LIB 找到多个匹配项，无法解析多义性。 会不生成任何输出文件 （.exe、.dll、.exp 或.lib）。 此警告后跟一个警告[LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md)每个重复的符号和最后跟错误[LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md)。  
  
 若要防止出现此警告，请以修饰形式指定符号。 运行[DUMPBIN](../../build/reference/dumpbin-options.md)上的对象，若要查看修饰名。