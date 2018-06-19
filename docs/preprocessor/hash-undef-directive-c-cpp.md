---
title: '#undef 指令 （C/c + +） |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#undef'
dev_langs:
- C++
helpviewer_keywords:
- '#undef directive'
- undef directive (#undef)
- preprocessor, directives
ms.assetid: 88900e0e-2c19-4a63-b681-f3d3133c24ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16b8c937ad62ddc6738c626543dab2d4e5453bc5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33839775"
---
# <a name="undef-directive-cc"></a>#undef 指令 (C/C++)
移除（取消定义）之前使用 `#define` 创建的名称。  
  
## <a name="syntax"></a>语法  
  
```  
  
#undef   
identifier  
  
```  
  
## <a name="remarks"></a>备注  
 `#undef`指令可移除的当前定义*标识符*。 因此，随后出现*标识符*由预处理器忽略。 若要删除宏定义使用`#undef`，指定仅宏*标识符*; 不提供的参数列表。  
  
 您还可以将 `#undef` 指令应用于之前没有定义的标识符。 这将确保该标识符是不确定的。 宏替换不在 `#undef` 语句中执行。  
  
 `#undef` 指令通常与 `#define` 指令成对，用来在源程序中创建一个区域，使其中的标识符具有特殊含义。 例如，源程序的特定函数可使用清单常量定义不会影响程序的其余部分的环境特定值。 `#undef` 指令还可与 `#if` 指令一起使用来控制源程序的条件编译。 请参阅[#if、 #elif，#else 和 #endif 指令](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)有关详细信息。  
  
 在以下示例中，`#undef` 指令将移除符号常量和宏的定义。 请注意，只给定宏的标识符。  
  
```  
#define WIDTH 80  
#define ADD( X, Y ) ((X) + (Y))  
.  
.  
.  
#undef WIDTH  
#undef ADD  
```  
  
 **Microsoft 专用**  
  
 可以使用 /U 选项后跟要取消定义的宏名称从命令行取消定义宏。 发出此命令的效果相当于一系列`#undef`*宏名称*语句开头的文件。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [预处理器指令](../preprocessor/preprocessor-directives.md)