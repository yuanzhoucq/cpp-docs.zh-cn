---
title: "&lt;filesystem&gt; 运算符 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FILESYSTEM/std::experimental::filesystem::operator==
- std::experimental::filesystem::operator==
- FILESYSTEM/std::experimental::filesystem::operator!=
- std::experimental::filesystem::operator!=
- FILESYSTEM/std::experimental::filesystem::operator<
- std::experimental::filesystem::operator<
- FILESYSTEM/std::experimental::filesystem::operator<=
- std::experimental::filesystem::operator<=
- FILESYSTEM/std::experimental::filesystem::operator>
- std::experimental::filesystem::operator>
- FILESYSTEM/std::experimental::filesystem::operator>=
- std::experimental::filesystem::operator>=
- FILESYSTEM/std::experimental::filesystem::operator/
- std::experimental::filesystem::operator/
- FILESYSTEM/std::experimental::filesystem::operator<<
- std::experimental::filesystem::operator<<
- FILESYSTEM/std::experimental::filesystem::operator>>
- std::experimental::filesystem::operator>>
dev_langs:
- C++
ms.assetid: 102c4833-aa3b-41a8-8998-f5003c546bfd
caps.latest.revision: 12
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
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 0875324fada10022291e8d33c2c2d6cf7276105c
ms.lasthandoff: 02/24/2017

---
# <a name="ltfilesystemgt-operators"></a>&lt;filesystem&gt; 运算符
这些运算符将两个路径作为字符串进行词汇比较。 使用 **等效** 函数来确定两个路径（例如，相对路径和绝对路径）是否指向磁盘上的同一文件或目录。  
  
```  
C:\root> D:\root: false  
C:\root> C:\root\sub: false  
C:\root> C:\roo: true  
```  
  
 有关详细信息，请参阅[文件系统导航 (C++)](../standard-library/file-system-navigation.md)。  
  
## <a name="operator"></a>operator==  
  
```  
bool operator==(const path& left, const path& right) noexcept;  
```  
  
 函数返回 left.native() == right.native()。  
  
## <a name="operator"></a>operator!=  
  
```  
bool operator!=(const path& left, const path& right) noexcept;  
```  
  
 函数返回 !(left == right)。  
  
## <a name="operator"></a>operator<  
  
```  
bool operator<(const path& left, const path& right) noexcept;  
```  
  
 函数返回 left.native() < right.native()。  
  
## <a name="operator"></a>operator<=  
  
```  
bool operator<=(const path& left, const path& right) noexcept;  
```  
  
 函数返回 !(right \< left)。  
  
## <a name="operator"></a>operator>  
  
```  
bool operator>(const path& left, const path& right) noexcept;  
```  
  
 函数返回 right \< left。  
  
## <a name="operator"></a>operator>=  
  
```  
bool operator>=(const path& left, const path& right) noexcept;  
```  
  
 函数返回 !(left < right)。  
  
## <a name="operator"></a>operator/  
  
```  
path operator/(const path& left, const path& right);
```  
  
 函数执行：  
  
```  
basic_string<Elem, Traits> str;  
path ans = left;  
return (ans /= right);
```  
  
## <a name="operator"></a>operator<<  
  
```  
template <class Elem, class Traits>  
basic_ostream<Elem, Traits>& operator<<(basic_ostream<Elem, Traits>& os, const path& pval);
```  
  
 函数返回 os << pval.string\<Elem, Traits>()。  
  
## <a name="operator"></a>operator>>  
  
```  
template <class Elem, class Traits>  
basic_istream<Elem, Traits>& operator<<(basic_istream<Elem, Traits>& is, const path& pval);
```  
  
 函数执行：  
  
```  
basic_string<Elem, Traits> str;  
is>> str;  
pval = str;  
return (is);
```  
  
## <a name="see-also"></a>另请参阅  
 [path 类（C++ 标准库）](../standard-library/path-class.md)   
 [文件系统导航 (C++)](../standard-library/file-system-navigation.md)   
 [\<filesystem>](../standard-library/filesystem.md)


