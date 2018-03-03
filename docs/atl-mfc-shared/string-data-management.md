---
title: "字符串数据管理 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ad7a17b1b34375fcb45019bcaf8878757288a290
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="string-data-management"></a>字符串数据管理
Visual c + + 提供多种方式来管理字符串数据：  
  
-   [字符串操作](../c-runtime-library/string-manipulation-crt.md)用于使用 C 样式 null 结尾的字符串  
  
-   用于管理字符串的 Win32 API 函数  
  
-   MFC 的类[CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)，它提供灵活、 可调整大小的字符串对象  
  
-   类[CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)，这独立于 MFC 的字符串对象提供与相同的功能`CString`  
  
 几乎所有的程序使用的字符串数据。 MFC 的`CString`类通常是灵活的字符串处理的最佳解决方案。 从版本 7.0，开始`CString`可以在 MFC 或独立于 MFC 的程序中使用。 这两个运行时库和`CString`支持包含多字节 （宽） 字符，如下所示 Unicode 或 MBCS 编程的字符串。  
  
 本文介绍类库提供了与字符串操作相关的通用服务。 本文中涵盖的主题包括：  
  
-   [Unicode 和 MBCS 提供可移植性](#_core_unicode_and_mbcs_provide_portability)  
  
-   [Cstring 和 const char 指针](#_core_cstrings_and_const_char_pointers)  
  
-   [CString 引用计数](#_core_cstring_reference_counting)  
  
 [CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)类提供了操作字符串的支持。 它旨在替换和扩展通常由 C 运行时库字符串包提供的功能。 `CString`类提供成员函数和简化的字符串处理，类似于 Basic 中的运算符。 此类还提供构造函数和运算符用于构造、 分配，和比较**Cstring**和标准 c + + 字符串数据类型。 因为`CString`不派生自`CObject`，你可以使用`CString`独立于大多数的 Microsoft 基础类库 (MFC) 的对象。  
  
 `CString`对象遵循"值语义"。 A`CString`对象表示一个唯一值。 想一想`CString`为实际字符串，而不是指向字符串的指针。  
  
 A`CString`对象表示的可变数量的字符序列。 `CString`对象可以看作的字符数组。  
  
##  <a name="_core_unicode_and_mbcs_provide_portability"></a>Unicode 和 MBCS 提供可移植性  
 MFC 3.0 版及更高版本，MFC，其中包括`CString`，为 Unicode 和多字节字符集 (MBCS) 启用。 此支持，使你更轻松地编写可移植的应用程序可以构建用于 Unicode 或 ANSI 字符。 若要启用此可移植性，在每个字符`CString`对象属于类型**TCHAR**，其定义为`wchar_t`如果您定义符号**_UNICODE**时生成应用程序，或作为`char`如果不是。 A`wchar_t`字符是 16 位宽。 如果用的符号生成启用 MBCS **_MBCS**定义。 MFC 本身生成使用**_MBCS**符号 （对于 NAFX 库中） 或**_UNICODE** （对于 UAFX 库中） 的符号定义。  
  
> [!NOTE]
>  `CString`中的示例和伴随文章上字符串显示为 Unicode 可移植性正确设置格式字符串，使用**_T**宏，将转换到窗体的文本字符串：  
  
 `L"literal string"`  
  
> [!NOTE]
>  该编译器将为 Unicode 字符串。 例如，以下代码：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]  
  
> [!NOTE]
>  如果将被转换为 Unicode 字符串**_UNICODE**定义或作为一个 ANSI 字符串如果不是。 有关详细信息，请参阅文章[Unicode 和多字节字符集 (MBCS) 支持](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。  
  
 A`CString`对象可存储最多**INT_MAX** (2,147,483,647) 个字符。 **TCHAR**数据类型用于获取或设置单个字符`CString`对象。 与字符数组不同`CString`类具有内置的内存分配功能。 这允许`CString`对象根据需要自动增长 (即，不需要担心增长`CString`对象大小以适应较长的字符串)。  
  
##  <a name="_core_cstrings_and_const_char_pointers"></a>Cstring 和 const char 指针  
 A`CString`对象还可以充当文字的 C 样式字符串 ( `PCXSTR`，这是与相同**const char\*** 如果不是在 Unicode 下的)。 [CSimpleStringT::operator PCXSTR](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr)转换运算符允许`CString`自由地将替换为在函数调用中的字符指针的对象。 **CString (LPCWSTR** `pszSrc` **)**构造函数允许要替换的字符指针`CString`对象。  
  
 未尝试折叠`CString`对象。 如果使两个`CString`对象包含`Chicago`，例如中的字符`Chicago`存储在两个位置。 （这可能不为 true 的将来版本的 MFC，因此不应依赖于它。）  
  
> [!NOTE]
>  使用[CSimpleStringT::GetBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)和[CSimpleStringT::ReleaseBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)成员函数时你需要直接访问`CString`为非常量指向某个字符。  
  
> [!NOTE]
>  使用[CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring)和[CStringT::SetSysString](../atl-mfc-shared/reference/cstringt-class.md#setsysstring)成员函数以分配和设置`BSTR`在自动化 （以前称为 OLE 自动化） 中使用的对象。  
  
> [!NOTE]
>  如果可能，分配`CString`帧上而不是在堆上的对象。 这样可以节省内存并简化了参数传递。  
  
 `CString`类未实现为 Microsoft 基础类库集合类，但`CString`对象当然可以存储为集合中的元素。  
  
##  <a name="_core_cstring_reference_counting"></a>CString 引用计数  
 从 MFC 4.0 版本后，开始时[CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)复制对象，则 MFC 递增引用计数，而不是将数据复制。 这样，传递参数的值并返回`CString`通过更高效的值的对象。 这些操作会导致复制构造函数以调用，有时多个一次。 递增引用计数降低这些常见的操作的开销并使使用`CString`更具吸引力的选项。  
  
 由于在销毁了每个副本中的原始对象的引用计数会递减。 原始`CString`只要其引用计数降为零，对象不会被销毁。  
  
 你可以使用`CString`成员函数[CSimpleStringT::LockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer)和[CSimpleStringT::UnlockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer)禁用或启用引用计数。  
  
## <a name="see-also"></a>请参阅  
 [常规 MFC 主题](../mfc/general-mfc-topics.md)

