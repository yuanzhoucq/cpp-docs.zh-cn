---
title: enable_if 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::enable_if
helpviewer_keywords:
- enable_if class
- enable_if
ms.assetid: c6b8d41c-a18f-4e30-a39e-b3aa0e8fd926
ms.openlocfilehash: 1017fc315a4440350a0190cf4b40e644cda16876
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230034"
---
# <a name="enable_if-class"></a>enable_if 类

有条件地为 SFINAE 重载决策设置类型的实例。 `enable_if<Condition,Type>::type` `Type` 当且仅当是时，嵌套的 typedef 才存在（并且是的同义词） `Condition` **`true`** 。

## <a name="syntax"></a>语法

```cpp
template <bool B, class T = void>
struct enable_if;
```

### <a name="parameters"></a>参数

*B*\
确定存在产生的类型的值。

*关心*\
*B*为 true 时要实例化的类型。

## <a name="remarks"></a>备注

如果*B*为 true，则 `enable_if<B, T>` 具有名为 "type" 的嵌套 typedef，它是*T*的同义词。

如果*B*为 false，则 `enable_if<B, T>` 不具有名为 "type" 的嵌套 typedef。

提供此别名模板：

```cpp
template <bool B, class T = void>
using enable_if_t = typename enable_if<B,T>::type;
```

在 C++ 中，模板参数的替换失败不是其本身的错误，这称为 *SFINAE*（替换失败不是错误）。 通常，`enable_if` 用于从重载决策中删除候选项（即剔除重载集），以便为了支持一个定义而拒绝另一个定义。 这符合 SFINAE 行为。 有关 SFINAE 的详细信息，请参阅 Wikipedia 上的[替换失败不是错误](https://go.microsoft.com/fwlink/p/?linkid=394798)。

以下是四种示例方案：

- 方案 1：包装函数的返回类型：

```cpp
    template <your_stuff>
typename enable_if<your_condition, your_return_type>::type
    yourfunction(args) {// ...
}
// The alias template makes it more concise:
    template <your_stuff>
enable_if_t<your_condition, your_return_type>
yourfunction(args) {// ...
}
```

- 方案 2：添加具有默认参数的函数参数：

```cpp
    template <your_stuff>
your_return_type_if_present
    yourfunction(args, enable_if_t<your condition, FOO> = BAR) {// ...
}
```

- 方案 3：添加具有默认参数的模板参数：

```cpp
    template <your_stuff, typename Dummy = enable_if_t<your_condition>>
rest_of_function_declaration_goes_here
```

- 方案 4：如果你的函数具有非模板化的参数，你可以包装其类型：

```cpp
    template <typename T>
void your_function(const T& t,
    enable_if_t<is_something<T>::value, const string&>
s) {// ...
}
```

方案 1 不能使用构造函数和转换运算符，因为它们没有返回类型。

方案 2 可使参数处于未命名状态。 你可以假定 `::type Dummy = BAR`，但与名称 `Dummy` 无关，而且向其提供一个名称很可能会触发“未引用的参数”警告。 你必须选择 `FOO` 函数参数类型和 `BAR` 默认参数。  你可以说 **`int`** 和 `0` ，但随后你的代码用户可能会意外地将忽略的额外整数传递给函数。 相反，我们建议你使用 `void **` 和或， `0` **`nullptr`** 因为几乎不能转换为 `void **` ：

```cpp
template <your_stuff>
your_return_type_if_present
yourfunction(args, typename enable_if<your_condition, void **>::type = nullptr) {// ...
}
```

方案 2 也适用于普通构造函数。  但是，它不适用于转换运算符，因为它们无法采用多余的参数。  它也不适用于 [variadic](../cpp/ellipses-and-variadic-templates.md) 构造函数，因为添加多余的参数会使函数参数打包非导出上下文，从而与使用 `enable_if` 的初衷背道而驰。

方案 3 可使用名称 `Dummy`，但是它是可选的。 仅“`typename = typename`”可用，但是如果你认为它看起来太怪异，则可以使用“虚拟”名，只是不要使用还可能会在函数定义中使用的名称。 如果你未向 `enable_if` 提供类型，则它默认为 void，这是完全合理的，因为你不在乎 `Dummy` 的具体内容。 这适用于所有情况，包括转换运算符和 [variadic](../cpp/ellipses-and-variadic-templates.md) 构造函数。

方案 4 在不具有返回类型的构造函数中可用，因此可解决方案 1 的包装限制问题。  但是，方案 4 受限于并非始终可用的非模板化的函数参数。  （在模板化的函数参数上使用方案 4 可以阻止模板参数导入在其上运行。）

`enable_if` 功能强大，但是如果误用也会很危险。  因为其用途是使候选项在重载决策之前消失，如果误用它，产生的结果可能很容易让人产生混淆。  以下是一些建议：

- 编译时，请不要使用 `enable_if` 在实现之间作出选择。 请永远都不要为 `enable_if` 编写一个 `CONDITION` 并为 `!CONDITION` 编写另一个 enable_if。  请改为使用*标记调度*模式，例如，一种根据所提供的迭代器的优点选择实现的算法。

- 请不要使用 `enable_if` 强制执行要求。  如果要验证模板参数，并且如果验证失败，引发错误，而未选择其他实现，请使用 [static_assert](../cpp/static-assert.md)。

- 如果你拥有会使其他好的代码变得不明确的重载集，则请使用 `enable_if`。  通常，这种情况发生在隐式转换构造函数中。

## <a name="example"></a>示例

此示例说明了 C++ 标准库模板函数 [std::make_pair()](../standard-library/utility-functions.md#make_pair) 如何利用 `enable_if`。

```cpp
void func(const pair<int, int>&);

void func(const pair<string, string>&);

func(make_pair("foo", "bar"));
```

在本示例中，`make_pair("foo", "bar")` 将返回 `pair<const char *, const char *>`。 重载决策必须确定你想要的 `func()`。 `pair<A, B>` 具有 `pair<X, Y>` 中的隐式转换构造函数。  这不是新内容，它在 C++98 中出现过。 但是，在 C++98/03 中，隐式转换构造函数的签名始终存在，即使它是 `pair<int, int>(const pair<const char *, const char *>&)` 也是如此。  重载决策不会注意到，尝试实例化该构造函数会发生可怕，因为 `const char *` 它不能隐式转换为 **`int`** ; 它仅在对函数定义进行实例化之前查看签名。  因此，示例代码是不明确的，因为存在可将 `pair<const char *, const char *>` 转换为 `pair<int, int>` 和 `pair<string, string>` 的签名。

C++11 通过使用 `enable_if` 确保**仅**当 `const X&` 可隐式转换为 `A` 且 `const Y&` 可隐式转换为 `B` 时 `pair<A, B>(const pair<X, Y>&)` 才存在，来解决此多义性问题。  这允许重载决策确定 `pair<const char *, const char *>` 不可转换为 `pair<int, int>`，以及采用 `pair<string, string>` 的重载可行。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>另请参阅

[<type_traits>](../standard-library/type-traits.md)
