---
title: "enable_if 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "enable_if"
  - "std::tr1::enable_if"
  - "std.tr1.enable_if"
  - "std.enable_if"
  - "std::enable_if"
  - "type_traits/std::enable_if"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "enable_if 类 [TR1]"
  - "enable_if"
ms.assetid: c6b8d41c-a18f-4e30-a39e-b3aa0e8fd926
caps.latest.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 28
---
# enable_if 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有条件地为 SFINAE 重载决策设置类型的实例。  当且仅当 `enable_if<Condition,Type>::type` 是 `Type` 时，嵌套的 typedef `Condition` 才存在（并且是 `true` 的同义词）。  
  
## 语法  
  
```  
template<bool B, class T = void>  
    struct enable_if;  
```  
  
#### 参数  
 `B`  
 确定存在产生的类型的值。  
  
 `T`  
 `B` 为 true 时要实例化的类型。  
  
## 备注  
 如果 `B` 为 true，则 `enable_if<B, T>` 具有名为“type”的嵌套 typedef（它是 `T` 的同义词）。  
  
 如果 `B` 为 false，则 `enable_if<B, T>` 不具有名为“type”的嵌套 typedef。  
  
 提供此别名模板：  
  
```cpp  
template< bool B, class T = void >  
using enable_if_t = typename enable_if<B,T>::type;  
```  
  
 在 C\+\+ 中，模板参数的替换失败不是其本身的错误，这称为 *SFINAE*（替换失败不是错误）。  通常，`enable_if` 用于从重载决策中删除候选项（即剔除重载集），以便为了支持一个定义而拒绝另一个定义。  这符合 SFINAE 行为。  有关 SFINAE 的详细信息，请参阅 Wikipedia 上的[替换失败不是错误](http://go.microsoft.com/fwlink/?LinkId=394798)。  
  
 以下是四种示例方案：  
  
-   方案 1：包装函数的返回类型：  
  
    ```cpp  
    template <your_stuff> typename enable_if<your_condition, your_return_type>::type  
    yourfunction(args) {  
        // ...  
    }  
  
    // The alias template makes it more concise:  
    template <your_stuff>  
    enable_if_t<your_condition, your_return_type> yourfunction(args) {  
        // ...  
    }  
  
    ```  
  
-   方案 2：添加具有默认参数的函数参数：  
  
    ```cpp  
  
    template <your_stuff> your_return_type_if_present  
    yourfunction(args, enable_if_t<your condition, FOO> = BAR) {  
        // ...  
    }  
    ```  
  
-   方案 3：添加具有默认参数的模板参数：  
  
    ```cpp  
  
    template <your_stuff, typename Dummy = enable_if_t<your_condition>>  
    rest_of_function_declaration_goes_here  
    ```  
  
-   方案 4：如果你的函数具有非模板化的参数，你可以包装其类型：  
  
    ```cpp  
  
    template <typename T>  
    void your_function(const T& t,  
        enable_if_t<is_something<T>::value, const string&> s) {  
        // ...  
    }  
  
    ```  
  
 方案 1 不能使用构造函数和转换运算符，因为它们没有返回类型。  
  
 方案 2 可使参数处于未命名状态。  你可以假定 `::type Dummy = BAR`，但与名称 `Dummy` 无关，而且向其提供一个名称很可能会触发“未引用的参数”警告。  你必须选择 `FOO` 函数参数类型和 `BAR` 默认参数。  你可以假定 `int` 和 `0`，但随后你的代码用户可能会不小心将被忽略的多余整数传递给函数。  因此，我们建议你使用 `void **` 和 `0` 或 `nullptr`，因为它们几乎都无法转换为 `void **`：  
  
```cpp  
template <your_stuff> your_return_type_if_present   
yourfunction(args, typename enable_if<your_condition, void **>::type = nullptr) {  
    // ...  
}  
```  
  
 方案 2 也适用于普通构造函数。  但是，它不适用于转换运算符，因为它们无法采用多余的参数。  它也不适用于 [variadic](../cpp/ellipses-and-variadic-templates.md) 构造函数，因为添加多余的参数会使函数参数打包非导出上下文，从而与使用 `enable_if` 的初衷背道而驰。  
  
 方案 3 可使用名称 `Dummy`，但是它是可选的。  仅“`typename = typename`”可用，但是如果你认为它看起来太怪异，则可以使用“假”名，只是不要使用还可能会在函数定义中使用的名称。  如果你未向 `enable_if` 提供类型，则它默认为 void，这是完全合理的，因为你不在乎 `Dummy` 的具体内容。  这适用于所有情况，包括转换运算符和 [variadic](../cpp/ellipses-and-variadic-templates.md) 构造函数。  
  
 方案 4 在不具有返回类型的构造函数中可用，因此可解决方案 1 的包装限制问题。  但是，方案 4 受限于并非始终可用的非模板化的函数参数。  （在模板化的函数参数上使用方案 4 可以阻止模板参数导入在其上运行。）  
  
 `enable_if` 功能强大，但是如果误用也会很危险。  因为其用途是使候选项在重载决策之前消失，如果误用它，产生的结果可能很容易让人产生混淆。  下面是一些建议：  
  
-   编译时，请不要使用 `enable_if` 在实现之间作出选择。  请永远都不要为 `enable_if` 编写一个 `CONDITION` 并为 `!CONDITION` 编写另一个 enable\_if。  请改为使用*标记调度*模式，例如，一种根据所提供的迭代器的优点选择实现的算法。  
  
-   请不要使用 `enable_if` 强制执行要求。  如果你想要验证模板参数，并且当验证失败时引发错误而不是选择另一个实现，则请使用 [static\_assert](../cpp/static-assert.md)。  
  
-   如果你拥有会使其他好的代码变得不明确的重载集，则请使用 `enable_if`。  通常，这种情况发生在隐式转换构造函数中。  
  
## 示例  
 此示例说明了 STL 模板函数 [std::make\_pair\(\)](../Topic/make_pair.md) 如何利用 `enable_if`。  
  
```cpp  
void func(const pair<int, int>&);  
void func(const pair<string, string>&);  
  
func(make_pair("foo", "bar"));  
```  
  
 在本示例中，`make_pair("foo", "bar")` 将返回 `pair<const char *, const char *>`。  重载决策必须确定你想要的 `func()`。  `pair<A, B>` 具有 `pair<X, Y>` 中的隐式转换构造函数。  这不是新内容，它在 C\+\+98 中出现过。  但是，在 C\+\+98\/03 中，隐式转换构造函数的签名始终存在，即使它是 `pair<int, int>(const pair<const char *, const char *>&)` 也是如此。  重载决策不介意实例化该构造函数的企图严重瓦解，因为 `const char *` 不可隐式转换为 `int`；在实例化函数定义之前，它只是在查看签名。  因此，示例代码是不明确的，因为存在可将 `pair<const char *, const char *>` 转换为 `pair<int, int>` 和 `pair<string, string>` 的签名。  
  
 C\+\+11 通过使用 `enable_if` 确保`pair<A, B>(const pair<X, Y>&)`仅当  **可隐式转换为 `const X&` 且 `A` 可隐式转换为 `const Y&` 时 `B` 才存在，来解决此多义性问题。** 这允许重载决策确定 `pair<const char *, const char *>` 不可转换为 `pair<int, int>`，以及采用 `pair<string, string>` 的重载可行。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)