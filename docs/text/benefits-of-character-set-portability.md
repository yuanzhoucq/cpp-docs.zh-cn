---
title: 字符的优点集可移植性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 115a4524f3b11d847291015f3bee5ca10f628310
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423437"
---
# <a name="benefits-of-character-set-portability"></a>字符集可迁移性的好处

您可以使用 MFC 和 C 运行时可移植性功能，即使您不目前打算国际化应用程序中受益：

- 移植编码使基本代码的灵活性。 你可以稍后它轻松转移到 Unicode 或 MBCS。

- 使用 Unicode 使 Windows 应用程序更高效。 由于 Windows 使用 Unicode，因此必须转换传递到和从操作系统的非 Unicode 字符串，这可能会产生开销。


## <a name="see-also"></a>请参阅

[Unicode 和 MBCS](../text/unicode-and-mbcs.md)<br/>
[支持 Unicode](../text/support-for-unicode.md)