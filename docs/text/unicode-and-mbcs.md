---
title: "Unicode 和 MBCS | Microsoft Docs"
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
  - "MBCS [C++], Unicode"
  - "MFC [C++], 字符集"
  - "字符集 [C++], 多字节"
  - "运行时库 [C++], 语言可迁移性"
  - "字符集 [C++], Unicode"
  - "Unicode [C++], MFC 和 C 运行时函数"
  - "多字节字符 [C++]"
  - "运行时 [C++], 语言可迁移性"
ms.assetid: 677baec6-71b4-4579-94df-64f18bc117c4
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 9
---
# Unicode 和 MBCS
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为支持国际编程，启用了 Microsoft 基础类库 \(MFC\)、Visual C\+\+ 的 C 运行库和 Visual C\+\+ 开发环境。  它们：  
  
-   在 Windows 2000（以前为 Windows NT）上提供对 Unicode 标准的支持。  Unicode 是当前的标准，并且应尽可能使用。  
  
     Unicode 是为所有语言提供足够编码的 16 位字符编码。  所有 ASCII 字符都作为“加宽”字符包含在 Unicode 中。  
  
    > [!NOTE]
    >  Windows 95、Windows 98 或 Windows Millennium Edition 上不支持 Unicode 标准。  
  
-   在所有平台上，支持称为双字节字符集 \(DBCS\) 的多字节字符集 \(MBCS\) 形式。  
  
     DBCS 字符由一个或两个字节构成。  某些范围的字节留出用作“前导字节”。  前导字节指定由它和后面的“尾字节”构成单个双字节宽字符。  必须清楚哪些字节是前导字节。  在某个多字节字符集内，前导字节位于某个特定范围内，尾字节也一样。  当这两种范围重叠时，可能需要计算上下文以确定某个给定的字节是用作前导字节还是尾字节。  
  
-   对简化 MBCS 编程的工具提供支持（MBCS 编程用于为国际市场编写的应用程序）。  
  
     当在支持 MBCS 的 Windows 操作系统版本上运行时，Visual C\+\+ 开发系统（包括集成的源代码编辑器、调试器和命令行工具）完全支持 MBCS。  有关更多信息，请参见 [Visual C\+\+ 中的 MBCS 支持](../text/mbcs-support-in-visual-cpp.md)。  
  
> [!NOTE]
>  在本文档中，MBCS 用于描述所有对多字节字符的非 Unicode 支持。  在 Visual C\+\+ 中，MBCS 始终是指 DBCS。  不支持比两个字节宽的字符集。  
  
 按照定义，ASCII 字符集是所有多字节字符集的子集。  在许多多字节字符集中，0x00 到 0x7F 范围内的每个字符都与 ASCII 字符集中具有相同值的字符相同。  例如，在 ASCII 和 MBCS 字符串中，单字节 **NULL** 字符（“\\0”）的值都是 0x00 并且指示终止空字符。  
  
## 请参阅  
 [文本和字符串](../text/text-and-strings-in-visual-cpp.md)   
 [国际支持](../text/international-enabling.md)