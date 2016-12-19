---
title: "省略号和可变参数模板 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: f20967d9-c967-4fd2-b902-2bb1d5ed87e3
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 省略号和可变参数模板
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文演示了如何借助 C\+\+ 可变参数模板使用省略号 \(`...`\)。  省略号在 C 和 C\+\+ 中具有[许多用途](../misc/ellipsis-dot-dot-dot.md)。  这些包括函数的变量参数列表。  C 运行库的 `printf()` 函数是一种最常见的示例。  
  
 *variadic 模板*是支持任意数量的参数的类或函数模板。  此机制对 C\+\+ 库开发人员尤其有用，因为您可以将其应用于类模板和函数模板，从而提供一系列类型安全和重要功能以及灵活性。  
  
## 语法  
 可变参数模板用两种方法使用省略号。  参数名称的左侧表示*参数包*，参数名称的右侧将参数包扩展为单独的名称。  
  
 以下是*可变参数模板类*定义语法的基本示例：  
  
```cpp  
template<typename... Arguments> class classname;  
```  
  
 如以下示例所示，对于参数装箱和展开，可以根据您的喜好在省略号周围添加空白，例如：  
  
```cpp  
template<typename ...Arguments> class classname;  
```  
  
 或为：  
  
```cpp  
template<typename ... Arguments> class classname;  
```  
  
 请注意本文使用的是显示在第一个例子中约定\(该省略号附加于`typename`\).  
  
 在前面的示例中，`Arguments` 是参数包。  类 `classname` 可以接受参数数目可变，例如以下示例：  
  
```cpp  
  
template<typename... Arguments> class vtclass;  
  
vtclass< > vtinstance1;  
vtclass<int> vtinstance2;  
vtclass<float, bool> vtinstance3;  
vtclass<long, std::vector<int>, std::string> vtinstance4;  
  
```  
  
 通过使用可变参数模板类定义，您还可以要求至少一个参数。  
  
```cpp  
template <typename First, typename... Rest> class classname;  
  
```  
  
 以下是*可变参数模板函数*语法的基本示例：  
  
```cpp  
template <typename... Arguments> returntype functionname(Arguments... args);  
```  
  
 如下一节“**了解可变参数模板**”所示，`Arguments` 参数包展开使用。  
  
 variadic 模板函数语法还可能有其他形式，包括不限制于：  
  
```cpp  
template <typename... Arguments> returntype functionname(Arguments&... args);   
template <typename... Arguments> returntype functionname(Arguments&&... args);  
template <typename... Arguments> returntype functionname(Arguments*... args);  
```  
  
 还允许使用类似 `const` 的说明符：  
  
```cpp  
template <typename... Arguments> returntype functionname(const Arguments&... args);  
  
```  
  
 按照可变参数模板类的定义，您可以创建需要至少一个参数的函数：  
  
```cpp  
template <typename First, typename... Rest> returntype functionname(const First& first, const Rest&... args);  
  
```  
  
 可变模板使用 `sizeof...()` 运算符（与更早的 `sizeof()` 运算符不相关）：  
  
```cpp  
template<typename... Arguments>  
void tfunc(const Arguments&... args)  
{  
    const unsigned numargs = sizeof...(Arguments);  
  
    X xobj[numargs]; // array of some previously defined type X  
  
    helper_func(xobj, args...);  
}  
  
```  
  
## 更多有关省略号位置  
 过去，本文介绍了定义参数装箱和展开“在参数名称左侧的省略号位置，它表示参数，包，并在参数名称右侧，其展开参数装箱到单独的名称”。  这是技术上为 true，但可能会费一番功夫在转换代码。  请考虑：  
  
-   模板参数列表\(`template <parameter-list>`\), `typename...` 介绍了模板参数包。  
  
-   在参数声明语句\(`func(parameter-list)`\)，“顶层”省略号介绍函数参数包，并且该省略号地位是很重要的  
  
    ```cpp  
  
    // v1 is NOT a function parameter pack:  
    template <typename... Types> void func1(std::vector<Types...> v1);   
  
    // v2 IS a function parameter pack:  
    template <typename... Types> void func2(std::vector<Types>... v2);   
    ```  
  
-   如果省略号在参数名之后出现，则具有参数 pack 展开。  
  
## 示例  
 一种阐明 variadic 模板功能框架的好方法是在 `printf` 一些功能的重新写入中使用：  
  
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
  
## Output  
  
```  
  
1  
10, 20  
100, 200, 300  
first, 2, third, 3.14159  
```  
  
> [!NOTE]
>  合并变参数模板函数的大多数实现使用某种形式的递归，但是它与传统递归稍有不同。传统递归涉及使用与函数相同的签名调用函数。（可以重载或模板化，但每次都要选择相同的签名。）可变递归使用不同（几乎总是减少）数目的参数调用可变函数模板，因此每次都抹去不同的签名。  仍需要“基用例”，但是，递归性质是不同的。  
  
## 请参阅  
 [省略号 \(...\)](../misc/ellipsis-dot-dot-dot.md)