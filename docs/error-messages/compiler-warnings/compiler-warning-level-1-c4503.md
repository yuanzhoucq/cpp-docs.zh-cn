---
title: 编译器警告（等级 1）C4503
ms.date: 05/14/2018
f1_keywords:
- C4503
helpviewer_keywords:
- C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
ms.openlocfilehash: 94c88511d87c3adf3cf5687a94948c83ebc5b3d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160973"
---
# <a name="compiler-warning-level-1-c4503"></a>编译器警告（等级 1）C4503

> '*标识符*： 修饰名的长度超过，名称已被截断

## <a name="remarks"></a>备注

这一编译器警告已过时，不在 Visual Studio 2017 和更高版本的编译器中生成。

修饰的名的长度超出编译器限制 (4096)，已被截断。 若要避免此警告和截断，减少参数的数目或使用的标识符的名称长度。 修饰名超过编译器限制具有哈希应用并不处于名称冲突的危险。

当你的代码包含模板时使用较旧版本的 Visual Studio，可以发出此警告重复上模板专用化。 例如，映射的映射 (从C++标准库)。 在这种情况下，您可以使您 typedef 类型 (**结构**，例如)，其中包含该映射。

但是，您可能决定不重构你的代码。  可以发布的应用程序生成 C4503，但如果截断符号上遇到链接时错误，它可以是更难以确定中错误的符号的类型。 调试可能还会更加困难;调试器可能无法映射到的类型名称的符号名称。 正确性的程序，但是，不受被截断的名称。

## <a name="example"></a>示例

下面的示例在 Visual Studio 2017 之前的编译器生成 C4503:

```cpp
// C4503.cpp
// compile with: /W1 /EHsc /c
// C4503 expected
#include <string>
#include <map>

class Field{};

typedef std::map<std::string, Field> Screen;
typedef std::map<std::string, Screen> WebApp;
typedef std::map<std::string, WebApp> WebAppTest;
typedef std::map<std::string, WebAppTest> Hello;
Hello MyWAT;
```

此示例显示了一种方法重写代码来解决 c4503 的方法：

```cpp
// C4503b.cpp
// compile with: /W1 /EHsc /c
#include <string>
#include <map>

class Field{};

struct Screen2 {
   std::map<std::string, Field> Element;
};

struct WebApp2 {
   std::map<std::string, Screen2> Element;
};

struct WebAppTest2 {
   std::map<std::string, WebApp2> Element;
};

struct Hello2 {
   std::map<std::string, WebAppTest2> Element;
};

Hello2 MyWAT2;
```