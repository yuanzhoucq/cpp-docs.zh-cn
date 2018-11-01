---
title: alloca
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 2b209335-e3a0-4934-93f0-3b5925d22918
ms.openlocfilehash: 2c528a9cdecc52afa1e7d59f58160b247cecfee2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491619"
---
# <a name="alloca"></a>alloca

[_alloca](../c-runtime-library/reference/alloca.md)必须是 16 字节对齐，此外还要求使用帧指针。

堆栈分配需要包含低于其参数的随后被调用的函数，如中所述[堆栈分配](../build/stack-allocation.md)。

## <a name="see-also"></a>请参阅

[堆栈使用](../build/stack-usage.md)