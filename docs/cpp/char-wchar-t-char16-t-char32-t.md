---
title: "char、 wchar_t、 char16_t、 char32_t |Microsoft 文档"
ms.custom: 
ms.date: 02/14/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- char_cpp
- char16_t_cpp
- wchar_t_cpp
- char32_t_cpp
dev_langs:
- C++
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a87eff9801b2754909159ef4d5e2c24c079ee8f1
ms.sourcegitcommit: 23a0ddd271bbcc31631283542981ff5f1693d27f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/15/2018
---
# <a name="char-wchart-char16t-char32t"></a>char、wchar_t、char16_t、char32_t
类型**char**， **wchar_t**， **char16_t**和**char32_t**是表示字母数字字符的内置类型，以及非字母数字的标志符号和非打印字符。

## <a name="syntax"></a>语法

```cpp  
char     ch1{ 'a' };  // or { u8'a' }   
wchar_t  ch2{ L'a' };    
char16_t ch3{ u'a' };    
char32_t ch4{ U'a' };  
```  
  
## <a name="remarks"></a>备注

**Char**类型是 C 和 c + + 中的原始字符类型。 类型**无符号 char**通常用于表示*字节*，这不是 c + + 中的内置类型。 **Char**类型可以用于存储中的字符的 ASCII 字符集或所有 iso-8859 字符集，和单个个字节 Shift JIS 等的多字节字符或 Unicode 字符集的 utf-8 编码。 字符串**char**类型统称为*缩小*字符串，即使用于多字节字符进行编码。 Microsoft 编译器中**char**是 8 位类型。

**Wchar_t**类型为实现定义的宽字符类型。 在 Microsoft 编译器中，它表示用于存储 Unicode 编码为 UTF 16LE，16 位宽字符在 Windows 操作系统上的本机字符类型。 通用 C 运行时 (UCRT) 库函数使用的宽字符版本**wchar_t**和其指针和数组类型作为参数和返回值，像那样的本机 Windows API 的宽字符版本。

**Char16_t**和**char32_t**类型分别表示 16 位和 32 位的宽字符。 Unicode 编码为 utf-16 可以存储在**char16_t**类型和 Unicode 编码为 utf-32 可以存储在**char32_t**类型。 这些类型的字符串和**wchar_t**是否所有称为*宽*字符串，但通常是指专门的字符串**wchar_t**类型。

在 c + + 标准库，`basic_string`类型专用于窄和宽字符串。 使用`std::string`字符时的类型都是**char**，`std::u16string`字符时的类型都是**char16_t**，`std::u32string`字符时的类型都是**char32_t**，和`std::wstring`字符时的类型都是**wchar_t**。 其他表示文本的类型包括`std::stringstream`和`std::cout`均可专用于窄字符串和宽字符串。  
  
