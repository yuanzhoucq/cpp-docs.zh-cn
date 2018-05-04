---
title: 位域 |Microsoft 文档
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
ms.openlocfilehash: 85db49f138cc733326e47a3008e79bae5ab4b7cb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="bitfields"></a>位域
结构位域限制为 64 位并且可以为类型 int、 unsigned 的 int、 int64、 或无符号的 int64 签名。 交叉类型边界的位域将跳过位，以使位域与下一步类型对齐方式。 例如，整数位域可能不能跨越 32 位边界。  
  
## <a name="see-also"></a>请参阅  
 [类型和存储](../build/types-and-storage.md)