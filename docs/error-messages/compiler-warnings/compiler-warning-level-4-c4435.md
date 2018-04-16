---
title: "编译器警告 （等级 4） C4435 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: a04524af-2b71-4ff9-9729-d9d1d1904ed7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7136cfb61a7452b7e835030216d08f064874df8b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4435"></a>编译器警告（等级 4）C4435
“class1”: /vd2 下的对象布局将因虚拟基“class2”而更改  
  
 默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。  
  
 在 /vd1 的默认编译选项下，派生类没有指示的虚拟基的 `vtordisp` 字段。  如果 /vd2 或 `#pragma vtordisp(2)` 有效，`vtordisp` 字段将存在，并更改对象布局。  如果使用不同的 `vtordisp` 设置编译交互的模块，这可能导致二进制兼容性问题。  
  
## <a name="example"></a>示例  
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
  
## <a name="see-also"></a>请参阅  
 [vtordisp](../../preprocessor/vtordisp.md)   
 [/vd （禁用构造置换）](../../build/reference/vd-disable-construction-displacements.md)