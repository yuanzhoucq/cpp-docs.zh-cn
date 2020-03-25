---
title: 使用 abort
ms.date: 11/04/2016
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
ms.openlocfilehash: db0f6cdcdaf4bca1b74d89a9415c4f7951455d80
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187852"
---
# <a name="using-abort"></a>使用 abort

调用[abort](../c-runtime-library/reference/abort.md)函数会导致立即终止。 它绕过初始化的全局静态对象的一般析构过程。 它还绕过使用 `atexit` 函数指定的任何特殊处理。

## <a name="see-also"></a>另请参阅

[附加终止注意事项](../cpp/additional-termination-considerations.md)
