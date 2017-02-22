---
title: "Unicode 编程摘要 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Unicode [C++], MFC 和 C 运行时函数"
  - "Unicode [C++], 编程方法"
ms.assetid: a4c9770f-6c9c-447c-996b-980920288bed
caps.latest.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 8
---
# Unicode 编程摘要
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要利用 MFC 和 C 运行时对 Unicode 的支持，需要：  
  
-   定义 **\_UNICODE**。  
  
     在生成程序之前定义 **\_UNICODE** 符号。  
  
-   指定入口点。  
  
     在项目的[属性页](../ide/property-pages-visual-cpp.md)对话框的“链接器”文件夹的“输出”页中，设置 **wWinMainCRTStartup** 的“入口点”符号。  
  
-   使用可移植的运行时函数和类型。  
  
     为 Unicode 字符串处理使用正确的 C 运行时函数。  可以使用 **wcs** 函数族，但您可能更喜欢使用完全可移植的（支持国际化的）**\_TCHAR** 宏。  这些宏都以 **\_tcs** 为前缀；它们一对一地替换 **str** 函数族。  在“运行库参考”的[国际化](../c-runtime-library/internationalization.md)节中对这些函数有详细介绍。  有关更多信息，请参见 [Tchar.h 中的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)。  
  
     使用[支持 Unicode](../text/support-for-unicode.md) 中描述的 **\_TCHAR** 和相关的可移植数据类型。  
  
-   正确地处理字符串。  
  
     Visual C\+\+ 编译器将编码的字符串解释为：  
  
    ```  
    L"this is a literal string"  
    ```  
  
     指出这是 Unicode 字符的字符串。  可以对文字字符使用相同的前缀。  一般使用 **\_T** 宏对字符串进行编码，因此在 Unicode 下字符串编译为 Unicode 字符串，不使用 Unicode 时字符串编译为 ANSI 字符串（包括 MBCS）。  例如，不要使用：  
  
    ```  
    pWnd->SetWindowText( "Hello" );  
    ```  
  
     而使用：  
  
    ```  
    pWnd->SetWindowText( _T("Hello") );  
    ```  
  
     使用已定义的 **\_UNICODE**，**\_T** 将字符串翻译为以 L 为前缀的格式；否则 **\_T** 将字符串翻译为不带 L 前缀的格式。  
  
    > [!TIP]
    >  **\_T** 宏与 `_TEXT` 宏相同。  
  
-   将字符串长度传递给函数时要小心。  
  
     一些函数需要获取字符串的字符数；另一些函数需要获取字符串的字节数。  例如，如果已定义 **\_UNICODE**，则下列对 `CArchive` 对象的调用无效（`str` 属于 `CString`）：  
  
    ```  
    archive.Write( str, str.GetLength( ) );    // invalid  
    ```  
  
     在 Unicode 应用程序中，由于每个字符都是 2 个字节宽，因此长度给出的是字符数而不是正确的字节数。  所以必须使用：  
  
    ```  
    archive.Write( str, str.GetLength( ) * sizeof( _TCHAR ) );    // valid  
    ```  
  
     它指定要写入的正确字节数。  
  
     但是，MFC 成员函数是面向字符而非面向字节的，因此无需此额外的编码：  
  
    ```  
    pDC->TextOut( str, str.GetLength( ) );  
    ```  
  
     `CDC::TextOut` 采用字符数而非字节数。  
  
-   使用 [fopen\_s、\_wfopen\_s](../c-runtime-library/reference/fopen-s-wfopen-s.md) 打开 Unicode 文件。  
  
 总之，MFC 和运行库对 Windows 2000 下的 Unicode 编程提供下列支持：  
  
-   除数据库类成员函数外，所有 MFC 函数（包括 `CString`）都支持 Unicode。  `CString` 还提供 Unicode\/ANSI 转换函数。  
  
-   运行库提供所有字符串处理函数的 Unicode 版本。（运行库还提供适合 Unicode 或 MBCS 的可移植版本。  这些版本是 **\_tcs** 宏。）  
  
-   Tchar.h 提供可移植的数据类型以及用于转换字符串和字符的 **\_T** 宏。  有关更多信息，请参见 [Tchar.h 中的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)。  
  
-   运行库提供 **main** 的宽字符版本。  使用 **wmain** 可使应用程序成为 Unicode 识别的应用程序。  
  
## 请参阅  
 [支持 Unicode](../text/support-for-unicode.md)