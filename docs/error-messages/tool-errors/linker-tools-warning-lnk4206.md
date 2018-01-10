---
title: "链接器工具警告 LNK4206 |Microsoft 文档"
ms.date: 12/05/2017
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4206
dev_langs: C++
helpviewer_keywords: LNK4206
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cd13ac59aefa074db869f0502743c7a49d23082c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4206"></a>链接器工具警告 LNK4206

> 找不到; 的预编译的类型信息*filename*未链接或重写; 正在链接对象，如同没有调试信息

*Filename*对象文件中，使用编译的[/Yc](../../build/reference/yc-create-precompiled-header-file.md)，或者未在 LINK 命令中指定，或者已被覆盖。

此警告的一个常见方案是用 /Yc 编译.obj 时在库中，并在有没有对该.obj 在代码中的符号引用。  在这种情况下，链接器将不使用 （或甚至查看）.obj 文件。  在此情况下，你应重新编译你的代码并使用[/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md)使用编译的对象[/Yu](../../build/reference/yu-use-precompiled-header-file.md)。