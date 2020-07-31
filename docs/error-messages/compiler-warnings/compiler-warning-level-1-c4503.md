---
title: 编译器警告（等级 1）C4503
ms.date: 05/14/2018
f1_keywords:
- C4503
helpviewer_keywords:
- C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
ms.openlocfilehash: 1d3af2b5629906679db46f6f669084c11a41f7ca
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233244"
---
# <a name="compiler-warning-level-1-c4503"></a>编译器警告（等级 1）C4503

> "*identifier*"：超出修饰名的长度，名称被截断

## <a name="remarks"></a>备注

此编译器警告已过时，并且不会在 Visual Studio 2017 和更高版本的编译器中生成。

修饰名的长度超过编译器限制（4096），已被截断。 若要避免此警告和截断，请减少参数的数量或使用的标识符的名称长度。 比编译器限制更长的修饰名应用了哈希，并且不存在名称冲突的危险。

当使用较旧版本的 Visual Studio 时，如果您的代码重复包含在模板上专用化的模板，则可以发出此警告。 例如，映射（来自 c + + 标准库）的映射。 在这种情况下，你可以将你的 typedef 设置为（ **`struct`** 例如）包含该映射的类型。

但是，你可能决定不重构你的代码。  可以提供生成 C4503 的应用程序，但如果在截断的符号上收到链接时间错误，则很难确定错误中的符号类型。 调试也可能更困难;调试器可能就越大将符号名称映射到类型名称。 但是，程序的正确性不受截断名称的影响。

## <a name="example"></a>示例

下面的示例在 Visual Studio 2017 之前的编译器中生成 C4503：

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

此示例演示重写代码以解析 C4503 的一种方法：

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
