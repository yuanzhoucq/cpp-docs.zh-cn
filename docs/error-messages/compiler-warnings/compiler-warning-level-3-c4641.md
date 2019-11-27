---
title: 编译器警告（等级 3）C4641
ms.date: 11/04/2016
f1_keywords:
- C4641
helpviewer_keywords:
- C4641
ms.assetid: 28fe5c3e-6039-42da-9100-1312b5b15aea
ms.openlocfilehash: 0a930490f7b53fbbb31abb0f621cf972295d2ea6
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2019
ms.locfileid: "74189428"
---
# <a name="compiler-warning-level-3-c4641"></a>编译器警告（等级 3）C4641

XML 文档注释含有不明确的交叉引用。

编译器无法明确解析引用。 若要解决此警告，请指定使引用明确所需的参数信息。

有关更多信息，请参见 [XML Documentation](../../build/reference/xml-documentation-visual-cpp.md)。

## <a name="example"></a>示例

下面的示例生成 C4641。

```cpp
// C4641.cpp
// compile with: /W3 /doc /clr /c

/// <see cref="f" />   // C4641
// try the following line instead
// /// <see cref="f(int)" />
public ref class GR {
public:
   void f( int ) {}
   void f( char ) {}
};
```