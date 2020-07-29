---
title: 省略号和可变参数模板
ms.date: 11/04/2016
ms.assetid: f20967d9-c967-4fd2-b902-2bb1d5ed87e3
ms.openlocfilehash: e916dac40355f4397ef4846c0edf568c60b7d3dd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221622"
---
# <a name="ellipsis-and-variadic-templates"></a>省略号和可变参数模板

本文介绍如何使用 `...` 带有 c + + 可变参数模板的省略号（）。 省略号在 C 和 c + + 中具有许多用途。 其中包括函数的变量参数列表。 `printf()`C 运行时库中的函数是一个最常见的示例。

*可变参数模板*是支持任意数量的参数的类或函数模板。 此机制对 c + + 库开发人员特别有用，因为您可以将其应用于类模板和函数模板，从而提供各种类型安全且不重要的功能和灵活性。

## <a name="syntax"></a>语法

可变参数模板通过两种方式使用省略号。 参数名称的左侧表示*参数包*，参数名称的右侧将参数包扩展为多个单独的名称。

下面是*可变参数模板类*定义语法的基本示例：

```cpp
template<typename... Arguments> class classname;
```

对于参数包和扩展，您可根据您的偏好在省略号周围添加空白，如以下这些示例所示：

```cpp
template<typename ...Arguments> class classname;
```

或者这个：

```cpp
template<typename ... Arguments> class classname;
```

请注意，本文使用第一个示例中显示的约定（省略号连接到 **`typename`** ）。

在前面的示例中，*参数*是参数包。 类 `classname` 可以接受数量可变的自变量，如以下示例中所示：

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
vtclass<long, std::vector<int>, std::string> vtinstance4;
```

使用可变参数模板类定义时，还可以至少要求一个参数：

```cpp
template <typename First, typename... Rest> class classname;
```

下面是*可变参数模板函数*语法的基本示例：

```cpp
template <typename... Arguments> returntype functionname(Arguments... args);
```

然后，将*扩展参数包*以供使用，如下一节 "**了解可变参数模板**" 中所示。

可以采用其他形式的可变参数模板函数语法，包括但不限于以下示例：

```cpp
template <typename... Arguments> returntype functionname(Arguments&... args);
template <typename... Arguments> returntype functionname(Arguments&&... args);
template <typename... Arguments> returntype functionname(Arguments*... args);
```

**`const`** 还允许使用类似的说明符：

```cpp
template <typename... Arguments> returntype functionname(const Arguments&... args);
```

与可变参数模板类定义一样，您可以创建需要至少一个参数的函数：

```cpp
template <typename First, typename... Rest> returntype functionname(const First& first, const Rest&... args);
```

可变参数模板使用 `sizeof...()` 运算符（与较旧的 `sizeof()` 运算符无关）：

```cpp
template<typename... Arguments>
void tfunc(const Arguments&... args)
{
    constexpr auto numargs{ sizeof...(Arguments) };

    X xobj[numargs]; // array of some previously defined type X

    helper_func(xobj, args...);
}
```

## <a name="more-about-ellipsis-placement"></a>有关省略号位置的更多信息

之前，本文介绍了省略号位置，此位置将参数包和扩展定义为“参数名称的左侧表示参数包，参数名称的右侧将参数包扩展为单独的名称”。 这从技术上讲的确如此，但在转换为代码的过程中可能会造成混淆。 请注意以下几点：

- 在模板参数列表（ `template <parameter-list>` ）中 `typename...` 引入了一个模板参数包。

- 在参数声明子句（ `func(parameter-list)` ）中，"顶级" 省略号引入函数参数包，并且省略号定位非常重要：

    ```cpp
    // v1 is NOT a function parameter pack:
    template <typename... Types> void func1(std::vector<Types...> v1);

    // v2 IS a function parameter pack:
    template <typename... Types> void func2(std::vector<Types>... v2);
    ```

- 其中省略号显示在参数名称的后面，并且您具有一个参数包扩展。

## <a name="example"></a>示例

说明可变参数模板函数机制的一个好方法是在重新编写的某些功能时使用它 `printf` ：

```cpp
#include <iostream>

using namespace std;

void print() {
    cout << endl;
}

template <typename T> void print(const T& t) {
    cout << t << endl;
}

template <typename First, typename... Rest> void print(const First& first, const Rest&... rest) {
    cout << first << ", ";
    print(rest...); // recursive call using pack expansion syntax
}

int main()
{
    print(); // calls first overload, outputting only a newline
    print(1); // calls second overload

    // these call the third overload, the variadic template,
    // which uses recursion as needed.
    print(10, 20);
    print(100, 200, 300);
    print("first", 2, "third", 3.14159);
}
```

## <a name="output"></a>输出

```Output
1
10, 20
100, 200, 300
first, 2, third, 3.14159
```

> [!NOTE]
> 大多数包含可变参数模板函数的实现使用某种形式的递归，但与传统递归略有不同。  传统递归涉及使用同一签名调用自身的函数。 （它可以是重载的或模板化的，但每次都选择相同的签名。）可变参数递归涉及到使用不同的（几乎始终减少）参数调用可变参数函数模板，从而每次都能标记出不同的签名。 仍需要 "基本情况"，但递归的性质是不同的。
