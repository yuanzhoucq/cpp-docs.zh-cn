---
title: 编译器警告 （等级 1） C4503 |Microsoft 文档
ms.custom: ''
ms.date: 05/14/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4503
dev_langs:
- C++
helpviewer_keywords:
- C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f60fdb44c5368ccc5c5f089002614332d95a63fe
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34255669"
---
# <a name="compiler-warning-level-1-c4503"></a>编译器警告（等级 1）C4503

> *标识符*： 修饰名的长度超出，名称已被截断

## <a name="remarks"></a>备注

此编译器警告已过时，并在 Visual Studio 2017 和更高版本的编译器不生成。

修饰的名的长度超出编译器限制 (4096)，已被截断。 若要避免此警告和截断，减少参数的数目或使用标识符的名称长度。 修饰名超过编译器限制具有应用哈希并不处于存在名称冲突的风险。

如果代码中包含模板时使用较旧版本的 Visual Studio，可以发出此警告重复上模板专用化。 例如，映射 （从 c + + 标准库） 的映射。 在此情况下，你可以使你 typedef 类型 (**结构**，例如) 包含的映射。

但是，你可能会决定不重构你的代码。  可以提供的应用程序生成 C4503，但如果在上截断符号链接时错误，它会更加困难，以确定错误中的符号的类型。 调试可能还会更加困难;调试器可能有难度就越大将符号名称映射为类型名称。 正确的程序，但是，不受截断的名称。

## <a name="example"></a>示例

下面的示例生成 C4503 在 Visual Studio 2017 之前的编译器中：

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

此示例演示一种方法重写你的代码以解决 c4503 的方法：

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