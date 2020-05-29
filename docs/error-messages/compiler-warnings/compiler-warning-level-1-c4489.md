---
title: 编译器警告（等级 1）C4489
ms.date: 11/04/2016
f1_keywords:
- C4489
helpviewer_keywords:
- C4489
ms.assetid: 43b51c8c-27b5-44c9-b974-fe4b48f4896f
ms.openlocfilehash: e9811e9f9c17463fdcd550ffd82af4f81a40bb34
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186603"
---
# <a name="compiler-warning-level-1-c4489"></a>编译器警告（等级 1）C4489

"说明符"：不允许在接口方法 "method" 上使用;重写说明符只允许在 ref 类和值类方法上使用

在接口方法上错误地使用了说明符关键字。

有关详细信息，请参阅[重写说明符](../../extensions/override-specifiers-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C4489。

```cpp
// C4489.cpp
// compile with: /clr /c /W1
public interface class I {
   void f() new;   // C4489
   virtual void b() override;   // C4489

   void g();   // OK
};
```
