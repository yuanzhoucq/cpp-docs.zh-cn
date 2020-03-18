---
title: 使用 abort
ms.date: 11/04/2016
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
ms.openlocfilehash: e8cc7bce552acf67c0f9bf2025e0040dc051cff6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446409"
---
# <a name="using-abort"></a>使用 abort

调用[abort](../c-runtime-library/reference/abort.md)函数会导致立即终止。 它绕过初始化的全局静态对象的一般析构过程。 它还绕过使用 `atexit` 函数指定的任何特殊处理。

## <a name="see-also"></a>另请参阅

[附加终止注意事项](../cpp/additional-termination-considerations.md)