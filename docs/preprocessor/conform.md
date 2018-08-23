---
title: 符合 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- conform_CPP
- vc-pragma.conform
dev_langs:
- C++
helpviewer_keywords:
- conform pragma
- forScope conform pragma
- pragmas, conform
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c6204349731222df99683ddb20b2b2d827b3fcd
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2018
ms.locfileid: "42543079"
---
# <a name="conform"></a>conform
**C + + 专用**  
  
指定的运行时行为[/zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)编译器选项。  
  
## <a name="syntax"></a>语法  
  
```  
#pragma conform(name [, show ] [, on | off ] [ [, push | pop ] [, identifier ] ] )  
```  
  
### <a name="parameters"></a>参数  
*name*  
指定要修改的编译器选项的名称。 唯一有效*名称*是`forScope`。  
  
*显示*（可选）  
当前设置将导致*名称*（true 或 false） 在编译期间显示通过一条警告消息。 例如 `#pragma conform(forScope, show)`。  
  
*on、 off*（可选）  
设置*名称*到*上*使[/zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)编译器选项。 默认值是*关闭*。  
  
*推送*（可选）  
将当前值推送*名称*到内部编译器堆栈上。 如果指定*标识符*，可以指定*上*或*关闭*值*名称*可以被推送到堆栈上。 例如 `#pragma conform(forScope, push, myname, on)`。  
  
*pop* （可选）  
设置的值*名称*到内部编译器堆栈和弹出堆栈的顶部的值。 如果具有指定标识符*pop*，堆栈将弹回，直到它找到的记录*标识符*，这也会弹出; 的当前值*名称*中在堆栈上的下一个记录成为的新值*名称*。 如果指定使用 pop*标识符*的不是在堆栈上的记录*pop*将被忽略。  
  
*标识符*（可选）  
可随附*推送*或*pop*命令。 如果*标识符*使用，则*上*或*关闭*还可以使用说明符。  
  
## <a name="example"></a>示例  
  
```cpp  
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