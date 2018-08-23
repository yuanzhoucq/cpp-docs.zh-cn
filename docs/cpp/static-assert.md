---
title: static_assert |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- static_assert_cpp
dev_langs:
- C++
helpviewer_keywords:
- C++ keywords, static_assert
- C2338
- assertions [C++], static_assert
- static_assert
ms.assetid: 28dd3668-e78c-4de8-ba68-552084743426
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6fa9b8fb7fe85aca21e90195534f33201bee59fc
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464929"
---
# <a name="staticassert"></a>static_assert
在编译时测试软件断言。 如果指定的常量表达式为 FALSE，在编译器显示指定的消息，如果提供，且编译将失败，错误为 C2338;否则，声明没有任何影响。  
  
## <a name="syntax"></a>语法  
  
```   
static_assert( constant-expression, string-literal );  

**Visual Studio 2017 and later:**
static_assert( constant-expression ); 
```  
  
#### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|*constant-expression*|可以转换为布尔值的整型常量表达式。<br /><br /> 如果表达式的计算结果为零 (false)，*字符串文字*显示参数，则编译将失败并出现错误。 如果表达式为非零值 (true)， **static_assert**声明不起作用。|  
|*string-literal*|如果显示的消息*常数表达式*参数为零。 该消息是一个字符串中的字符[基字符集](../c-language/ascii-character-set.md)编译器; 的而非[多字节或宽字符](../c-language/multibyte-and-wide-characters.md)。|  
  
## <a name="remarks"></a>备注  
 *常数表达式*的参数**static_assert**声明表示*软件断言*。 软件断言指定在程序的某个特定点应满足的条件。 如果条件为 true， **static_assert**声明不起作用。 如果条件为 false，则断言失败，在编译器显示中的消息*字符串文字*参数，并且编译失败并出现错误。 在 Visual Studio 2017 及更高版本，字符串文字参数是可选的。 
  
 **Static_assert**声明测试软件断言在编译时。 与此相反， [assert 宏、 _assert、 _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)宏测试软件断言在运行时，会产生运行的时花费的空间和时间。 **Static_assert**声明是因为模板自变量可以包含在调试模板尤其有用*常数表达式*参数。  
  
 编译器将检查**static_assert**遇到声明时出现语法错误的声明。 编译器将计算*常数表达式*立即如果它不依赖于模板参数的参数。 否则，编译器将计算*常数表达式*参数实例化模板时。 因此，当遇到声明时，编译器可能一次发布一个诊断消息，而在对模板进行实例化时也是如此。  
  
 可以使用**static_assert**在命名空间、 类或块范围内的关键字。 ( **Static_assert**关键字是声明从技术上讲，即使它不会引入的新名称到您的程序，因为在命名空间范围内使用它也是如此。)  
  
## <a name="description"></a>描述  
 在以下示例中， **static_assert**声明具有命名空间范围。 由于编译器知道类型 `void *` 的大小，因此可以立即计算表达式。  
  
## <a name="example"></a>示例  
  
```cpp 
static_assert(sizeof(void *) == 4, "64-bit code generation is not supported.");  
```  
  
## <a name="description"></a>描述  
 在以下示例中， **static_assert**声明具有类范围。 **Static_assert**验证模板参数是否*纯旧数据*(POD) 类型。 编译器将检查**static_assert**声明进行声明，但不会计算*常数表达式*参数，直到`basic_string`中实例化类模板`main()`.  
  
## <a name="example"></a>示例  
  
```cpp 
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
 在以下示例中， **static_assert**声明具有块范围。 **Static_assert**验证 VMPage 结构的大小等于系统的虚拟内存 pagesize。  
  
## <a name="example"></a>示例  
  
```cpp 
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
  
## <a name="see-also"></a>请参阅  
 [断言和用户提供的消息 （C++）](../cpp/assertion-and-user-supplied-messages-cpp.md)   
 [#error 指令 （C/C++）](../preprocessor/hash-error-directive-c-cpp.md)   
 [assert 宏、_assert、_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)   
 [模板](../cpp/templates-cpp.md)   
 [ASCII 字符集](../c-language/ascii-character-set.md)   
 [声明和定义](declarations-and-definitions-cpp.md)