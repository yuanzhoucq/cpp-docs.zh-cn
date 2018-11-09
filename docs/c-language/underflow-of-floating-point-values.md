---
title: 浮点值的下溢
ms.date: 11/04/2016
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
ms.openlocfilehash: cd4aadc5ab006b79a43e31348fa101d40e8ca03a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477358"
---
# <a name="underflow-of-floating-point-values"></a>浮点值的下溢

**ANSI 4.5.1** 对于下溢范围错误，数学函数是否将整数表达式 `errno` 设置为宏 `ERANGE` 的值

浮点下溢不会将表达式 `errno` 设置为 `ERANGE`。 当值接近零且最终下溢时，该值将设置为零。

## <a name="see-also"></a>请参阅

[库函数](../c-language/library-functions.md)