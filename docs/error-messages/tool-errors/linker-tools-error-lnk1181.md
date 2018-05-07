---
title: 链接器工具错误 LNK1181 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1181
dev_langs:
- C++
helpviewer_keywords:
- LNK1181
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 617678e5453acdafaf72875857b0e0f9b84a110a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1181"></a>链接器工具错误 LNK1181
无法打开输入的文件 filename  
  
 找不到链接器`filename`因为它不存在或找不到路径。  
  
 错误 lnk1181 某些常见原因：  
  
-   `filename` 链接器行中，但该文件上的其他依赖关系不存在，因此引用。  
  
-   A **/LIBPATH**指定目录包含的语句`filename`缺少。  
  
 若要解决上述问题，请确保引用链接器行上的任何文件都存在于系统。  另外，请确保没有 **/LIBPATH**包含依赖于链接器文件每个目录的语句。  
  
 LNK1181 的另一个可能原因是具有嵌入的空格的长文件名都不包含用引号引起来。  在这种情况下，链接器将仅识别最多包含第一个空格，文件名称，然后假定为文件扩展名。 obj。这种情况的解决方案是括起来的长文件名 （路径和文件名） 用引号引起来。  
  
 有关详细信息，请参阅[用作链接器输入的.lib 文件](../../build/reference/dot-lib-files-as-linker-input.md)。  
  
## <a name="see-also"></a>请参阅  
 [/LIBPATH（附加的 Libpath）](../../build/reference/libpath-additional-libpath.md)