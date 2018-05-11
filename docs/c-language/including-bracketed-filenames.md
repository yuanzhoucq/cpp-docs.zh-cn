---
title: 包含用括号括起来的文件名 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 6a4e5411-c35e-48b8-90ef-b37ac324ed94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ba45c21029a428784e1c8410dcf42295aa6350f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="including-bracketed-filenames"></a>包含用括号括起来的文件名
**ANSI 3.8.2** 查找可包含源文件的方法  
  
 对于用尖括号括起的文件规范，预处理器不会搜索父文件的目录。 “父级”文件是其中包含 [#include](../preprocessor/hash-include-directive-c-cpp.md) 指令的文件。 相反，它首先会通过 /I 后面的编译器命令行上指定的目录中搜索文件。 如果 /I 选项不存在或失败，预处理器会使用 INCLUDE 环境变量在尖括号中查找包含文件。 INCLUDE 环境变量可以包含使用分号 (;) 分隔的多个路径。 如果多个目录显示为 /I 选项的一部分或在 INCLUDE 环境变量中，预处理器会按它们的出现顺序搜索它们。  
  
## <a name="see-also"></a>请参阅  
 [预处理指令](../c-language/preprocessing-directives.md)