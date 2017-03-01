---
title: "regex_error 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- regex_error
- std::regex_error
- regex/std::regex_error
- std::regex_error::code
- regex/std::regex_error::code
dev_langs:
- C++
helpviewer_keywords:
- regex_error class
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 248e9ba676b906af62f6804f4939e04158a8e2ef
ms.openlocfilehash: e5eab496a34eaef6f6d382ce8b1d10055c6b4422
ms.lasthandoff: 02/24/2017

---
# <a name="regexerror-class"></a>regex_error 类
报告错误的 basic_regex 对象。  
  
## <a name="syntax"></a>语法  
  
```  
class regex_error  
 : public std::runtime_error {  
public:  
    explicit regex_error(regex_constants::error_code error);

    regex_constants::error_code code() const;

 
 };  
```  
  
## <a name="remarks"></a>备注  
 该类描述一个异常对象，引发该异常的目的是为报告一个构造中的错误或 `basic_regex` 对象的使用错误。  
  
## <a name="requirements"></a>要求  
 **标头：**\<regex&1;>  
  
 **命名空间：** std  
  
##  <a name="a-nameregexerrorcodea--regexerrorcode"></a><a name="regex_error__code"></a>  regex_error::code  
 返回错误代码。  
  
```  
regex_constants::error_code code() const;
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回传递给对象的构造函数的值。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_error_code.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex_error paren(std::regex_constants::error_paren);   
  
    try   
        {   
        std::regex rx("(a");   
        }   
    catch (const std::regex_error& rerr)   
        {   
        std::cout << "regex error: "   
            << (rerr.code() == paren.code()   
                 "unbalanced parentheses" : "")   
            << std::endl;   
        }   
    catch (...)   
        {   
        std::cout << "unknown exception" << std::endl;   
        }   
  
    return (0);   
    }  
  
```  
  
```Output  
regex error: unbalanced parentheses  
```  
  
##  <a name="a-nameregexerrorregexerrora--regexerrorregexerror"></a><a name="regex_error__regex_error"></a>  regex_error::regex_error  
 构造对象。  
  
```  
regex_error(regex_constants::error_code error);
```  
  
### <a name="parameters"></a>参数  
 `error`  
 错误代码。  
  
### <a name="remarks"></a>备注  
 构造函数将构造一个保留 `error`值的对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_error_construct.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex_error paren(std::regex_constants::error_paren);   
  
    try   
        {   
        std::regex rx("(a");   
        }   
    catch (const std::regex_error& rerr)   
        {   
        std::cout << "regex error: "   
            << (rerr.code() == paren.code()   
                 "unbalanced parentheses" : "")   
            << std::endl;   
        }   
    catch (...)   
        {   
        std::cout << "unknown exception" << std::endl;   
        }   
  
    return (0);   
    }  
  
```  
  
```Output  
regex error: unbalanced parentheses  
```  
  
## <a name="see-also"></a>另请参阅  
[\<regex>](../standard-library/regex.md)  
[regex_constants 类](../standard-library/regex-constants-class.md)  
[\<regex> functions](../standard-library/regex-functions.md)  
[regex_iterator 类](../standard-library/regex-iterator-class.md)  
[\<regex> operators](../standard-library/regex-operators.md)  
[regex_token_iterator 类](../standard-library/regex-token-iterator-class.md)  
[regex_traits 类](../standard-library/regex-traits-class.md)  
[\<regex> typedefs](../standard-library/regex-typedefs.md)  

