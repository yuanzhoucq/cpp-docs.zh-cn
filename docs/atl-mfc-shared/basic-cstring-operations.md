---
title: "Basic CString Operations | Microsoft Docs"
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
  - "字符, accessing in CStrings"
  - "CString objects"
  - "CString objects, 基本操作"
  - "literal strings, CString operations"
  - "字符串比较, CString operations"
  - "字符串, CString operations"
ms.assetid: 41db66b2-9427-4bb3-845a-9b6869159a6c
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# Basic CString Operations
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题说明下面的基本 [CString](../atl-mfc-shared/reference/cstringt-class.md) 操作:  
  
-   [创建从标准C字符串的CString对象](#_core_creating_cstring_objects_from_standard_c_literal_strings)  
  
-   [在CString的访问各个字符](#_core_accessing_individual_characters_in_a_cstring)  
  
-   [串联两CString对象](#_core_concatenating_two_cstring_objects)  
  
-   [比较CString对象](#_core_comparing_cstring_objects)  
  
-   [转换CString对象](#_core_converting_cstring_objects)  
  
 `Class CString` 基于选件类模板 [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md)。  `CString` 是 `CStringT``typedef`。  正确，`CString` 是 `CStringT`的 *显式专用化的*`typedef`，是一种常用方法使用选件类模板定义选件类。  同样定义的选件类是 `CStringA` 和 `CStringW`。  有关显式专用化的更多信息，请参见 [类模板实例化](../Topic/Class%20Template%20Instantiation.md)。  
  
 `CString`、 `CStringA`和 `CStringW` 在atlstr.h定义。  `CStringT` 在cstringt.h定义。  
  
 `CString`、 `CStringA`和 `CStringW` 获取 `CStringT` 和运算符定义的方法与其所支持的字符串数据的使用。  某些方法副本，因此，在某些情况下，超过C运行库的字符串服务。  
  
 注意: `CString` 是本机选件类。  对用于c.的C\+\+\/CLI的字符串选件类管理的项目，使用 `System.String`。  
  
##  <a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a> 创建从标准C字符串的CString Objects  
 就象可以分配一 `CString` 对象到另一个中，可以指定C样式字符串到 `CString`。  
  
-   进行c.文本字符串的值为 `CString` 对象。  
  
     [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/CPP/basic-cstring-operations_1.cpp)]  
  
-   分配一 `CString` 的值到另一 `CString` 对象。  
  
     [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/CPP/basic-cstring-operations_2.cpp)]  
  
     当一 `CString` 对象分配给另一个时，`CString` 对象的内容复制。  因此，两个字符串不共享对组成该字符串的实际字符。  有关如何使用 `CString` 对象的更多信息作为值，请参见 [CString Semantics](../atl-mfc-shared/cstring-semantics.md)。  
  
    > [!NOTE]
    >  编写应用程序，以便它可以生成对Unicode或为ANSI，使用\_T宏的代码文本字符串。  有关更多信息，请参见 [Unicode 和多字节字符集 \(MBCS\) 支持](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。  
  
##  <a name="_core_accessing_individual_characters_in_a_cstring"></a> 在CString的访问各个字符  
 使用 `GetAt` 和 `SetAt` 方法，可以在 `CString` 对象的访问各个字符。  还可以使用数组元素或下标，运算符 \( \[ \] \) 而不是 `GetAt` 访问各个字符。  （可以通过索引类似于访问数组元素，在标准 C 样式字符串。）`CString` 字符的索引是从零开始的。  
  
##  <a name="_core_concatenating_two_cstring_objects"></a> 串联两CString Objects  
 若要串联两 `CString` 对象，请使用串联运算符\(\+或\+\=\)，如下所示。  
  
 [!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/CPP/basic-cstring-operations_3.cpp)]  
  
 至少为串联运算符的一个参数\(\+或\+\=\)必须是 `CString` 对象，但是，您可以对另一个参数使用常量字符串\(例如，`"big"`\)或 `char` \(例如，" x "）。  
  
##  <a name="_core_comparing_cstring_objects"></a> 比较CString Objects  
 `Compare` 方法和\=\=运算符 `CString` 的等效。  `Compare`、 `operator==`和 `CompareNoCase` 可识别的MBCS和Unicode的; `CompareNoCase` 也不区分大小写。  `CString``Collate` 方法比 `Compare`是区分区域设置而通常很慢。  使用才必须遵循排序规则按照指定由当前区域设置的 `Collate`。  
  
 下表列出在C运行库中显示可用的 [CString](../atl-mfc-shared/reference/cstringt-class.md) 比较函数及其等效的Unicode\/MBCS可移植函数。  
  
|CString功能|MBCS函数|Unicode函数|  
|---------------|------------|---------------|  
|`Compare`|`_mbscmp`|`wcscmp`|  
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|  
|`Collate`|`_mbscoll`|`wcscoll`|  
  
 `CStringT`选件类模板定义关系运算符（\<、\<\=、\>\=、\>、\=\= 和 \!\=），可供 `CString` 使用。  通过使用这些运算符，如下面的示例所示，可以比较两个 `CStrings`。  
  
 [!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/CPP/basic-cstring-operations_4.cpp)]  
  
##  <a name="_core_converting_cstring_objects"></a> 转换CString Objects  
 有关转换为其他字符串类型的CString对象的信息，请参见 [如何：在各种字符串类型之间进行转换](../text/how-to-convert-between-various-string-types.md)。  
  
## 使用wcout的CString  
 如下面的示例所示，若要使用CString和 `wcout` 必须显式转换为 `const wchar_t*` 的对象:  
  
```  
CString cs("meow");  
  wcout << (const wchar_t*) cs << endl;  
  
```  
  
 不带转换，`void*` 和 `wcout` 输出对象的地址，`cs` 将。  此行为由其正确和符合C\+\+标准模板参数推导和重载决策之间的细微的交互引起的。  
  
## 请参阅  
 [字符串](../atl-mfc-shared/strings-atl-mfc.md)   
 [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md)   
 [类模板实例化](../Topic/Class%20Template%20Instantiation.md)   
 [类模板的显式专用化](../Topic/Explicit%20Specialization%20of%20Class%20Templates.md)   
 [类模板的部分专用化](../cpp/template-specialization-cpp.md)   
 [如何：在各种字符串类型之间进行转换](../text/how-to-convert-between-various-string-types.md)