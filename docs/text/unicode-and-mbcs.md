---
title: Unicode 和 MBCS |Microsoft 文档
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2e10c07e11cbe940b5f7cfee460ddd33f6f5ff1f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="unicode-and-mbcs"></a>Unicode 和 MBCS
启用 Microsoft 基础类 (MFC) 库、 Visual c + +、 C 运行时库和 Visual c + + 开发环境以帮助你国际化编程。 它们提供：  
  
-   针对 Windows 上 Unicode 标准的支持。 Unicode 是最新的标准，应该尽可能使用它。  
  
     Unicode 是 16 位字符编码，并为所有语言提供足够的编码。 所有的 ASCII 字符作为扩大字符包含在 Unicode。  
  
-   在所有平台上调用双字节字符集 (DBCS) 的一种形式的多字节字符集 (MBCS) 支持。  
  
     DBCS 字符组成 1 或 2 个字节。 某些范围的字节是为留用用作前导字节。 前导字节指定它和以下的结尾字节构成单个 2 字节宽度字符。 你必须跟踪的哪些字节是前导字节。 在特定的多字节字符集中，前导字节位于某个范围内，尾字节也是如此。 这些范围重叠时，可能需要计算上下文以确定某个给定的字节用作前导字节还是结尾字节。  
  
-   支持简化的应用程序为国际市场编写 MBCS 编程的工具。  
  
     MBCS 支持的版本的 Windows 操作系统的 Visual c + + 开发系统上运行的时间，包括集成的源代码编辑器、 调试器和命令行工具 — 是完全支持 MBCS 的。 有关详细信息，请参阅[Visual c + + 中的 MBCS 支持](../text/mbcs-support-in-visual-cpp.md)。  
  
> [!NOTE]
>  在本文档中，MBCS 用于描述的多字节字符的所有非 Unicode 支持。 在 Visual c + +，MBCS 始终意味着 DBCS。 不支持 2 个字节宽的字符集。  
  
 根据定义，ASCII 字符集是多字节字符的所有集的子集。 在许多多字节字符集中，0x00 - 0x7F 范围内的每个字符都与 ASCII 字符集中具有相同值的字符相同。 例如，在 ASCII 和 MBCS 字符字符串，1 字节**NULL**字符 (\0) 的值为 0x00 并指示终止 null 字符。  
  
## <a name="see-also"></a>请参阅  
 [文本和字符串](../text/text-and-strings-in-visual-cpp.md)   
 [国际支持](../text/international-enabling.md)