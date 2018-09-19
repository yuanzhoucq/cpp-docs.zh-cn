---
title: 编译器警告 （等级 3） C4637 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4637
dev_langs:
- C++
helpviewer_keywords:
- C4637
ms.assetid: 5fd347c1-2de9-408f-9136-1bf1ff273622
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 094182dd0e438a89ce3652130b411ab1ca1a0bd1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111779"
---
# <a name="compiler-warning-level-3-c4637"></a>编译器警告（等级 3）C4637

XML 文档注释目标：\<包括 > 标记被丢弃。  原因

语法[\<包括 >](../../ide/include-visual-cpp.md)标记的不正确。

下面的示例生成 C4637：

```
// C4637.cpp
// compile with: /clr /doc /LD /W3
using namespace System;

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <include file="c:\davedata\jtest\xml_include.doc"/>
   // Try the following line instead:
   // /// <include file='xml_include.doc' path='MyDocs/MyMembers/*' />
   void MyMethod() {
   }
};   // C4637
```