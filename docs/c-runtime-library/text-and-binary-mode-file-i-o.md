---
title: "文本和二进制模式文件 I/O| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.io
dev_langs: C++
helpviewer_keywords:
- files [C++], open functions
- I/O [CRT], text files
- functions [CRT], file access
- binary access, binary mode file I/O
- translation, modes
- I/O [CRT], binary
- text files, I/O
- I/O [CRT], translation modes
- translation modes (file I/O)
- binary access
ms.assetid: 3196e321-8b87-4609-b302-cd6f3c516051
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 50387aa2512e38a4e9f13fdfb1b042c3df2de45c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="text-and-binary-mode-file-io"></a>文本和二进制模式文件 I/O
文件 I/O 操作将在文本或二进制这两种转换模式之一中进行，具体取决于文件时在哪种模式下打开的。 数据文件通常在文本模式下处理。 若要控制文件转换模式，可以：  
  
-   保留当前默认设置，并且仅在打开选定文件时指定替代模式。  
  
-   使用函数 [_set_fmode](../c-runtime-library/reference/set-fmode.md) 更改新打开的文件的默认模式。 使用 [_get_fmode](../c-runtime-library/reference/get-fmode.md) 查找当前默认模式。 初始默认设置为文本模式 (`_O_TEXT`)。  
  
-   通过在程序中设置全局变量 [_fmode](../c-runtime-library/fmode.md) 来直接更改默认转换模式。 函数 `_set_fmode` 将设置此变量的值，不过也可以直接设置它。  
  
 当调用一个文件打开函数（如 [_open](../c-runtime-library/reference/open-wopen.md)、[fopen](../c-runtime-library/reference/fopen-wfopen.md)、[fopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)、[freopen](../c-runtime-library/reference/freopen-wfreopen.md)、[freopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)、[_fsopen](../c-runtime-library/reference/fsopen-wfsopen.md) 或 [_sopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)）时，可通过指定函数 [_set_fmode](../c-runtime-library/reference/set-fmode.md) 的相应参数来替代 `_fmode` 的当前默认设置。 默认情况下，`stdin`、`stdout` 和 `stderr` 流始终在文本模式中打开；在打开这些文件中的任一文件时，也可以重写该默认值。 使用 [_setmode](../c-runtime-library/reference/setmode.md) 可在文件打开后利用文件说明符更改转换模式。  
  
## <a name="see-also"></a>请参阅  
 [输入和输出](../c-runtime-library/input-and-output.md)   
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)