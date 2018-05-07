---
title: 编译器错误 C3451 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3451
dev_langs:
- C++
helpviewer_keywords:
- C3451
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a8aa09f0eb38364179be1608c3f230fe8059509
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3451"></a>编译器错误 C3451
attribute： 无法将应用非托管的属性 type  
  
 C + + 特性不能应用于 CLR 类型。 请参阅[c + + 特性参考](../../windows/cpp-attributes-reference.md)有关详细信息。  
  
 有关详细信息，请参阅 [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md)。  
  
 此错误可能来自于为 Visual c + + 2005年执行的编译器一致性工作： [uuid](../../windows/uuid-cpp-attributes.md)属性不再允许在使用 CLR 编程的用户定义的特性。 请改用 <xref:System.Runtime.InteropServices.GuidAttribute>。  
  
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