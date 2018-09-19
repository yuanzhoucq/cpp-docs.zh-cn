---
title: 位域 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- bitfields
ms.assetid: e9a1010d-1e1b-487f-9943-3c574e08f544
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a7451ea6afee81cc296fb091705bde48041ef5d1
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722483"
---
# <a name="bitfields"></a>位域

结构位域被限制为 64 位和可以为类型 int、 unsigned 的 int、 int64、 或 unsigned 的 int64 的签名。 交叉类型边界的位域将跳过位，以使位域到下一步类型对齐方式。 例如，整数位域可能不会跨 32 位边界。

## <a name="see-also"></a>请参阅

[类型和存储](../build/types-and-storage.md)