---
title: 表达式计算器错误 CXX0024 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0024
dev_langs:
- C++
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50a07297ddabf269b003a1f14d967d1187fea96d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="expression-evaluator-error-cxx0024"></a>表达式计算器错误 CXX0024
操作需要左值  
  
 有关要求左值的操作指定了计算结果不是左值的表达式。  
  
 左值 （因此称为因为它将出现在赋值语句的左侧） 是指内存位置的表达式。  
  
 例如，`buffer[count]`是一个有效的左值，因为它指向特定内存位置。 逻辑比较`zed != 0`不是有效的左值，因为它的计算结果为 TRUE 或 FALSE，不适用于内存地址。  
  
 此错误是与 CAN0024 相同。