---
title: "Unicode 和多字节字符集 (MBCS) 支持 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - "MFC [C++], 字符集支持"
  - "MBCS [C++], 字符串和 MFC 支持"
  - "字符串 [C++], MFC 中的 MBCS 支持"
  - "字符集 [C++], 多字节"
  - "Unicode [C++], MFC 字符串"
  - "Unicode [C++], 字符串对象"
  - "字符串 [C++], Unicode"
  - "字符串 [C++], 字符集支持"
ms.assetid: 44b3193b-c92d-40c5-9fa8-5774da303cce
caps.latest.revision: 17
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Unicode 和多字节字符集 (MBCS) 支持
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

某些语言，例如，日语和中文，拥有较大的字符集。  若要为这些市场提供编程支持， Microsoft 基础类库 \(MFC\) 为处理大字符集提供了两个不同的方法：  
  
-   [Unicode](#_core_mfc_support_for_unicode_strings)  
  
-   [多字节字符集（MBCS）](#_core_mfc_support_for_mbcs_strings)  
  
 您应该使用 Unicode 进行所有新的开发。  
  
##  <a name="_core_mfc_support_for_unicode_strings"></a> MFC 支持 Unicode 字符串.  
 整个类库对于 Unicode 字符和字符串是有条件地启用。  具体而言，下列 [CString](../atl-mfc-shared/reference/cstringt-class.md) 类支持 Unicode。  
  
|||||  
|-|-|-|-|  
|UAFXCW.LIB|UAFXCW.PDB|NAFXCWD.LIB|UAFXCWD.PDB|  
|MFC*xx*U.LIB|MFC*xx*U.PDB|MFC*xx*U.DLL|MFC*xx*UD.LIB|  
|MFC*xx*UD.PDB|MFC*xx*UD.DLL|MFCS*xx*U.LIB|MFCS*xx*U.PDB|  
|MFCS*xx*UD.LIB|MFCS*xx*UD.PDB|MFCM*xx*U.LIB|MFCM*xx*U.PDB|  
|MFCM*xx*U.DLL|MFCM*xx*UD.LIB|MFCM*xx*UD.PDB|MFCM*xx*UD.DLL|  
  
 \(*xx* 表示文件版本号；例如，“80 "意味着 8.0 版。\)  
  
 `CString` 基于 `TCHAR` 数据类型。  如果符号 `_UNICODE` 构建了您的应用程序，`TCHAR` 被定义为类型 `wchar_t`，一个16 位字符编码类型。  否则，`TCHAR` 被定义为 `char`，常规的 8 位字符编码。  因此，在 Unicode 下，`CString` 由 16 位字符组成。  不支持 Unicode，它由`char`字符类型组成。  
  
 若要完成基于 Unicode 编程的应用程序，则还必须：  
  
-   使用 `_T` 宏有条件地逐字符串的将代码文本移植到 Unicode。  
  
-   当您传递字符串，要注意函数参数是需要一个字符形式的长度还是一个字节形式的长度。  如果使用 Unicode 字符串，这个差别很重要。  
  
-   使用 C 运行时字符串处理函数的可移植版本。  
  
-   对于字符和字符指针使用以下数据类型：  
  
    -   使用`TCHAR`当您将使用 `char`时。  
  
    -   `LPTSTR`当您将使用 `char*`时。  
  
    -   `LPCTSTR` 当您将使用 `const char*`时。  `CString` 提供运算符 `LPCTSTR` 实现 `CString` 和 `LPCTSTR`之间的转换。  
  
 `CString` 还提供 Unicode 编码的可识别构造函数、赋值运算符和比较运算符。  
  
 有关 Unicode 编程的相关信息，请参见 [Unicode 主题](../mfc/unicode-in-mfc.md)。  [运行时库参考文档](../c-runtime-library/c-run-time-library-reference.md) 定义了其所有字符串处理函数的可移植版本。  请参见类 [国际化](../c-runtime-library/internationalization.md)。  
  
##  <a name="_core_mfc_support_for_mbcs_strings"></a> MFC 支持 MBCS 字符串  
  
> [!WARNING]
>  MBCS 字符串是传统技术，不应在新的项目中使用。  以下信息在您需要维护使用 MBCS 的既有代码，并且这些代码不可使用 Unicode 进行升级的场景中提供。  
  
 类库也可以用于多字节字符集，但是，仅适用于双字节字符集 \(DBCS\)。  
  
> [!IMPORTANT]
>  在 [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)] 及更高版本中，MFC DLL 中的 MBCS 版本可用作 Visual Studio 免费的外接程序，可从 MSDN 的下载网站获得。  有关详细信息，请参见[MFC MBCS DLL 外接程序](../mfc/mfc-mbcs-dll-add-on.md)。  
  
 在多字节字符集中，一个字符可以是一个字节宽，也可以是两个字节宽。  如果是两个字节，它的第一个字节是特定范围的指定前导字节，特定范围依赖于所使用的代码页。  总的来说，前导字节与“尾字节”指出了一个字符编码。  
  
 如果符号 `_MBCS` 定义了您的程序，基于类型 `TCHAR` 的 `CString` 则被映射到 `char`。  由你决定 `CString` 的哪些字节是前导字节，哪些尾字节。  C 运行库提供的函数帮助您确定这个。  
  
 在 DBCS 下，一个给定的字符串可以包含任何单字节代 ANSI 字符、所有双字节字符或二者的组合。  在分析字符串时可能需要特别的小心。  这包括 `CString` 对象。  
  
> [!NOTE]
>  Unicode 字符串在 MFC 的序列化时可以读取正在运行的应用程序中 Unicode 和 MBCS 字符串，而不考虑他们的版本。  您的数据文件可在 Unicode 和的MBCS 版本的程序之间移植。  
  
 它们调用 `CString` 成员函数使用特殊的 C 运行时函数的“常规文本”版本，也使用 Unicode 识别功能。  因此，例如，如果 `CString` 函数调用 `strcmp`，将调用相应的 `_tcscmp`。  根据符号 `_MBCS` 和 `_UNICODE` 如何定义，`_tcscmp` 映射如下：  
  
|||  
|-|-|  
|`_MBCS` 定义为|`_mbscmp`|  
|`_UNICODE` 定义为|`wcscmp`|  
|两个符号都未定义|`strcmp`|  
  
> [!NOTE]
>  符号 `_MBCS` 和 `_UNICODE` 是互斥的。  
  
 泛型文本函数在 [C 运行时库参考](../c-runtime-library/c-run-time-library-reference.md)中讨论的所有运行时字符串处理例程进行了映射。  详情，请参见 [国际化](../c-runtime-library/internationalization.md)。  
  
 同样，`CString` 方法也使用"泛型"数据类型实现了映射。   为了同时支持 MBCS 和 Unicode，MFC使用 `TCHAR` 代替 `char`, `LPTSTR` 代替 `char*`, 以及 `LPCTSTR` 代替 `const char*`.  这些确保了 MBCS 和 Unicode 之间的正确映射。  
  
## 请参阅  
 [字符串](../atl-mfc-shared/strings-atl-mfc.md)   
 [字符串操作](../c-runtime-library/string-manipulation-crt.md)