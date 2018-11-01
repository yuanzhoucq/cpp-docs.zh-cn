---
title: 2.6.1 master 构造
ms.date: 11/04/2016
ms.assetid: c092064b-ea57-4d4e-9c99-a004d65656fe
ms.openlocfilehash: 0501b1fdfbd36829cee2793fc0f7bb03daeda900
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475525"
---
# <a name="261-master-construct"></a>2.6.1 master 构造

**主**指令标识一个构造，它指定由团队的主线程执行的结构化的块。 语法**主**指令是按如下所示：

```
#pragma omp master new-linestructured-block
```

团队中的其他线程才会执行相关联的结构化的块。 没有任何隐式的屏障进入或退出 master 构造上。