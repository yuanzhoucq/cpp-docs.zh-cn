---
title: "错误 C1046 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1046
dev_langs:
- C++
helpviewer_keywords:
- C1046
ms.assetid: 822ec5f5-b0b0-4711-99e1-fc237b619af6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1976a0715dafa7b10d295a7c21e7e7fc7726613f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1046"></a>错误 C1046
编译器限制： 结构嵌套太深  
  
 结构、 联合或类超出嵌套限制，这是 15 个级别。 重写的定义，以减少嵌套级别。 结构、 联合或类通过拆分成两个或多个部分使用`typedef`定义一个或多个嵌套的结构。