---
title: 编译器警告（等级 1）C4489
ms.date: 11/04/2016
f1_keywords:
- C4489
helpviewer_keywords:
- C4489
ms.assetid: 43b51c8c-27b5-44c9-b974-fe4b48f4896f
ms.openlocfilehash: dd150621ad3474444861982c095ae8a6addb52fa
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779201"
---
# <a name="compiler-warning-level-1-c4489"></a>编译器警告（等级 1）C4489

specifier： 不允许在接口方法 method;重写说明符只允许在 ref 类和值类方法

在接口方法不正确使用说明符关键字。

有关详细信息，请参阅[重写说明符](../../extensions/override-specifiers-cpp-component-extensions.md)。

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