---
title: 编译器错误 C2722 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2722
dev_langs:
- C++
helpviewer_keywords:
- C2722
ms.assetid: 4cc2c7fa-cb12-4bcf-9df1-6d627ef62973
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c8838ed6b2d202d58c9553a773da9653839b6c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236373"
---
# <a name="compiler-error-c2722"></a>编译器错误 C2722
:: 运算符： 非法以下操作员命令;使用运算符 operator  
  
 `operator`语句重新定义`::new`或`::delete`。 `new`和`delete`运算符是全局性的因此范围解析运算符 (`::`) 是无意义。 删除`::`运算符。