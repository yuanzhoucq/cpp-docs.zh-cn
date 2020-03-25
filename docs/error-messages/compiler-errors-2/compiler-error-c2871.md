---
title: 编译器错误 C2871
ms.date: 11/04/2016
f1_keywords:
- C2871
helpviewer_keywords:
- C2871
ms.assetid: 44aeb84d-61f0-45e0-8dad-22a3cd46b7f8
ms.openlocfilehash: cc24e5fefe9ffd67dc6b01520ea32805a22f70c3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201677"
---
# <a name="compiler-error-c2871"></a>编译器错误 C2871

"name"：不存在具有此名称的命名空间

当你将不是命名空间的标识符传递给[using](../../cpp/namespaces-cpp.md#using_directives)指令时，将发生此错误。

## <a name="example"></a>示例

下面的示例生成 C2871：

```cpp
// C2871.cpp
// compile with: /c
namespace a {
   int fn(int i) { return i; }
}
namespace b {
   using namespace d;   // C2871 because d is not a namespace
   using namespace a;   // OK
}
```
