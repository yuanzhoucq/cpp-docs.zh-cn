---
title: "符合 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- conform_CPP
- vc-pragma.conform
dev_langs: C++
helpviewer_keywords:
- conform pragma
- forScope conform pragma
- pragmas, conform
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5f876c1b921a00c251010d22e2cdd000a405a651
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="conform"></a>conform
**C + + 专用**  
  
 指定的运行时行为[/zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)编译器选项。  
  
## <a name="syntax"></a>语法  
  
```  
#pragma conform(name [, show ] [, on | off ] [ [, push | pop ] [, identifier ] ] )  
```  
  
#### <a name="parameters"></a>参数  
 *name*  
 指定要修改的编译器选项的名称。 仅有的有效*名称*是`forScope`。  
  
 **显示**（可选）  
 导致的当前设置*名称*（true 或 false），以在编译期间显示通过一条警告消息。 例如 `#pragma conform(forScope, show)`。  
  
 **打开、 关闭**（可选）  
 设置*名称*到**上**使[/zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)编译器选项。 默认值是**关闭**。  
  
 **推送**（可选）  
 当前值推送*名称*到内部编译器堆栈。 如果指定*标识符*，你可以指定**上**或**关闭**值*名称*推送到堆栈上。 例如 `#pragma conform(forScope, push, myname, on)`。  
  
 **pop** （可选）  
 设置的值*名称*到内部编译器堆栈，然后弹出堆栈顶部的值。 如果具有指定标识符**pop**，堆栈将弹回，直到它找到的记录*标识符*，这也会弹出; 的当前值*名称*中堆栈上的下一步记录将成为新值*名称*。 如果指定使用 pop*标识符*不在堆栈上，记录**pop**将被忽略。  
  
 *标识符*（可选）  
 可以包含在**推送**或**pop**命令。 如果*标识符*使用时，则**上**或**关闭**说明符还可以使用。  
  
## <a name="example"></a>示例  
  
```  
// pragma_directive_conform.cpp  
// compile with: /W1  
// C4811 expected  
#pragma conform(forScope, show)  
#pragma conform(forScope, push, x, on)  
#pragma conform(forScope, push, x1, off)  
#pragma conform(forScope, push, x2, off)  
#pragma conform(forScope, push, x3, off)  
#pragma conform(forScope, show)  
#pragma conform(forScope, pop, x1)  
#pragma conform(forScope, show)  
  
int main() {}  
```  
  
## <a name="see-also"></a>请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)