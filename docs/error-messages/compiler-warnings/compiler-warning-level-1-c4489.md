---
title: 编译器警告 （等级 1） C4489 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4489
dev_langs:
- C++
helpviewer_keywords:
- C4489
ms.assetid: 43b51c8c-27b5-44c9-b974-fe4b48f4896f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc019c618a5e4b8a453652573f6f407279792d56
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023249"
---
# <a name="compiler-warning-level-1-c4489"></a>编译器警告（等级 1）C4489

specifier： 不允许在接口方法 method;重写说明符只允许在 ref 类和值类方法

在接口方法不正确使用说明符关键字。

有关详细信息，请参阅[重写说明符](../../windows/override-specifiers-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C4489。

```
// C4489.cpp
// compile with: /clr /c /W1
public interface class I {
   void f() new;   // C4489
   virtual void b() override;   // C4489

   void g();   // OK
};
```