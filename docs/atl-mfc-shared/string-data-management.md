---
title: "String Data Management | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Unicode, string objects"
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# String Data Management
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+提供多种管理字符串数据:  
  
-   的[字符串操作](../c-runtime-library/string-manipulation-crt.md) 与C样式Null终止的字符串一起使用  
  
-   托管字符串的Win32 API函数  
  
-   MFC的选件类 [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md)，提供灵活，可调整大小的字符串对象  
  
-   选件类 [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md)，提供MFC独立字符串对象与函数和 `CString`相同  
  
 几乎所有程序与字符串处理数据。  MFC的 `CString` 选件类通常是灵活字符串处理的最佳方法。  从7.0版开始，`CString` 可用于MFC或MFC独立程序。  运行库和 `CString` 支持包含多字节（宽）字符的字符串，在 Unicode 或 MBCS 编程。  
  
 本文介绍常规服务选件类库提供与字符串操作。  本文中包含的主题包括:  
  
-   [Unicode和MBCS提供可移植性](#_core_unicode_and_mbcs_provide_portability)  
  
-   [CStrings和const char指针](#_core_cstrings_and_const_char_pointers)  
  
-   [CString引用计数](#_core_cstring_reference_counting)  
  
 [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md) 选件类提供操作的字符串支持。  要替换和扩展C运行库字符串包通常提供的功能。  `CString` 选件类提供成员函数和运算符处理简化的字符串，类似于在基本找到的接口。  选件类用于构造，分配和比较 **CStrings** 和标准C\+\+字符串数据类型还提供构造函数和运算符。  由于 `CString` 从 `CObject`未派生，可以独立于大多数Microsoft基础选件类库使用 `CString` 对象\(MFC\)。  
  
 `CString` 对象在“值语义”。`CString` 对象表示单个值。  思考 `CString` 作为一个实际字符串，不是指向字符串。  
  
 `CString` 对象表示字符数目可变序列。  `CString` 对象可被视为字符数组。  
  
##  <a name="_core_unicode_and_mbcs_provide_portability"></a> Unicode和MBCS提供可移植性  
 MFC 3.0版和更高版本，MFC，包括 `CString`，对Unicode和多字节字符集\(mbcs\)启用。  此支持便于您对您可以为Unicode或ANSI字符创建的编写可携式代码。  若要启用此可移植性，在 `CString` 对象的每个字符类型 **TCHAR**，定义为 `wchar_t`，如果定义了符号 **\_UNICODE**，当您生成应用程序时，或者 `char`，如果没有。  `wchar_t` 字符都为16位。  如果使用符号 **\_MBCS** 生成定义，MBCS启用。  MFC用 **\_MBCS** 符号\(对于NAFX库\)或\(对于UAFX库\)中定义的 **\_UNICODE** 符号生成。  
  
> [!NOTE]
>  `CString` 示例中的和字符串中的附带的文章显示为Unicode可移植性正确格式的文本字符串，使用 **\_T** 宏，后者将字符串翻译为窗体:  
  
 `L"literal string"`  
  
> [!NOTE]
>  哪些编译器将Unicode字符串。  例如，下列代码：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/CPP/string-data-management_1.cpp)]  
  
> [!NOTE]
>  如果 **\_UNICODE** 定义或为ANSI字符串;如果没有，会转换为Unicode字符串。  有关更多信息，请参见中的文章 [Unicode 和多字节字符集 \(MBCS\) 支持](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。  
  
 `CString` 对象可存储到 **INT\_MAX** \(2,147,483,647\)字符。  **TCHAR** 数据类型用于获取或设置各个字符在 `CString` 对象内。  不同字符数组，`CString` 选件类具有固定内存分配函数。  这允许 `CString` 对象自动增大根据需要\(即不需要考虑其 `CString` 对象以适应较长字符串\)。  
  
##  <a name="_core_cstrings_and_const_char_pointers"></a> CStrings和const char指针  
 `CString` 对象也象一个文本C样式字符串\( `PCXSTR`，与 **const char\***，如果不在Unicode下\)。  [CSimpleStringT::operator PCXSTR](../Topic/CSimpleStringT::operator%20PCXSTR.md) 转换运算符允许 `CString` 对象用的指针函数调用的字符随意进行替换。  **CString\( LPCWSTR**`pszSrc`**\)** 构造函数允许字符指针在 `CString` 对象进行替换。  
  
 不会尝试折叠 `CString` 对象。  如果您创建包含 `Chicago`的两 `CString` 对象，例如，在 `Chicago` 的字符在两个位置存储。  \(这可能不是真正的MFC的未来版本，因此，您不应依赖于它。\)  
  
> [!NOTE]
>  当您直接需要访问 `CString` 为用非常数指向字符的指针时，请使用 [CSimpleStringT::GetBuffer](../Topic/CSimpleStringT::GetBuffer.md) 和 [CSimpleStringT::ReleaseBuffer](../Topic/CSimpleStringT::ReleaseBuffer.md) 成员函数。  
  
> [!NOTE]
>  使用 [CStringT::AllocSysString](../Topic/CStringT::AllocSysString.md) 和 [CStringT::SetSysString](../Topic/CStringT::SetSysString.md) 成员函数分配和设置用于自动化的 `BSTR` 对象\(以前称为OLE自动化\)。  
  
> [!NOTE]
>  如果可能，请分配到框架中 `CString` 对象而不是在堆。  这节省内存和简化参数传递。  
  
 `CString` 选件类不实现为Microsoft基础类库选件集合选件类，不过，`CString` 对象可能必须存储为元素集合中。  
  
##  <a name="_core_cstring_reference_counting"></a> CString引用计数  
 基于MFC 4.0版，那么，当 [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md) 复制对象时，MFC会递增引用计数而不是复制数据。  这使得传递参数和返回值 `CString` 对象由更有效的值。  这些操作导致复制构造函数有时不止一次调用。  递增引用计数减少这些常见操作的开销并进行使用 `CString` 一个更构成的选项。  
  
 当销毁每个副本，原始对象的引用计数递减。  销毁的原始 `CString` 对象，直到其引用计数减少为零。  
  
 可以使用 `CString` 成员函数 [CSimpleStringT::LockBuffer](../Topic/CSimpleStringT::LockBuffer.md)，并禁用或启用的 [CSimpleStringT::UnlockBuffer](../Topic/CSimpleStringT::UnlockBuffer.md) 引用计数。  
  
## 请参阅  
 [常规 MFC 主题](../mfc/general-mfc-topics.md)