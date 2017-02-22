---
title: "&lt;string&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::<string>"
  - "string/std::<string>"
  - "std.<string>"
  - "<string>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "string 标头"
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# &lt;string&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义容器模板类 `basic_string` 和各种支持模板。  
  
 有关 `basic_string` 的详细信息，请参阅 [basic\_string 类](../standard-library/basic-string-class.md)。  
  
## 语法  
  
```  
#include <string>  
```  
  
## 备注  
 C\+\+ 语言和标准 C\+\+ 库支持两种类型的字符串：  
  
-   以 null 结尾的字符数组通常作为 C 字符串被引用。  
  
-   属于类 `basic_string` 的模板类对象，它处理类似于 `char` 的所有模板参数。  
  
### Typedef  
  
|||  
|-|-|  
|[string](../Topic/string%20\(C++%20STL%20%3Cstring%3E\).md)|使用 `char` 类型的元素将 `basic_string` 模板类的专用化描述为 `string` 的类型。|  
|[wstring](../Topic/wstring.md)|使用 `wchar_t` 类型的元素将 `basic_string` 模板类的专用化描述为 `wstring` 的类型。|  
|[u16string](../Topic/u16string.md)|基于 `char16_t` 类型的元素描述模板类 `basic_string` 的专用化的类型。|  
|[u32string](../Topic/u32string.md)|基于 `char32_t` 类型的元素描述模板类 `basic_string` 的专用化的类型。|  
  
### 运算符  
  
|||  
|-|-|  
|[运算符 \+](../Topic/operator+%20\(%3Cstring%3E\).md)|连接两个字符串对象。|  
|[operator\!\=](../Topic/operator!=%20\(%3Cstring%3E\).md)|测试运算符左侧的字符串对象是否不等于右侧的字符串对象。|  
|[operator\=\=](../Topic/operator==%20\(%3Cstring%3E\).md)|测试运算符左侧的字符串对象是否等于右侧的字符串对象。|  
|[运算符 \<](../Topic/operator%3C%20\(%3Cstring%3E\).md)|测试运算符左侧的字符串对象是否小于右侧的字符串对象。|  
|[运算符 \<\=](../Topic/operator%3C=%20\(in%20%3Cstring%3E\).md)|测试运算符左侧的字符串对象是否小于或等于右侧的字符串对象。|  
|[运算符 &lt;&lt;](../Topic/operator%3C%3C%20\(%3Cstring%3E\).md)|一个模板函数，用于向输出流插入字符串。|  
|[运算符 \>](../Topic/operator%3E%20\(%3Cstring%3E\).md)|测试运算符左侧的字符串对象是否大于右侧的字符串对象。|  
|[运算符 \>\=](../Topic/operator%3E=%20\(%3Cstring%3E\).md)|测试运算符左侧的字符串对象是否大于或等于右侧的字符串对象。|  
|[运算符 \>\>](../Topic/operator%3E%3E%20\(%3Cstring%3E\).md)|一个模板函数，用于从输入流提取字符串。|  
  
### 专用化模板函数  
  
|||  
|-|-|  
|[swap](../Topic/swap%20\(C++%20STL%20%3Cstring%3E\).md)|交换两个字符串的字符数组。|  
|[stod](../Topic/stod.md)|将字符序列转换为 `double.`|  
|[stof](../Topic/stof.md)|将字符序列转换为 `float`。|  
|[stoi](../Topic/stoi.md)|将字符序列转换为整数。|  
|[stold](../Topic/stold.md)|将字符序列转换为 `long double`。|  
|[stoll](../Topic/stoll.md)|将字符序列转换为 `long long`。|  
|[stoul](../Topic/stoul.md)|将字符序列转换为 `unsigned long`。|  
|[stoull](../Topic/stoull.md)|将字符序列转换为 `unsigned long long`。|  
|[to\_string](../Topic/to_string.md)|将一个值转换为 `string`。|  
|[to\_wstring](../Topic/to_wstring.md)|将一个值转换为宽 `string`。|  
  
### 函数  
  
|||  
|-|-|  
|[getline](../Topic/getline%20Template%20Function.md)|将字符串从输入流中一行一行地提取出来。|  
  
### 类  
  
|||  
|-|-|  
|[basic\_string 类](../standard-library/basic-string-class.md)|一个模板类，用于描述可存储任意字符类对象序列的对象。|  
|[char\_traits 结构](../standard-library/char-traits-struct.md)|一个模板类，用于描述与类型 CharType 的字符关联的特性。|  
  
### 专用化  
  
|||  
|-|-|  
|[char\_traits\<char\> 结构](../standard-library/char-traits-char-struct.md)|一个结构，它是模板结构 `char_traits`\<CharType\> 对类型 `char` 的一个元素的专用化。|  
|[char\_traits\<wchar\_t\> 结构](../standard-library/char-traits-wchar-t-struct.md)|一个结构，它是模板结构 `char_traits`\<CharType\> 对类型 `wchar_t` 的一个元素的专用化。|  
|[char\_traits\<char16\_t\> 结构](../standard-library/char-traits-char16-t-struct.md)|`char_traits`\<CharType\> 模板结构对 `char16_t` 类型的元素的专用化的结构。|  
|[char\_traits\<char32\_t\> 结构](../standard-library/char-traits-char32-t-struct.md)|`char_traits`\<CharType\> 模板结构对 `char32_t` 类型的元素的专用化的结构。|  
  
## 要求  
  
-   **标头：**\<string\>  
  
-   **命名空间:** std  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)