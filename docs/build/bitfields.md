---
title: "位域 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- bitfields
ms.assetid: e9a1010d-1e1b-487f-9943-3c574e08f544
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 231d84e5d99cd9e6c1238ae12c143636f62ce80d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="bitfields"></a>位域
结构位域限制为 64 位并且可以为类型 int、 unsigned 的 int、 int64、 或无符号的 int64 签名。 交叉类型边界的位域将跳过位，以使位域与下一步类型对齐方式。 例如，整数位域可能不能跨越 32 位边界。  
  
## <a name="see-also"></a>请参阅  
 [类型和存储](../build/types-and-storage.md)