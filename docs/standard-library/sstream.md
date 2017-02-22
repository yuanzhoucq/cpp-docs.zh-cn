---
title: "&lt;sstream&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.<sstream>"
  - "std::<sstream>"
  - "<sstream>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sstream 标头"
ms.assetid: 56f55bc5-549d-4e7f-aaad-99e0ffa49c9e
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# &lt;sstream&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义支持在一个数组赋对象存储的顺序 iostreams 操作的多个模板类。  此类序列轻松进出模板类转换对象。[basic\_string](../standard-library/basic-string-class.md)  
  
## 语法  
  
```  
namespace std {  
template<class CharType,  
    class Traits = char_traits<CharType>,  
    class Allocator = allocator<CharType> >  
    class basic_stringbuf;  
typedef basic_stringbuf<char> stringbuf;  
typedef basic_stringbuf<wchar_t> wstringbuf;  
  
template<class CharType,  
    class Traits = char_traits<CharType>,  
    class Allocator = allocator<CharType> >  
    class basic_istringstream;  
typedef basic_istringstream<char> istringstream;  
typedef basic_istringstream<wchar_t> wistringstream;  
  
template<class CharType,  
    class Traits = char_traits<CharType>,  
    class Allocator = allocator<CharType> >  
    class basic_ostringstream;  
typedef basic_ostringstream<char> ostringstream;  
typedef basic_ostringstream<wchar_t> wostringstream;  
  
template<class CharType,  
    class Traits = char_traits<CharType>,  
    class Allocator = allocator<CharType> >  
    class basic_stringstream;  
typedef basic_stringstream<char> stringstream;  
typedef basic_stringstream<wchar_t> wstringstream;  
  
        // TEMPLATE FUNCTIONS  
template<class CharType, class Traits, class Allocator>  
    void swap(  
        basic_stringbuf<CharType, Traits, Allocator>& _Left,  
        basic_stringbuf<CharType, Traits, Allocator>& _Right  
    );   
template<class CharType, class Traits, class Allocator>  
    void swap(  
        basic_istringstream<CharType, Traits, Allocator>& _Left,  
        basic_istringstream<CharType, Traits, Allocator>& _Right  
    );  
template<class CharType, class Traits, class Allocator>  
    void swap(  
        basic_ostringstream<CharType, Traits, Allocator>& _Left,  
        basic_ostringstream<CharType, Traits, Allocator>& _Right  
    );  
template<class CharType, class Traits, class Allocator>  
    void swap (  
        basic_stringstream<CharType, Traits, Allocator>& _Left,  
        basic_stringstream<CharType, Traits, Allocator>& _Right  
    );  
}  // namespace std  
  
```  
  
#### 参数  
  
|参数|说明|  
|--------|--------|  
|`_Left`|对 `sstream` 对象的引用。|  
|`_Right`|对 `sstream` 对象的引用。|  
  
## 备注  
 类型 `char *` 的对象。[\<strstream\>](../standard-library/strstream.md) 使用的功能的流。  但是，`<strstream>` 已弃用，并鼓励使用 `<sstream>`。  
  
### Typedef  
  
|||  
|-|-|  
|[istringstream](../Topic/istringstream.md)|创建类型在 `char` 模板参数专用的 `basic_istringstream`。|  
|[ostringstream](../Topic/ostringstream.md)|创建类型在 `char` 模板参数专用的 `basic_ostringstream`。|  
|[stringbuf](../Topic/stringbuf.md)|创建类型在 `char` 模板参数专用的 `basic_stringbuf`。|  
|[stringstream](../Topic/stringstream.md)|创建类型在 `char` 模板参数专用的 `basic_stringstream`。|  
|[wistringstream](../Topic/wistringstream.md)|创建类型在 `wchar_t` 模板参数专用的 `basic_istringstream`。|  
|[wostringstream](../Topic/wostringstream.md)|创建类型在 `wchar_t` 模板参数专用的 `basic_ostringstream`。|  
|[wstringbuf](../Topic/wstringbuf.md)|创建类型在 `wchar_t` 模板参数专用的 `basic_stringbuf`。|  
|[wstringstream](../Topic/wstringstream.md)|创建类型在 `wchar_t` 模板参数专用的 `basic_stringstream`。|  
  
### 操控器  
  
|||  
|-|-|  
|[swap](../Topic/%3Csstream%3E%20swap.md)|交换两个 `sstream` 对象之间的值。|  
  
### 类  
  
|||  
|-|-|  
|[basic\_stringbuf](../standard-library/basic-stringbuf-class.md)|进出存储的元素序列描述控制传输 **Elem**元素类型，性格字符类依赖 **Tr**的流缓冲区，在对象数组。|  
|[basic\_istringstream](../standard-library/basic-istringstream-class.md)|描述对象元素和编码对象的控件从类**Elem**，[basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<**Tr**，`Alloc`\>流缓冲区，用 **Elem**类型的元素，性格类取决于字符 **Tr**，并且，元素按类分配的 `Alloc`分配器。|  
|[basic\_ostringstream](../standard-library/basic-ostringstream-class.md)|描述对象元素和编码对象的控件插入类 [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<**Elem**，**Tr**，`Alloc`\>流缓冲区，用 **Elem**类型的元素，性格类取决于字符 **Tr**，并且，元素按类分配的 `Alloc`分配器。|  
|[basic\_stringstream](../standard-library/basic-stringstream-class.md)|描述一个控件对象元素和编码对象的插入和提取使用 [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<类**Elem**，**Tr**，`Alloc`\>流缓冲区，用 **Elem**类型的元素，性格类取决于字符 **Tr**，并且，元素按类分配的 `Alloc`分配器。|  
  
## 要求  
  
-   **页眉：** \<sstream\>  
  
-   **命名空间:**  std  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)