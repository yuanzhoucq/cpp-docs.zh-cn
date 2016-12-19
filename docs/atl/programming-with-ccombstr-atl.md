---
title: "使用 CComBSTR 进行编程 (ATL) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComBSTR 类, 编程方法"
  - "Unicode, 使用 CComBSTR [ATL]"
ms.assetid: d3bd0851-d132-4be9-9c4c-6ccba17acb2b
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 CComBSTR 进行编程 (ATL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL选件类 [CComBSTR](../atl/reference/ccombstr-class.md) 在 `BSTR` 数据类型的提供包装。  当 `CComBSTR` 非常有用的工具时，有需要注意的几种情况。  
  
-   [转换问题](#programmingwithccombstr_conversionissues)  
  
-   [范围问题](#programmingwithccombstr_scopeissues)  
  
-   [显式释放CComBSTR对象](#programmingwithccombstr_explicitlyfreeing)  
  
-   [在循环中使用CComBSTR Objects](#programmingwithccombstr_usingloops)  
  
-   [内存泄漏问题](#programmingwithccombstr_memoryleaks)  
  
##  <a name="programmingwithccombstr_conversionissues"></a> 转换问题  
 虽然多个 `CComBSTR` 方法将自动转换为ANSI字符串参数转换为Unicode，方法将总是返回Unicode格式字符串。  若要将输出字符串返回ANSI，请使用ATL转换选件类。  有关ATL转换选件类的更多信息，请参见 [ATL和MFC字符串翻译宏](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md)。  
  
### 示例  
 [!code-cpp[NVC_ATL_Utilities#114](../atl/codesnippet/CPP/programming-with-ccombstr-atl_1.cpp)]  
  
 如果您使用字符串修改 `CComBSTR` 对象，请使用宽字符字符串。  这将减少不必要的转换。  
  
### 示例  
 [!code-cpp[NVC_ATL_Utilities#115](../atl/codesnippet/CPP/programming-with-ccombstr-atl_2.cpp)]  
  
##  <a name="programmingwithccombstr_scopeissues"></a> 范围问题  
 在其超出范围，与任何功能良好的选件类，`CComBSTR` 将其释放资源。  如果函数返回指向 `CComBSTR` 字符串，则可能会出现问题，因为指针，将引用已释放的内存。  在这些情况下，请使用 **Copy** 方法，如下所示。  
  
### 示例  
 [!code-cpp[NVC_ATL_Utilities#116](../atl/codesnippet/CPP/programming-with-ccombstr-atl_3.cpp)]  
  
##  <a name="programmingwithccombstr_explicitlyfreeing"></a> 显式释放CComBSTR对象  
 在对象超出范围之前，显式可能可用在 `CComBSTR` 对象包含的字符串。  如果该字符串被释放，`CComBSTR` 对象无效。  
  
### 示例  
 [!code-cpp[NVC_ATL_Utilities#117](../atl/codesnippet/CPP/programming-with-ccombstr-atl_4.cpp)]  
  
##  <a name="programmingwithccombstr_usingloops"></a> 在循环中使用CComBSTR Objects  
 因为 `CComBSTR` 选件类分配缓冲区执行特定操作，例如 `+=` 运算符或 **Append** 方法，建议不要对一个紧凑循环中的字符串操作。  在这些情况下，`CStringT` 提供更好的性能。  
  
### 示例  
 [!code-cpp[NVC_ATL_Utilities#118](../atl/codesnippet/CPP/programming-with-ccombstr-atl_5.cpp)]  
  
##  <a name="programmingwithccombstr_memoryleaks"></a> 内存泄漏问题  
 通过初始化的 `CComBSTR` 的地址对作为 **\[out\]** 参数导致内存泄漏。  
  
 在下面的示例中，当函数 `MyGoodFunction` 替换字符串时，分配的字符串保存该字符串 `"Initialized"` 泄漏。  
  
 [!code-cpp[NVC_ATL_Utilities#119](../atl/codesnippet/CPP/programming-with-ccombstr-atl_6.cpp)]  
  
 若要避免泄露，请在将该地址之前对现有 `CComBSTR` 对象的 **Empty** 方法作为 **\[out\]** 参数。  
  
 请注意相同的代码不会导致内存泄漏，如果函数的参数是 **\[in, out\]**。  
  
## 请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md)   
 [wstring](../Topic/wstring.md)   
 [String Conversion Macros](../atl/reference/string-conversion-macros.md)