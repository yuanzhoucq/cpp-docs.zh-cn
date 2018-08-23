---
title: Unicode 和 MBCS |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], Unicode
- MFC [C++], character sets
- character sets [C++], multibyte
- run-time libraries [C++], language portability
- character sets [C++], Unicode
- Unicode [C++], MFC and C run-time functions
- multibyte characters [C++]
- runtime [C++], language portability
ms.assetid: 677baec6-71b4-4579-94df-64f18bc117c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af5f782a337c7dc4b85c25006d7a1470034b92b4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42584266"
---
# <a name="unicode-and-mbcs"></a>Unicode 和 MBCS
Microsoft 基础类 (MFC) 库、 Visual c + +，C 运行时库和 Visual c + + 开发环境可以帮助在国际化编程。 它们提供：  
  
-   在 Windows 上的 Unicode 标准的支持。 Unicode 是最新的标准，应该尽可能使用它。  
  
     Unicode 是 16 位字符编码、 适用于所有语言提供足够的编码。 所有的 ASCII 字符作为加宽字符包含以 unicode 格式。  
  
-   支持多字节字符集 (MBCS) 的窗体在所有平台上称为双字节字符集 (DBCS)。  
  
     DBCS 字符由 1 或 2 个字节构成。 某些范围的字节将留出使用用作前导字节。 前导字节指定它和以下结尾字节构成单个的 2 个字节宽字符。 您必须跟踪的哪些字节是前导字节。 在特定的多字节字符集中，前导字节位于某个范围内，尾字节也是如此。 这些范围重叠时，可能需要计算上下文以确定某个给定的字节用作前导字节还是尾字节。  
  
-   提供的简化为国际市场编写应用程序的 MBCS 编程的工具支持。  
  
     Mbcs 的版本的 Windows 操作系统的 Visual c + + 开发系统上运行时，包括集成的源代码代码编辑器、 调试器和命令行工具，是完全支持 MBCS 的。 有关详细信息，请参阅[Visual c + + 中的 MBCS 支持](../text/mbcs-support-in-visual-cpp.md)。  
  
> [!NOTE]
>  在本文档中，MBCS 用于描述对多字节字符的所有非 Unicode 支持。 在 Visual c + +，MBCS 始终意味着 DBCS。 不支持 2 个字节宽的字符集。  
  
 根据定义，ASCII 字符集是所有多字节字符集的子集。 在许多多字节字符集中，0x00 - 0x7F 范围内的每个字符都与 ASCII 字符集中具有相同值的字符相同。 例如，在 ASCII 和 MBCS 字符串 1 字节 NULL 字符 (\0) 的值为 0x00 并指示终止 null 字符。  
  
## <a name="see-also"></a>请参阅  
 [文本和字符串](../text/text-and-strings-in-visual-cpp.md)   
 [国际支持](../text/international-enabling.md)