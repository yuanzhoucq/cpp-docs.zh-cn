---
title: -LINKERMEMBER |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /linkermember
dev_langs:
- C++
helpviewer_keywords:
- /LINKERMEMBER dumpbin option
- LINKERMEMBER dumpbin option
- -LINKERMEMBER dumpbin option
ms.assetid: c96868c1-d70e-4651-ae36-c55b58b16406
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac961f985de65bb7eea9a4ad0f5d10b75fbe60d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="linkermember"></a>/LINKERMEMBER
```  
/LINKERMEMBER[:{1|2}]  
```  
  
## <a name="remarks"></a>备注  
 此选项显示在库中定义的公共符号。 指定要显示在对象的顺序，以及它们的偏移量的符号的 1 自变量。 指定要显示偏移量和对象的索引号的 2 的自变量，并列出字母顺序排列，以及每个对象索引中的符号。 若要获取这两个输出，请不带编号的参数指定 /LINKERMEMBER。  
  
 仅[/HEADERS](../../build/reference/headers.md) DUMPBIN 选项是可供产生的文件的使用[/GL](../../build/reference/gl-whole-program-optimization.md)编译器选项。  
  
## <a name="see-also"></a>请参阅  
 [DUMPBIN 选项](../../build/reference/dumpbin-options.md)