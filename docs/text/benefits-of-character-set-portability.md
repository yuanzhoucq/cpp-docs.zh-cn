---
title: 字符集可迁移性的好处
ms.date: 11/04/2016
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
ms.openlocfilehash: 446d59fe62999e5be652be5efabb53fd907fcd88
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631343"
---
# <a name="benefits-of-character-set-portability"></a>字符集可迁移性的好处

您可以使用 MFC 和 C 运行时可移植性功能，即使您不目前打算国际化应用程序中受益：

- 移植编码使基本代码的灵活性。 你可以稍后它轻松转移到 Unicode 或 MBCS。

- 使用 Unicode 使 Windows 应用程序更高效。 由于 Windows 使用 Unicode，因此必须转换传递到和从操作系统的非 Unicode 字符串，这可能会产生开销。

## <a name="see-also"></a>请参阅

[Unicode 和 MBCS](../text/unicode-and-mbcs.md)<br/>
[支持 Unicode](../text/support-for-unicode.md)