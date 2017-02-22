---
title: "编译器警告（等级 4）C4435 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
dev_langs: 
  - "C++"
ms.assetid: a04524af-2b71-4ff9-9729-d9d1d1904ed7
caps.latest.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 2
---
# 编译器警告（等级 4）C4435
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class1”: \/vd2 下的对象布局将因虚拟基“class2”而更改  
  
 默认情况下关闭此警告。  有关更多信息，请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 默认在中编译的 \/vd1 选项，派生类没有指示虚拟基的 `vtordisp` 字段。如果 \/vd2 或 `#pragma vtordisp(2)` 实际上是，`vtordisp` 字段将存在，更改对象布局。如果交互的模块编译具有不同的 `vtordisp` 设置，这可能导致二进制兼容性问题。  
  
## 示例  
 下面的示例生成 C4435。  
  
```cpp  
// C4435.cpp  
// compile with: /c /W4  
#pragma warning(default : 4435)  
class A  
{  
public:  
    virtual ~A() {}  
};  
  
class B : public virtual A  // C4435  
{};  
```  
  
## 请参阅  
 [vtordisp](../../preprocessor/vtordisp.md)   
 [\/vd（禁用构造置换）](../../build/reference/vd-disable-construction-displacements.md)