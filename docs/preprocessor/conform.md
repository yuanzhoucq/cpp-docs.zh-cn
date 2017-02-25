---
title: "conform | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "conform_CPP"
  - "vc-pragma.conform"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "符合杂注"
  - "forScope 符合杂注"
  - "杂注, 符合"
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# conform
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 专用**  
  
 指定 [\/Zc:forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) 编译器选项的运行时行为。  
  
## 语法  
  
```  
#pragma conform(name [, show ] [, on | off ] [ [, push | pop ] [, identifier ] ] )  
```  
  
#### 参数  
 *name*  
 指定要修改的编译器选项的名称。  唯一有效的 *name* 为 `forScope`。  
  
 **show**（可选）  
 导致 *name* 的当前设置（true 或 false）在编译期间以警告消息的方式显示。  例如 `#pragma conform(forScope, show)`。  
  
 **on、off**（可选）  
 将 *name* 设置为 **on** 将启用 [\/Zc:forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) 编译器选项。  默认值为 **off**。  
  
 **push**（可选）  
 将 *name* 的当前值推送到内部编译器堆栈。  如果您指定 *identifier*，则可为要推送到堆栈的 *name* 指定 **on** 或 **off** 值。  例如 `#pragma conform(forScope, push, myname, on)`。  
  
 **pop**（可选）  
 将 *name* 的值设置为位于内部编译器堆栈顶部的值，然后弹出堆栈。  如果使用 **pop** 指定 identifier，则堆栈将弹回，直到它找到具有 *identifier* 的记录（也会弹出）；堆栈上的下一记录中的 *name* 的当前值将变为 *name* 的新值。  如果使用不在堆栈上的记录中的 *identifier* 指定 pop，则将忽略 **pop**。  
  
 *identifier*（可选）  
 可以与 **push** 或 **pop** 命令包含在一起。  如果使用了 *identifier*，则还可以使用 **on** 或 **off** 说明符。  
  
## 示例  
  
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
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)