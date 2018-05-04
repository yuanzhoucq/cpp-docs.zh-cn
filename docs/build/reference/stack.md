---
title: -堆栈 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /stack
dev_langs:
- C++
helpviewer_keywords:
- -STACK editbin option
- STACK editbin option
- stack, setting size
- /STACK editbin option
ms.assetid: a39bcff0-c945-4355-80cc-8e4f24a5f142
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a82111ce950d14bc6b3e270ee9a658d806b28b62
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="stack"></a>/STACK
```  
/STACK:reserve[,commit]  
```  
  
## <a name="remarks"></a>备注  
 此选项以字节为单位设置堆栈大小，并以十进制或 C 语言表示法采用自变量。 /STACK 选项仅适用于可执行文件。  
  
 *保留*自变量指定的总堆栈分配虚拟内存中。 EDITBIN 将指定的值与最接近的 4 个字节向上舍入。  
  
 可选`commit`自变量是取决于操作系统的解释。 在 Windows NT、 Windows 95 和 Windows 98、`commit`指定要一次分配的物理内存量。 提交的虚拟内存后，要分页文件中保留的空间。 更高`commit`值可以节省的时间，当应用程序需要更多堆栈空间但会增加内存需求并可能延长启动时间。  
  
## <a name="see-also"></a>请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)