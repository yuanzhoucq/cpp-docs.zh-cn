---
title: "CString Argument Passing | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "argument passing [C++]"
  - "argument passing [C++], C strings"
  - "arguments [C++], 传递"
  - "CString objects, 传递参数"
  - "函数 [C++], strings as input/output"
  - "传递参数, C strings"
  - "string arguments"
  - "字符串 [C++], as function input/output"
ms.assetid: a67bebff-edf1-4cf4-bbff-d1cc6a901099
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CString Argument Passing
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明如何传递到函数的 [CString](../atl-mfc-shared/reference/cstringt-class.md) 对象以及如何从返回的函数的 `CString` 对象。  
  
##  <a name="_core_cstring_argument.2d.passing_conventions"></a> CString传递约定  
 在定义选件类接口时，必须确定您的成员函数的参数传递的约定。  具有传递和返回的 `CString` 对象一些标准规则。  如果您遵循在 [字符串作为函数的进入](#_core_strings_as_function_inputs) 和 [字符串作为函数输出](#_core_strings_as_function_outputs)描述的规则，您将具有有效，正确的代码。  
  
##  <a name="_core_strings_as_function_inputs"></a> 字符串作为函数的进入  
 最高效且最安全的方式使用 `CString` 对象被调用函数将传递给函数的一 `CString` 对象。  尽管名称，`CString` 对象内部不存储一个字符串作为具有null结束符的c.样式字符串。  相反，`CString` 对象保留它的字符数的精心跟踪。  具有 `CString` 请提供一 `LPCTSTR` 指向一个Null终止的字符串是可能会很大的少量工作，如果您的代码通常必须执行此操作。  因为对 `CString` 目录中的所有更改无效指针，`LPCTSTR` 的旧副本结果是瞬态的。  
  
 很有意义在某些情况下提供c.样式字符串。  例如，可能有一个调用函数编写C的情况，但不支持对象。  在这种情况下，请强制 `CString` 参数传递给 `LPCTSTR`，因此，函数将获取c.样式Null终止的字符串。  还可以转到另一个方向和创建 `CString` 对象使用接受c样式字符串.参数的 `CString` 构造函数。  
  
 如果字符串内容将功能更改，则以声明形参，用非常数 `CString` 引用\(**CString&**）。  
  
##  <a name="_core_strings_as_function_outputs"></a> 字符串作为函数输出  
 通常，因为 `CString` 对象遵循与原类型，的值语义可以从返回的函数的 `CString` 对象。  若要返回一个只读的字符串，请使用常量 `CString` 引用\(**const CString&**）。  下面的示例阐释 `CString` 参数和返回类型:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/CPP/cstring-argument-passing_1.cpp)]  
  
 [!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/CPP/cstring-argument-passing_2.cpp)]  
  
## 请参阅  
 [字符串](../atl-mfc-shared/strings-atl-mfc.md)