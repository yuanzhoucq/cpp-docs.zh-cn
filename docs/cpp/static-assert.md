---
title: "static_assert |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- C2338
- static_assert_cpp
- static_assert
dev_langs:
- C++
helpviewer_keywords:
- C++ keywords, static_assert
- C2338
- assertions [C++], static_assert
- static_assert
ms.assetid: 28dd3668-e78c-4de8-ba68-552084743426
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 1428d890fe079c7ac1fce175686e9776f9c21746
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="staticassert"></a>static_assert
在编译时测试软件断言。 如果指定的常量表达式为`false`，编译器显示指定的消息中，如果提供，且编译将失败，错误为 C2338; 否则，声明不起作用。  
  
## <a name="syntax"></a>语法  
  
```   
static_assert( constant-expression, string-literal );  

**Visual Studio 2017 and later:**
static_assert( constant-expression ); 
```  
  
#### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`constant-expression`|可以转换为布尔值的整型常量表达式。<br /><br /> 如果计算出的表达式为零 (false)，则显示 `string-literal` 参数，并且编译因出错而失败。 如果表达式不为零 (true)，则 `static_assert` 声明无效。|  
|`string-literal`|当 `constant-expression` 参数为零时显示的消息。 消息是一个字符串中的字符[基字符集](../c-language/ascii-character-set.md)的编译器; 即，而不[多字节或宽字符](../c-language/multibyte-and-wide-characters.md)。|  
  
## <a name="remarks"></a>备注  
 `constant-expression`参数`static_assert`声明表示*软件断言*。 软件断言指定在程序的某个特定点应满足的条件。 如果满足该条件，则 `static_assert` 声明无效。 如果未满足该条件，则断言失败，编译器在 `string-literal` 参数中显示消息，并且编译因出错而失败。 Visual Studio 2017 及更高版本，字符串文本参数是可选的。 
  
 `static_assert` 声明在编译时测试软件断言。 与此相反，[断言宏、 _assert、 _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)宏测试软件断言在运行时和数据将产生运行的时成本在空间或时间。 由于模板参数包含在 `static_assert` 参数中，因此 `constant-expression` 声明对于调试模板很有用。  
  
 当遇到声明时，编译器将检查 `static_assert` 声明是否存在语法错误。 如果编译器不依赖于模板参数，则编译器会立即计算 `constant-expression` 参数。 否则，在对模板进行实例化时，编译器将计算 `constant-expression` 参数。 因此，当遇到声明时，编译器可能一次发布一个诊断消息，而在对模板进行实例化时也是如此。  
  
 可以在命名空间、类或块范围中使用 `static_assert` 关键字。 （由于 `static_assert` 关键字可以在命名空间范围内使用，因此，即使它不将新名称引入程序中，但从技术上讲，它也是一个声明。）  
  
## <a name="description"></a>描述  
 在下面的示例中，`static_assert` 声明具有命名空间范围。 由于编译器知道类型 `void *` 的大小，因此可以立即计算表达式。  
  
## <a name="example"></a>示例  
  
```  
static_assert(sizeof(void *) == 4, "64-bit code generation is not supported.");  
```  
  
## <a name="description"></a>描述  
 在下面的示例中，`static_assert` 声明具有类范围。 `static_assert`验证模板参数是*纯旧数据*(POD) 类型。 编译器将在声明 `static_assert` 声明时检查该声明，但不计算 `constant-expression` 参数，直到在 `basic_string` 中实例化 `main()` 类模板。  
  
## <a name="example"></a>示例  
  
```  
#include <type_traits>  
#include <iosfwd>  
namespace std {  
template <class CharT, class Traits = std::char_traits<CharT> >  
class basic_string {  
    static_assert(std::is_pod<CharT>::value,  
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
  
## <a name="description"></a>描述  
 在下面的示例中，`static_assert` 声明具有块范围。 `static_assert` 验证 VMPage 结构的大小是否与该系统的虚拟内存页大小相等。  
  
## <a name="example"></a>示例  
  
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
  
## <a name="see-also"></a>另请参阅  
 [断言和用户提供的消息 （c + +）](../cpp/assertion-and-user-supplied-messages-cpp.md)   
 [#error 指令 （C/c + +）](../preprocessor/hash-error-directive-c-cpp.md)   
 [assert 宏、_assert、_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)   
 [模板](../cpp/templates-cpp.md)   
 [ASCII 字符集](../c-language/ascii-character-set.md)   
 [声明和定义](declarations-and-definitions-cpp.md)
