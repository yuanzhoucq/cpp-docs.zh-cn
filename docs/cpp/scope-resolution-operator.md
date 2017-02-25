---
title: "范围解析运算符：:: | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "::"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ":: 运算符"
  - "运算符 [C++], 范围解析"
  - "范围解析运算符"
  - "范围, 范围解析运算符"
ms.assetid: fd5de9d3-c716-4e12-bae9-03a16fd79a50
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 范围解析运算符：::
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

范围解析运算符 `::` 用于标识和消除在不同范围内使用的标识符。  有关范围的详细信息，请参阅[范围](../cpp/scope-visual-cpp.md)。  
  
## 语法  
  
```  
:: identifier class-name :: identifier namespace :: identifier enum class :: identifier enum struct :: identifier  
```  
  
## 备注  
 `identifier` 可以是变量、函数或枚举值。  
  
## 具有命名空间和类  
 以下示例显示范围解析运算符如何与命名空间和类一起使用：  
  
```cpp  
namespace NamespaceA{  
    int x;  
    class ClassA {  
    public:  
        int x;  
    };  
}  
  
int main() {  
  
    // A namespace name used to disambiguate  
    NamespaceA::x = 1;  
  
    // A class name used to disambiguate  
    NamespaceA::ClassA a1;  
    a1.x = 2;  
  
}  
  
```  
  
 没有范围限定符的范围解析运算符表示全局命名空间。  
  
```cpp  
namespace NamespaceA{  
    int x;  
}  
  
int x;   
  
int main() {  
    int x;  
  
    // the x in main()  
    x = 0;   
    // The x in the global namespace  
    ::x = 1;   
  
    // The x in the A namespace  
    NamespaceA::x = 2;   
}  
```  
  
 你可以使用范围解析运算符来标识命名空间的成员，还可标识通过 using 指定成员的命名空间的命名空间。  在下面的示例中，你可以使用 `NamespaceC` 限定 `ClassB`（尽管 `ClassB` 已在 `NamespaceB` 中声明），因为已通过 using 指令在 `NamespaceC` 中指定 `NamespaceB`。  
  
```cpp  
namespace NamespaceB {  
    class ClassB {  
    public:  
        int x;  
    };  
}  
  
namespace NamespaceC{  
    using namespace B;  
  
}  
int main() {  
    NamespaceB::ClassB c_b;  
    NamespaceC::ClassB c_c;  
  
    c_b.x = 3;  
    c_c.x = 4;  
}  
  
```  
  
 可使用范围解析运算符链。  在以下示例中，`NamespaceD::NamespaceD1` 将标识嵌套的命名空间 `NamespaceD1`，并且 `NamespaceE::ClassE::ClassE1` 将标识嵌套的类 `ClassE1`。  
  
```cpp  
namespace NamespaceD{  
    namespace NamespaceD1{  
        int x;  
    }  
}  
  
namespace NamespaceE{  
  
    class ClassE{  
    public:  
        class ClassE1{  
        public:  
            int x;  
        };  
    };  
}  
  
int main() {  
    NamespaceD:: NamespaceD1::x = 6;  
    NamespaceE::ClassE::ClassE1 e1;  
    e1.x = 7  ;  
}  
  
```  
  
## 具有静态成员  
 必须使用范围解析运算符来调用类的静态成员。  
  
```cpp  
class ClassG {  
public:  
    static int get_x() { return x;}  
    static int x;  
};  
  
int ClassG::x = 6;  
  
int main() {  
  
    int gx1 = ClassG::x;  
    int gx2 = ClassG::get_x();   
}  
  
```  
  
## 具有区分范围的枚举  
 区分范围的解析运算符还可以与区分范围的枚举[枚举声明](../cpp/enumerations-cpp.md)的值一起使用，如下例所示：  
  
```cpp  
enum class EnumA{  
    First,  
    Second,  
    Third  
};  
  
int main() {  
  
    EnumA enum_value = EnumA::First;  
}  
  
```  
  
## 请参阅  
 [C\+\+ 运算符优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [命名空间](../cpp/namespaces-cpp.md)   
 [名称和限定名称](../misc/names-and-qualified-names.md)