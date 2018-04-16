---
title: "Commit-To-Disk 常量 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.constants
dev_langs:
- C++
helpviewer_keywords:
- commit-to-disk constants
ms.assetid: 0b903b23-b4fa-431e-a937-51d95f695ecf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9dd4873d8f9b3a658996bfd057372e8fb29e3478
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="commit-to-disk-constants"></a>Commit-To-Disk 常量
**Microsoft 专用**  
  
## <a name="syntax"></a>语法  
  
```  
  
#include <stdio.h>  
```  
  
## <a name="remarks"></a>备注  
 这些特定于 Microsoft 的常量指定将与打开的文件关联的缓冲区刷新到操作系统缓冲区还是磁盘。 模式包含在指定读/写访问权限的类型（“r”、“w”、“a”、“r+”、“w+”、“a+”）的字符串中。  
  
 提交到磁盘模式如下所示：  
  
 **c**  
 将指定缓冲区的未写入内容写入磁盘。 此提交到磁盘功能仅在显式调用 [fflush](../c-runtime-library/reference/fflush.md) 或 [_flushall](../c-runtime-library/reference/flushall.md) 函数时生效。 此模式在处理敏感数据时很有用。 例如，如果在调用 `fflush` 或 `_flushall` 后程序终止，您可以确保数据已到达操作系统的缓冲区。 但是，除非文件是使用 c 选项打开的，否则当操作系统也终止时，数据可能从不会将文件传送到磁盘。  
  
 **n**  
 将指定缓冲区的未写入内容写入操作系统的缓冲区。 操作系统可以缓存数据然后确定写入到磁盘的最佳时间。 在大多数情况下，此行为有助于产生有效的程序行为。 但是，如果保留数据很重要（如银行交易或机票信息）请考虑使用 c 选项。 n 模式是默认设置。  
  
> [!NOTE]
>  c 和 n 选项不是 `fopen` 的 ANSI 标准的一部分，而是 Microsoft 扩展，因此不应在需要 ANSI 可移植性的情况下使用。  
  
## <a name="using-the-commit-to-disk-feature-with-existing-code"></a>将提交到磁盘功能用于现有代码  
 默认情况下，调用 [fflush](../c-runtime-library/reference/fflush.md) 或 [_flushall](../c-runtime-library/reference/flushall.md) 库函数会将数据写入操作系统维护的缓冲区。 操作系统确定将数据实际写入磁盘的最佳时间。 利用运行库的提交到磁盘功能，您可以确保关键数据直接写入磁盘而不是操作系统的缓冲区。 您可以将此功能提供给现有程序，而无需通过将该程序的对象文件与 COMMODE.OBJ 链接来重写程序。  
  
 在生成的可执行文件中，调用 `fflush` 会将缓冲区的内容直接写入磁盘，而调用 `_flushall` 会将所有缓冲区的内容写入磁盘。 这两个函数是唯一受 COMMODE.OBJ 影响函的数。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [流 I/O](../c-runtime-library/stream-i-o.md)   
 [_fdopen、_wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fopen、_wfopen](../c-runtime-library/reference/fopen-wfopen.md)   
 [全局常量](../c-runtime-library/global-constants.md)