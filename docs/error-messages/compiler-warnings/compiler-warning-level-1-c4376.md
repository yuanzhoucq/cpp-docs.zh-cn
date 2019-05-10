---
title: 编译器警告（等级 1）C4376
ms.date: 11/04/2016
f1_keywords:
- C4376
helpviewer_keywords:
- C4376
ms.assetid: 5f202c74-9489-48fe-b36f-19cd882b1589
ms.openlocfilehash: b1f6e7b403931f7fe1a67974ae85001cf80eab66
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410417"
---
# <a name="compiler-warning-level-1-c4376"></a>编译器警告（等级 1）C4376

访问说明符 old_specifier: 不再受支持： 请使用 new_specifier: 改为

在元数据中指定类型和成员可访问性的详细信息，请参阅[键入可见性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)并[成员的可见性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility)中[如何：定义和使用类和结构 (C++/CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)。

## <a name="example"></a>示例

下面的示例生成 C4376。

```
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