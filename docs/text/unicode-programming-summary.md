---
title: Unicode 编程摘要 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Unicode [C++], programming with
- Unicode [C++], MFC and C run-time functions
ms.assetid: a4c9770f-6c9c-447c-996b-980920288bed
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a378d46c517dfc0fbb5857ad54bc31f4c34287b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859672"
---
# <a name="unicode-programming-summary"></a>Unicode 编程摘要
若要充分利用 Unicode 的 MFC 和 C 运行时支持，你需要：  
  
-   定义 **_UNICODE**。  
  
     定义符号 **_UNICODE**生成程序之前。  
  
-   指定入口点。  
  
     上**输出**链接器中的文件夹的项目的页[属性页](../ide/property-pages-visual-cpp.md)对话框框中，将入口点符号设置为**wWinMainCRTStartup**。  
  
-   使用可移植运行时函数和类型。  
  
     为 Unicode 字符串处理使用适当的 C 运行时函数。 你可以使用**wcs**系列函数，但你可能希望 （国际上已启用） 完全可移植 **_TCHAR**宏。 这些宏全都带有前缀 **_tcs**; 它们替换，一对一，为**str**函数系列。 中详细介绍这些函数[国际化](../c-runtime-library/internationalization.md)部分*运行时库参考*。 有关详细信息，请参阅[Tchar.h 中的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)。  
  
     使用 **_TCHAR**和相关的可移植数据类型中所述[有关 Unicode 的支持](../text/support-for-unicode.md)。  
  
-   正确处理文本的字符串。  
  
     Visual c + + 编译器将解释为编码的文本字符串：  
  
    ```  
    L"this is a literal string"  
    ```  
  
     表示 Unicode 字符的字符串。 为原义字符，可以使用相同的前缀。 使用 **_T**宏以使它们编译为 Unicode 下的 Unicode 字符串或 Unicode 无的 ANSI 字符串 （包括 MBCS） 的一般情况下，代码文本字符串。 例如，而不是:  
  
    ```  
    pWnd->SetWindowText( "Hello" );  
    ```  
  
     使用：  
  
    ```  
    pWnd->SetWindowText( _T("Hello") );  
    ```  
  
     与 **_UNICODE**定义， **_T**转换字符串到 L 前缀窗体; 否则为 **_T**转换不 L 前缀的字符串。  
  
    > [!TIP]
    >  **_T**宏等同于`_TEXT`宏。  
  
-   请注意将字符串长度传递给函数。  
  
     某些函数需要字符串; 中的字符数其他希望字节的数。 例如，如果 **_UNICODE**定义的以下调用到`CArchive`不起作用对象 (`str`是`CString`):  
  
    ```  
    archive.Write( str, str.GetLength( ) );    // invalid  
    ```  
  
     在 Unicode 应用程序，长度可让你的字符数，但不是正确字节数，因为每个字符是双字节宽。 相反，你必须使用：  
  
    ```  
    archive.Write( str, str.GetLength( ) * sizeof( _TCHAR ) );    // valid  
    ```  
  
     它指定要写入字节的正确的数目。  
  
     但是，MFC 成员函数是面向字符的而不是面向字节的工作未对此进行额外的编码：  
  
    ```  
    pDC->TextOut( str, str.GetLength( ) );  
    ```  
  
     `CDC::TextOut` 采用数量的字符，不的字节数。  
  
-   使用[fopen_s、 _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)若要打开 Unicode 文件。  
  
 总之，MFC 和运行时库提供以下支持 Unicode 编程：  
  
-   数据库类成员函数，除了所有 MFC 函数都都支持 Unicode，包括`CString`。 `CString` 此外提供了 Unicode/ANSI 转换函数。  
  
-   运行时库提供所有字符串处理函数的 Unicode 的版本。 （运行时库还提供了合适的可移植版本为 Unicode 或 MBCS。 这些是 **_tcs**宏。)  
  
-   Tchar.h 提供可移植数据类型和 **_T**宏用于转换字符串和字符。 有关详细信息，请参阅[Tchar.h 中的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)。  
  
-   运行时库提供的宽字符版本**主要**。 使用**wmain**使 Unicode 感知应用程序。  
  
## <a name="see-also"></a>请参阅  
 [支持 Unicode](../text/support-for-unicode.md)