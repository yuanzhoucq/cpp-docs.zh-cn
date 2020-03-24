---
title: 编译器警告（等级 1）C4376
ms.date: 11/04/2016
f1_keywords:
- C4376
helpviewer_keywords:
- C4376
ms.assetid: 5f202c74-9489-48fe-b36f-19cd882b1589
ms.openlocfilehash: 8009d2e5d09ad173f6150ebe9a907be9f4947cd7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162851"
---
# <a name="compiler-warning-level-1-c4376"></a>编译器警告（等级 1）C4376

不再支持访问说明符 "old_specifier："：请改用 "new_specifier："

有关在元数据中指定类型和成员可访问性的详细信息，请参阅[如何：定义和使用类和结构（C++/cli）](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)中的[类型可见性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)和[成员可见性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility)。

## <a name="example"></a>示例

下面的示例生成 C4376。

```cpp
// C4376.cpp
// compile with: /clr /W1 /c
public ref class G {
public public:   // C4376
   void m2();
};

public ref class H {
public:   // OK
   void m2();
};
```
