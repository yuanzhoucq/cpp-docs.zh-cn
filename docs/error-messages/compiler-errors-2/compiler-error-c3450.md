---
title: "编译器错误 C3450 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3450
dev_langs:
- C++
helpviewer_keywords:
- C3450
ms.assetid: 78892cf7-0b82-4589-90d0-e06666247003
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 90aa45cc810f8a0d7f869484216a28ea80eaf602
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3450"></a>编译器错误 C3450
“type”：不是特性；不能指定 [System::AttributeUsageAttribute] 或 [Windows::Foundation::Metadata::AttributeUsageAttribute]  
  
 用户定义的托管特性必须继承自 <xref:System.ComponentModel.AttributeCollection.%23ctor%2A>。 Windows 运行时特性必须在 `Windows::Foundation::Metadata` 命名空间中定义。  
  
 有关详细信息，请参阅 [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md)。  
  
## <a name="example"></a>示例  
 下面的示例将生成 C3450，并演示如何修复此错误。  
  
```  
// C3450.cpp  
// compile with: /clr  
// C3450 expected  
using namespace System;  
using namespace System::Security;  
using namespace System::Security::Permissions;  
  
public ref class MyClass {};  
  
class MyClass2 {};  
  
[attribute(AttributeTargets::All)]  
ref struct AtClass {  
   AtClass(Type ^) {}  
};  
  
[attribute(AttributeTargets::All)]  
ref struct AtClass2 {  
   AtClass2() {}  
};  
  
// Apply the AtClass and AtClass2 attributes to class B  
[AtClass(MyClass::typeid), AtClass2]     
[AttributeUsage(AttributeTargets::All)]  
// Delete the following line to resolve.  
ref class B {};  
// Uncomment the following line to resolve.  
// ref class B : Attribute {};  
```
