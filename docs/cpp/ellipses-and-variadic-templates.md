---
title: 省略号和可变参数模板
ms.date: 11/04/2016
ms.assetid: f20967d9-c967-4fd2-b902-2bb1d5ed87e3
ms.openlocfilehash: 358cdeeaf6f3e8c7f7841bbc796eca6557ccd145
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366340"
---
# <a name="ellipses-and-variadic-templates"></a>省略号和可变参数模板

本文演示如何将省略号 （）`...`与C++可变模板一起使用. 椭圆在C和C++中有许多用途。 其中包括函数的变量参数列表。 C`printf()`运行时库中的函数是最广为人知的示例之一。

*可变模板*是支持任意数量的参数的类或函数模板。 此机制对于C++库开发人员特别有用，因为您可以将其应用于类模板和函数模板，从而提供广泛的类型安全和非普通功能和灵活性。

## <a name="syntax"></a>语法

杂音模板以两种方式使用省略号。 在参数名称的左侧，它表示*参数包*，在参数名称的右侧，它将参数包扩展到单独的名称中。

下面是*可变模板类*定义语法的基本示例：

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

请注意，本文使用第一个示例中显示的约定（省略号已附加到 `typename`）。

在前面的示例中，*参数*是参数包。 类`classname`可以接受可变数量的参数，如以下示例所示：

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
vtclass<long, std::vector<int>, std::string> vtinstance4;
```

通过使用可变模板类定义，还可以至少需要一个参数：

```cpp
template <typename First, typename... Rest> class classname;
```

下面是*可变模板函数*语法的基本示例：

```cpp
template <typename... Arguments> returntype functionname(Arguments... args);
```

然后展开*参数*包以使用，如下一节"**理解可变模板"中**所示。

其他形式的可变模板函数语法是可能的， 包括但不限于这些示例：

```cpp
template <typename... Arguments> returntype functionname(Arguments&... args);
template <typename... Arguments> returntype functionname(Arguments&&... args);
template <typename... Arguments> returntype functionname(Arguments*... args);
```

也允许像**康斯特**这样的指定者：

```cpp
template <typename... Arguments> returntype functionname(const Arguments&... args);
```

与可变模板类定义一样，您可以生成至少需要一个参数的函数：

```cpp
template <typename First, typename... Rest> returntype functionname(const First& first, const Rest&... args);
```

可变模板使用`sizeof...()`运算符（与较旧的`sizeof()`运算符无关）：

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

之前，本文介绍了省略号位置，此位置将参数包和扩展定义为“参数名称的左侧表示参数包，参数名称的右侧将参数包扩展为单独的名称”。 这从技术上讲的确如此，但在转换为代码的过程中可能会造成混淆。 请考虑：

- 在模板参数列表 （）`template <parameter-list>``typename...`中引入了模板参数包。

- 在参数声明子句 （）`func(parameter-list)`中，"顶级"椭圆引入函数参数包，省略号定位很重要：

    ```cpp
    // v1 is NOT a function parameter pack:
    template <typename... Types> void func1(std::vector<Types...> v1);

    // v2 IS a function parameter pack:
    template <typename... Types> void func2(std::vector<Types>... v2);
    ```

- 其中省略号显示在参数名称的后面，并且您具有一个参数包扩展。

## <a name="example"></a>示例

说明可变模板函数机制的一个好方法是在重写`printf`： 的一些功能时使用它：

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
> 大多数包含可变模板函数的实现使用某种形式的递归，但它与传统递归略有不同。  传统的递归涉及使用同一签名调用自己的函数。 （它可能重载或模板化，但每次都选择相同的签名。变幻性递归涉及使用不同（几乎总是减少）参数数调用变量函数模板，从而每次标记出不同的签名。 仍然需要"基本情况"，但递归的性质不同。
