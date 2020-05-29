---
title: Unicode 和 MBCS
ms.date: 11/04/2016
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
ms.openlocfilehash: 063c8b39ee0d29403b382b57a236f2a3e8759e3f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375745"
---
# <a name="unicode-and-mbcs"></a>Unicode 和 MBCS

启用 Microsoft 基础类 （MFC） 库、用于可视化C++的 C 运行时库和可视化C++开发环境可协助您的国际编程。 这些映像具有以下特性：

- 支持 Windows 上的 Unicode 标准。 Unicode 是最新的标准，应该尽可能使用它。

   Unicode 是一种 16 位字符编码，为所有语言提供足够的编码。 所有 ASCII 字符都包含在 Unicode 中，作为加宽字符。

- 支持所有平台上称为双字节字符集 （DBCS） 的多字节字符集 （MBCS） 形式。

   DBCS 字符由 1 或 2 个字节组成。 某些字节范围被预留用作引线字节。 潜在顾客字节指定它和下面的跟踪字节包含单个 2 字节宽的字符。 您必须跟踪哪些字节是潜在顾客字节。 在特定的多字节字符集中，前导字节位于某个范围内，尾字节也是如此。 当这些范围重叠时，可能需要评估上下文以确定给定字节是作为潜在顾客字节还是跟踪字节。

- 支持简化为国际市场编写的应用程序的 MBCS 编程的工具。

   在启用 MBCS 的 Windows 操作系统版本上运行时，Visual C++ 开发系统（包括集成源代码编辑器、调试器和命令行工具）完全启用了 MBCS。 有关详细信息，请参阅[可视化C++ 中的 MBCS 支持](../text/mbcs-support-in-visual-cpp.md)。

> [!NOTE]
> 在本文档中，MBCS 用于描述对多字节字符的所有非 Unicode 支持。 在可视C++中，MBCS 始终表示 DBCS。 不支持宽于 2 个字节的字符集。

根据定义，ASCII 字符集是所有多字节字符集的子集。 在许多多字节字符集中，0x00 - 0x7F 范围内的每个字符都与 ASCII 字符集中具有相同值的字符相同。 例如，在 ASCII 和 MBCS 字符串中，1 字节 NULL 字符 （'\0'） 的值为 0x00，并指示终止空字符。

## <a name="see-also"></a>另请参阅

[文本和字符串](../text/text-and-strings-in-visual-cpp.md)<br/>
[国际扶持](../text/international-enabling.md)
