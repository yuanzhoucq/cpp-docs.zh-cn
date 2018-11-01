---
title: 使用 atexit
ms.date: 11/04/2016
f1_keywords:
- atexit
helpviewer_keywords:
- atexit function
ms.assetid: d28fda17-c3d4-4af6-ba44-f44886bbb237
ms.openlocfilehash: 06baba59b5765f853f081b34d73be28a187730ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637445"
---
# <a name="using-atexit"></a>使用 atexit

与[atexit](../c-runtime-library/reference/atexit.md)函数，可以指定在程序终止之前执行 exit-processing 函数。 初始化之前调用了任何全局静态对象**atexit**在执行 exit-processing 函数之前销毁。

## <a name="see-also"></a>请参阅

[附加终止注意事项](../cpp/additional-termination-considerations.md)