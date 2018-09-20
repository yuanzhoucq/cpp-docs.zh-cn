---
title: inline_depth |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- inline_depth_CPP
- vc-pragma.inline_depth
dev_langs:
- C++
helpviewer_keywords:
- pragmas, inline_depth
- inline_depth pragma
ms.assetid: 2bba60fe-43ea-4d09-90f7-aafaba3bad07
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cbb90d36ea3da8e443eede8a3d74a35246077d52
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410256"
---
# <a name="inlinedepth"></a>inline_depth
指定内联启发式搜索深度，这样一来，如果它是在晚于 （在调用关系图） 深度，则函数将不内联*n*。  
  
## <a name="syntax"></a>语法  
  
```  
#pragma inline_depth( [n] )  
```  
  
## <a name="remarks"></a>备注  
 
此杂注控制标记的函数的内联[内联](../cpp/inline-functions-cpp.md)并[__inline](../cpp/inline-functions-cpp.md)或下自动内联`/Ob2`选项。  
  
*n*可以是介于 0 到 255 之间，其中 255 表示调用关系图中的无限的深度，而零禁止内联展开。  当*n*未指定，则使用默认值 (254)。  
  
**Inline_depth**杂注控制可以展开一系列函数调用的次数。 例如，如果内联深度为 4，并且如果 A 调用 B，然后 B 调用 C，则所有三种调用将为展开的内联。 但是，如果最接近的内联展开为 2，则仅展开 A 和 B，而 C 作为函数调用保留。  
  
若要使用此杂注，必须设置`/Ob`为 1 或 2 的编译器选项。 使用该杂注的深度设置在该杂注后进行第一个函数调用时生效。  
  
可在展开过程中减小内联深度，但不能增大该深度。 如果内联深度为 6，并且在扩展过程，预处理器遇到**inline_depth**杂注和值为 8，深度保持为 6。  
  
**Inline_depth**杂注对函数标记为无效`__forceinline`。  
  
> [!NOTE]
> 可对递归函数进行内联替换，最大调用深度为 16。  
  
## <a name="see-also"></a>请参阅  
 
[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[inline_recursion](../preprocessor/inline-recursion.md)