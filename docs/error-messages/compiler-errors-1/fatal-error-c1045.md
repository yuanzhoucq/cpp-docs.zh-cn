---
title: 错误 C1045 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1045
dev_langs:
- C++
helpviewer_keywords:
- C1045
ms.assetid: 766c2f89-4ecd-4281-adaa-14b270cc0829
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78ff500d050fbb646dd97fc898279712fb750d9e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197606"
---
# <a name="fatal-error-c1045"></a>错误 C1045
编译器限制 : 链接规范嵌套太深  
  
 嵌套的外部对象超过编译器限制。 允许嵌套的外部项使用外部链接类型，如 `extern` “C++”。 减少嵌套的外部项的数量以解决该错误。