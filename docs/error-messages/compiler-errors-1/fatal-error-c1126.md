---
title: 错误 C1126 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1126
dev_langs:
- C++
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a3ff02d69679074186e593d5e1c16bdf56d1052
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225909"
---
# <a name="fatal-error-c1126"></a>错误 C1126
identifier： 自动分配超过大小  
  
 为本地变量的函数 （加上使用的编译器，如用于可交换函数的额外 20 字节的空间有限） 分配的空间超过了限制。  
  
 若要更正此错误，使用`malloc`或`new`分配大量的数据。