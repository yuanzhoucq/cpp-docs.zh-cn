---
title: 链接器工具警告 LNK4001 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4001
dev_langs:
- C++
helpviewer_keywords:
- LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: acf65c00c5c039769a05e009dcfe46ea42633ac4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4001"></a>链接器工具警告 LNK4001
未指定; 的对象文件使用库  
  
 链接器已传递一个或多个.lib 文件，但不是含.obj 文件。  
  
 链接器不能访问它就可以访问在.obj 文件中的.lib 文件中的信息，因为此警告意味着需要显式指定其他链接器选项。 例如，你可能需要指定[/计算机](../../build/reference/machine-specify-target-platform.md)， [/out](../../build/reference/out-output-file-name.md)，或[/ENTRY](../../build/reference/entry-entry-point-symbol.md)选项。