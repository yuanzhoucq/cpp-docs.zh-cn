---
title: "优化 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ae1988292b1f6dfa35f4cb77d145641528ed827f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="optimize"></a>optimize
指定要对每个函数执行的优化。  
  
## <a name="syntax"></a>语法  
  
```  
  
#pragma optimize( "[optimization-list]", {on | off} )  
```  
  
## <a name="remarks"></a>备注  
 **优化**杂注必须显示在函数的外部，并在杂注显示后定义的第一个函数处生效。 **上**和**关闭**参数中指定的选项将打开*优化列表*打开或关闭。  
  
 *优化列表*可以为零个或多个下表中所示的参数。  
  
### <a name="parameters-of-the-optimize-pragma"></a>optimize 杂注的参数  
  
|参数|优化的类型|  
|--------------------|--------------------------|  
|**g**|启用全局优化。|  
|**s**或**t**|指定机器代码的短或快速序列。|  
|**y**|在程序堆栈上生成帧指针。|  
  
 这些是与使用的相同字母[/O](../build/reference/o-options-optimize-code.md)编译器选项。 例如，以下杂注等效于**/Os**编译器选项：  
  
```  
#pragma optimize( "ts", on )  
```  
  
 使用**优化**杂注和空字符串 (**""**) 是指令的特殊形式：  
  
 当你使用**关闭**参数，它会关闭本主题前面的表中列出的优化。  
  
 当你使用**上**参数，它将重置优化为使用指定的那些[/O](../build/reference/o-options-optimize-code.md)编译器选项。  
  
```  
#pragma optimize( "", off )  
.  
.  
.  
#pragma optimize( "", on )   
```  
  
## <a name="see-also"></a>请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)