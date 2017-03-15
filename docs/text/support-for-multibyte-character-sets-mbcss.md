---
title: "支持多字节字符集 (MBCS) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mbcs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "字符集 [C++], 多字节"
  - "MBCS [C++]"
  - "MBCS [C++], 关于 MBCS"
  - "多字节字符 [C++]"
ms.assetid: b498733c-a1e1-45e3-8f26-d6da3cb5f2dd
caps.latest.revision: 11
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 11
---
# 支持多字节字符集 (MBCS)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

多字节字符集 \(MBCS\) 是一种支持无法用单字节表示的字符集（如日语和中文）的旧方法。  如果要进行新的开发，则应对所有文本字符串（最终用户不会看到的系统字符串也许可以除外）使用 Unicode。  MBCS 是旧技术，不建议用于新开发。  
  
 最常见的 MBCS 实现是双字节字符集 \(DBCS\)。  通常，Visual C\+\+（尤其是 MFC）对 DBCS 完全启用。  
  
> [!WARNING]
>  在 Visual Studio 2013 及更高版本中，将提供多字节字符编码 \(MBCS\) 的 MFC 库作为 Visual Studio 的加载项，Visual Studio 客户（仅限 Professional 和 Enterprise 版本）可从 MSDN 下载站点免费获得。  
>   
>  这些库要求您的驱动器上有大约 440 MB 的空间，且安装包括库的所有本地化版本。  可以将其安装在安装了 Community、Professional 或 Enterprise 版本以及启用了随附 MFC 功能的任何计算机上。  
>   
>  如果您卸载或修复了 Visual Studio，MBCS 库也会被卸载或修复。  但是，如果您只是移除 MFC 功能，MBCS 库将保留在系统中。  如果您修复 MBCS 库，Visual Studio 不会以任何方式修改。  
>   
>  Visual Studio 2013 及更高版本的可再发行组件包仍将包含 MBCS MFC DLL。  无需执行额外步骤即可将 DLL 重新分发至您的计算机。  
  
 有关示例，请参阅 MFC 源代码文件。  
  
 对于在其语言使用大型字符集的市场中使用的平台，Unicode 的最佳备选方法是 MBCS。  MFC 通过使用可国际化的数据类型和 C 运行时函数来支持 MBCS。  应在你的代码中执行相同操作。  
  
 在 MBCS 下，字符以 1 或 2 字节进行编码。  在 2 字节字符中，第一个字节或前导字节会发出信号，表示它和下一个字节将被解释为一个字符。  第一个字节来自保留用作前导字节的代码范围。  哪个范围的字节可以是前导字节取决于正在使用的代码页。  例如，日语代码页 932 将 0x81 到 0x9F 的范围用作前导字节，而朝鲜语代码页 949 使用不同的范围。  
  
 请在 MBCS 编程中考虑以下各方面。  
  
 环境中的 MBCS 字符  
 MBCS 字符可以出现在字符串（如文件名和目录名）中。  
  
 编辑操作  
 MBCS 应用程序中的编辑操作应在字符上（而不是在字节上）执行。  插入点不应拆分一个字符，向右键应向右移动一个字符，依次类推。  **“删除”**应删除一个字符；**“撤消”**应将其重新插入。  
  
 字符串处理  
 在使用 MBCS 的应用程序中，字符串处理会引起特殊问题。  在单一字符串中混合使用两种宽度的字符；因此，你必须记得检查前导字节。  
  
 运行时库支持  
 C 运行时库和 MFC 支持单字节、MBCS 和 Unicode 编程。  使用 `str` 系列的运行时函数处理单字节字符串，使用相应的 `_mbs` 函数处理 MBC 字符串，使用相应的 *wcs* 函数处理 Unicode 字符串。  MFC 类成员函数的实现使用可移植运行时函数，该函数在适当情况下映射到 `str` 系列的函数、MBCS 函数或 Unicode 函数，如“MBCS\/Unicode 可移植性”中所述。  
  
 MBCS\/Unicode 可移植性  
 使用 Tchar.h 头文件，可以从相同的源生成单字节、MBCS 和 Unicode 应用程序。  Tchar.h 定义具有 *\_tcs* 前缀的宏，它们根据需要映射到 `str`、`_mbs` 或 *wcs* 函数。  若要生成 MBCS，请定义符号 **\_MBCS**。  若要生成 Unicode，请定义符号 **\_UNICODE**。  默认情况下，为 MFC 应用程序定义 **\_MBCS**。  有关详细信息，请参阅 [Tchar.h 中的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)。  
  
> [!NOTE]
>  如果同时定义了 **\_UNICODE** 和 **\_MBCS**，则行为是未定义的。  
  
 Mbctype.h 和 Mbstring.h 头文件定义特定于 MBCS 的函数和宏，你可能在某些情况下需要它们。  例如，`_ismbblead` 告诉你字符串中的特定字节是否为前导字节。  
  
 如需获得国际可移植性，请使用 [Unicode](../text/support-for-unicode.md) 或多字节字符集 \(MBCS\) 对程序进行编码。  
  
## 您希望做什么?  
  
-   [在我的程序中启用 MBCS](../text/international-enabling.md)  
  
-   [在我的程序中同时启用 Unicode 和 MBCS](../text/internationalization-strategies.md)  
  
-   [使用 MBCS 创建国际化程序](../text/mbcs-programming-tips.md)  
  
-   [请参阅 Unicode 编程摘要](../text/mbcs-programming-tips.md)  
  
-   [了解字节宽度可移植性的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)  
  
## 请参阅  
 [文本和字符串](../text/text-and-strings-in-visual-cpp.md)   
 [Visual C\+\+ 中的 MBCS 支持](../text/mbcs-support-in-visual-cpp.md)