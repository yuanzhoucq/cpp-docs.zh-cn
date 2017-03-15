---
title: "static_assert | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "C2338"
  - "static_assert_cpp"
  - "static_assert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "断言 [C++], static_assert"
  - "C++ 关键字, static_assert"
  - "C2338"
  - "static_assert"
ms.assetid: 28dd3668-e78c-4de8-ba68-552084743426
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# static_assert
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在编译时测试软件断言。  如果指定的常量表达式为 `false`，则编译器显示指定的消息，并且编译失败，错误为 C2338；否则，声明不起作用。  
  
## 语法  
  
```  
static_assert(   
    constant-expression,   
    string-literal   
);  
```  
  
#### 参数  
  
|参数|说明|  
|--------|--------|  
|`constant-expression`|可以转换为布尔值的整型常量表达式。<br /><br /> 如果计算出的表达式为零 \(false\)，则显示 `string-literal` 参数，并且编译因出错而失败。  如果表达式不为零 \(true\)，则 `static_assert` 声明无效。|  
|`string-literal`|当 `constant-expression` 参数为零时显示的消息。  该消息是编译器的[基本字符集](../c-language/ascii-character-set.md)中的一个字符串；即，不是[多字节或宽字符](../c-language/multibyte-and-wide-characters.md)。|  
  
## 备注  
 `static_assert` 声明的 `constant-expression` 参数表示软件断言。  软件断言指定在程序的某个特定点应满足的条件。  如果满足该条件，则 `static_assert` 声明无效。  如果未满足该条件，则断言失败，编译器在 `string-literal` 参数中显示消息，并且编译因出错而失败。  
  
 `static_assert` 声明在编译时测试软件断言。  相反，[assert 宏、\_assert、\_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) 宏在运行时测试软件断言，并会导致增大运行时花费的空间和时间。  由于模板参数包含在 `constant-expression` 参数中，因此 `static_assert` 声明对于调试模板很有用。  
  
 当遇到声明时，编译器将检查 `static_assert` 声明是否存在语法错误。  如果编译器不依赖于模板参数，则编译器会立即计算 `constant-expression` 参数。  否则，在对模板进行实例化时，编译器将计算 `constant-expression` 参数。  因此，当遇到声明时，编译器可能一次发布一个诊断消息，而在对模板进行实例化时也是如此。  
  
 可以在命名空间、类或块范围中使用 `static_assert` 关键字。（由于 `static_assert` 关键字可以在命名空间范围内使用，因此，即使它不将新名称引入程序中，但从技术上讲，它也是一个声明。）  
  
## 说明  
 在下面的示例中，`static_assert` 声明具有命名空间范围。  由于编译器知道类型 `void *` 的大小，因此可以立即计算表达式。  
  
## 示例  
  
```  
static_assert(sizeof(void *) == 4, "64-bit code generation is not supported.");  
```  
  
## 说明  
 在下面的示例中，`static_assert` 声明具有类范围。  `static_assert` 验证模板参数是否为纯旧数据 \(POD\) 类型。  编译器将在声明 `static_assert` 声明时检查该声明，但不计算 `constant-expression` 参数，直到在 `main()` 中实例化 `basic_string` 类模板。  
  
## 示例  
  
```  
#include <type_traits>  
#include <iosfwd>  
namespace std {  
template <class CharT, class Traits = std::char_traits<CharT> >  
class basic_string {  
    static_assert(tr1::is_pod<CharT>::value,  
                  "Template argument CharT must be a POD type in class template basic_string");  
    // ...  
    };  
}  
struct NonPOD {  
    NonPOD(const NonPOD &) {}  
    virtual ~NonPOD() {}  
};  
int main()  
{  
    std::basic_string<char> bs;  
}  
```  
  
## 说明  
 在下面的示例中，`static_assert` 声明具有块范围。  `static_assert` 验证 VMPage 结构的大小是否与该系统的虚拟内存页大小相等。  
  
## 示例  
  
```  
#include <sys/param.h> // defines PAGESIZE  
class VMMClient {  
public:  
    struct VMPage { // ...   
           };  
    int check_pagesize() {  
    static_assert(sizeof(VMPage) == PAGESIZE,  
        "Struct VMPage must be the same size as a system virtual memory page.");  
    // ...  
    }  
// ...  
};  
```  
  
## 请参阅  
 [断言和用户提供的消息 \(C\+\+\)](../cpp/assertion-and-user-supplied-messages-cpp.md)   
 [\#error 指令](../preprocessor/hash-error-directive-c-cpp.md)   
 [assert 宏、\_assert、\_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)   
 [模板](../cpp/templates-cpp.md)   
 [ASCII 字符集](../c-language/ascii-character-set.md)   
 [声明](../misc/declarations.md)