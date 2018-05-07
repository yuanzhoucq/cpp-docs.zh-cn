---
title: 错误 C1046 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1046
dev_langs:
- C++
helpviewer_keywords:
- C1046
ms.assetid: 822ec5f5-b0b0-4711-99e1-fc237b619af6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 02c609d5f846fa6f339eac98b725919560df068f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1046"></a>错误 C1046
编译器限制： 结构嵌套太深  
  
 结构、 联合或类超出嵌套限制，这是 15 个级别。 重写的定义，以减少嵌套级别。 结构、 联合或类通过拆分成两个或多个部分使用`typedef`定义一个或多个嵌套的结构。