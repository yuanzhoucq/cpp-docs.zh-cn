---
title: "vtordisp | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.vtordisp"
  - "vtordisp_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "杂注, vtordisp"
  - "vtordisp 杂注"
ms.assetid: 05b7d73c-43fa-4b62-8c8a-170a9e427391
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# vtordisp
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 专用**  
  
 控制隐藏的 vtordisp 构造函数\/析构函数置换成员的添加。  
  
## 语法  
  
```cpp  
#pragma vtordisp([push,] n)  
#pragma vtordisp(pop)  
#pragma vtordisp()  
#pragma vtordisp([push,] {on | off})  
```  
  
#### 参数  
 `push`  
 推送内部编译器堆栈上的当前 vtordisp 设置并将新 vtordisp 设置为 `n`。如果 `n` 未指定，则不会更改当前 vtordisp 设置。  
  
 `pop`  
 从内部编译器堆栈中移除顶部的记录并将 vtordisp 设置还原为已移除的值。  
  
 `n`  
 为 vtordisp 设置指定新值。  可能的值为 0、1 或 2，分别对应于 \/vd0、\/vd1 和 \/vd2 编译器选项。  有关详细信息，请参阅[\/vd（禁用构造置换）](../build/reference/vd-disable-construction-displacements.md)。  
  
 `on`  
 等效于 `#pragma vtordisp(1)`。  
  
 `off`  
 等效于 `#pragma vtordisp(0)`。  
  
## 备注  
 `vtordisp` 杂注仅适用于使用虚拟基的代码。  如果派生类重写它从虚拟基类继承的虚函数，并且派生类的构造函数或析构函数使用指向该虚拟基类的指针调用该函数，则编译器可能将其他隐藏的 `vtordisp` 字段引入具有虚拟基的类。  
  
 `vtordisp` 杂注影响它后面的类的布局。  \/vd0、\/vd1 和 \/vd2 选项为整个模块指定相同行为。  指定 `0` 或 `off` 将取消显示隐藏的 `vtordisp` 成员。  仅当类的构造函数和析构函数调用由 `this` 指针指向的对象上的虚函数时才关闭 `vtordisp`。  
  
 指定 `1` 或 `on`（默认值）将在必要时启用隐藏的 `vtordisp` 成员。  
  
 指定 `2` 将为所有具有虚函数的虚拟基启用隐藏 `vtordisp` 成员。可能需要 `vtordisp(2)` 以确保 `dynamic_cast` 在部分构造的对象上正常工作。  有关详细信息，请参阅[编译器警告（等级 1）C4436](../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)。  
  
 `#pragma vtordisp()`（没有参数）可将 vtordisp 设置还原到其初始设置。  
  
```  
#pragma vtordisp(push, 2)  
class GetReal : virtual public VBase { ... };  
#pragma vtordisp(pop)  
```  
  
 **结束 C\+\+ 专用**  
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)