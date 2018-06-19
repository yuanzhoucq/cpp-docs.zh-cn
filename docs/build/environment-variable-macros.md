---
title: 环境变量宏 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, environment variable macros
- environment variables, macros in NMAKE
- macros, environment-variable
ms.assetid: f8e96635-0906-47b0-9f56-12a6fdf5e347
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ebebb6e7d237746f96c7ac7e27c249244ff825b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367428"
---
# <a name="environment-variable-macros"></a>环境变量宏
NMAKE 继承的会话开始之前存在的环境变量的宏定义。 如果变量在操作系统环境中设置的则可以用作 NMAKE 宏。 继承的名称将转换为大写。 在预处理前发生继承。 使用 /E 选项会导致从环境变量重写中生成文件同名的任何宏继承的宏。  
  
 在会话中，可以重新定义环境变量宏，这将更改相应的环境变量。 你还可以更改使用 SET 命令的环境变量。 使用 SET 命令在会话中更改环境变量不会更改相应的宏，但是。  
  
 例如：  
  
```  
PATH=$(PATH);\nonesuch  
  
all:  
    echo %PATH%  
```  
  
 在此示例中，更改`PATH`更改相应的环境变量`PATH`; 追加`\nonesuch`到你的路径。  
  
 如果环境变量定义为一个字符串，将生成文件中语法不正确，没有宏创建和不生成任何警告。 如果变量的值包含美元符号 （$），NMAKE 会将其解释为宏调用的开头。 使用宏可能导致意外的行为。  
  
## <a name="see-also"></a>请参阅  
 [特殊 NMAKE 宏](../build/special-nmake-macros.md)