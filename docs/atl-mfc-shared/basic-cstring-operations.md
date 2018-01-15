---
title: "基本 CString 操作 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- CString objects, basic operations
- string literals, CString operations
- literal strings, CString operations
- CString objects
- string comparison, CString operations
- characters, accessing in CStrings
ms.assetid: 41db66b2-9427-4bb3-845a-9b6869159a6c
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 42353a9c59bead96da8eb3b114c8acb2361b53d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="basic-cstring-operations"></a>基本 CString 操作
本主题介绍以下基本[CString](../atl-mfc-shared/reference/cstringt-class.md)操作：  
  
- [从标准的 C 文本字符串创建 CString 对象](#_core_creating_cstring_objects_from_standard_c_literal_strings)  
  
- [访问 CString 中的每个字符](#_core_accessing_individual_characters_in_a_cstring)  
  
- [串联两个 CString 对象](#_core_concatenating_two_cstring_objects)  
  
- [比较 CString 对象](#_core_comparing_cstring_objects)  
  
- [将 CString 对象](#_core_converting_cstring_objects)  
  
 `Class CString`基于类模板[CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)。 `CString`是`typedef`的`CStringT`。 更准确地`CString`是`typedef`的*显式专用化*的`CStringT`，即使用类模板定义的类的常用方法。 同样定义的类是`CStringA`和`CStringW`。  
  
 `CString``CStringA`，和`CStringW`atlstr.h 中定义。 `CStringT`在 cstringt.h 中定义。  
  
 `CString``CStringA`，和`CStringW`每获取一组方法和定义运算符`CStringT`用于它们支持的字符串数据。 一些方法重复的并在某些情况下，超过 C 运行时库字符串服务。  
  
 注意：`CString`是本机类。 字符串类可用于在 C + + /cli CLI 管理项目中，使用`System.String`。  
  
##  <a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a>从标准的 C 文本字符串创建 CString 对象  
 你可以将分配到 C 样式字符串`CString`就像你可以指定一个`CString`到另一个对象。  
  
-   C 文本字符串到值分配给`CString`对象。  
  
 [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_1.cpp)]  
  
-   一个值分配给`CString`到另一个`CString`对象。  
  
 [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_2.cpp)]  
  
     内容`CString`时一个复制对象`CString`对象分配给另一个。 因此，两个字符串并共享对构成的字符串的实际字符的引用。 有关如何使用`CString`对象作为值，请参阅[CString 语义](../atl-mfc-shared/cstring-semantics.md)。  
  
    > [!NOTE]
    >  若要编写你的应用程序，以便为 Unicode 或 ANSI 进行编译，请使用 _T 宏代码文本字符串。 有关详细信息，请参阅[Unicode 和多字节字符集 (MBCS) 支持](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。  
  
##  <a name="_core_accessing_individual_characters_in_a_cstring"></a>访问 CString 中的每个字符  
 你可以访问中的单个字符`CString`通过使用对象`GetAt`和`SetAt`方法。 此外可以使用数组元素或下标运算符 ([])，而不是`GetAt`来获取单个字符。 （这类似于访问数组元素的索引，如下所示标准的 C 样式字符串。）索引的值`CString`字符都是从零开始。  
  
##  <a name="_core_concatenating_two_cstring_objects"></a>串联两个 CString 对象  
 要串联两个`CString`对象，请使用串联运算符 (+ 或 + =)、，如下所示。  
  
 [!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_3.cpp)]  
  
 至少一个自变量串联运算符 (+ 或 + =) 必须是`CString`对象，但你可以使用的字符常量字符串 (例如， `"big"`) 或`char`(例如，x) 的其他参数。  
  
##  <a name="_core_comparing_cstring_objects"></a>比较 CString 对象  
 `Compare`方法与 = = 运算符`CString`是等效的。 `Compare``operator==`，和`CompareNoCase`是 MBCS 和 Unicode 感知;`CompareNoCase`也是不区分大小写。 `Collate`方法`CString`区分区域设置，并且通常比慢`Compare`。 使用`Collate`仅其中你必须遵守的排序规则规定的当前区域设置。  
  
 下表显示可用[CString](../atl-mfc-shared/reference/cstringt-class.md)比较函数和 C 运行时库中其等效的 Unicode/MBCS 可移植函数。  
  
|CString 函数|MBCS 函数|Unicode 函数|  
|----------------------|-------------------|----------------------|  
|`Compare`|`_mbscmp`|`wcscmp`|  
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|  
|`Collate`|`_mbscoll`|`wcscoll`|  
  
 `CStringT`类模板定义的关系运算符 (<， \<=、 > =、 >、 = =、 和 ！ =)，它们可供使用`CString`。 你可以比较两个`CStrings`通过使用这些运算符，如下面的示例中所示。  
  
 [!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_4.cpp)]  
  
##  <a name="_core_converting_cstring_objects"></a>将 CString 对象  
 有关将 CString 对象转换为其他字符串类型的信息，请参阅[如何： 转换之间各种字符串类型](../text/how-to-convert-between-various-string-types.md)。  
  
## <a name="using-cstring-with-wcout"></a>CString 使用 wcout  
 若要使用与 CString`wcout`必须显式强制转换为对象`const wchar_t*`下面的示例中所示：  
  
```  
CString cs("meow");

    wcout <<(const wchar_t*) cs <<endl;  
 
```  
  
 不强制转换，`cs`将被视为`void*`和`wcout`打印对象的地址。 此行为是由 c + + 标准模板自变量推导和重载解析中正确本身和符合的之间细微交互引起的。  
  
## <a name="see-also"></a>请参阅  
 [字符串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)   
 [模板专用化](../cpp/template-specialization-cpp.md)   
 [如何：在各种字符串类型之间进行转换](../text/how-to-convert-between-various-string-types.md)

