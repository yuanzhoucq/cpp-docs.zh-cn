---
title: 位域
ms.date: 11/04/2016
helpviewer_keywords:
- bitfields
ms.assetid: e9a1010d-1e1b-487f-9943-3c574e08f544
ms.openlocfilehash: 3ff0092bbd31b8b1cd98fa56fb802c7ce28cb472
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652824"
---
# <a name="bitfields"></a>位域

结构位域被限制为 64 位和可以为类型 int、 unsigned 的 int、 int64、 或 unsigned 的 int64 的签名。 交叉类型边界的位域将跳过位，以使位域到下一步类型对齐方式。 例如，整数位域可能不会跨 32 位边界。

## <a name="see-also"></a>请参阅

[类型和存储](../build/types-and-storage.md)