---
title: "编译器错误 C3451 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3451
dev_langs:
- C++
helpviewer_keywords:
- C3451
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: c1c0f9de919fbe646eaa6303fa5b1e9fcba886eb
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3451"></a>编译器错误 C3451
attribute： 无法将应用非托管的属性 type  
  
 C + + 特性不能应用于 CLR 类型。 请参阅[c + + 特性参考](../../windows/cpp-attributes-reference.md)有关详细信息。  
  
 有关详细信息，请参阅 [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md)。  
  
 此错误可能来自于为 Visual c + + 2005年执行的编译器一致性工作： [uuid](../../windows/uuid-cpp-attributes.md)属性不再允许在使用 CLR 编程的用户定义的特性。 请改用 <xref:System.Runtime.InteropServices.GuidAttribute> 。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3451。  
  
```  
// C3451.cpp  
// compile with: /clr /c  
using namespace System;  
[ attribute(AttributeTargets::All) ]  
public ref struct MyAttr {};  
  
[ MyAttr, helpstring("test") ]   // C3451  
// try the following line instead  
// [ MyAttr ]  
public ref struct ABC {};  
```
