---
title: 定义 NMAKE 宏 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- defining NMAKE macros
- NMAKE macros, defining
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5997eee052ebba198e1fb52da35322c65a32627b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="defining-an-nmake-macro"></a>定义 NMAKE 宏
## <a name="syntax"></a>语法  
  
```  
  
macroname=string  
```  
  
## <a name="remarks"></a>备注  
 *Macroname*是字母、 数字和下划线 (_) 最多 1,024 个字符的组合和是敏感。 *Macroname*可以包含一个调用的宏。 如果*macroname*包含完全由调用的宏，从中调用该宏不能为空或未定义。  
  
 `string`可以是任意的零个或多个字符序列。 一个 null 字符串包含零个字符或仅空格或制表符。 `string`可以包含宏调用。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
 [在宏中的特殊字符](../build/special-characters-in-macros.md)  
  
 [Null 和未定义宏](../build/null-and-undefined-macros.md)  
  
 [定义宏的位置](../build/where-to-define-macros.md)  
  
 [宏定义中的优先级](../build/precedence-in-macro-definitions.md)  
  
## <a name="see-also"></a>请参阅  
 [宏和 NMAKE](../build/macros-and-nmake.md)