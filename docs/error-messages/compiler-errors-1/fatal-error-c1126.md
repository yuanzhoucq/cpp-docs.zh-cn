---
title: 错误 C1126 |Microsoft Docs
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
ms.openlocfilehash: f014aafc60a36bfbb4edad50e7e3ceede6e3c8b2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062470"
---
# <a name="fatal-error-c1126"></a>错误 C1126

identifier： 自动分配超过大小

为本地变量的函数 （加上使用的编译器，例如可交换函数的额外 20 字节的空间有限） 分配的空间超过了限制。

若要更正此错误，请使用`malloc`或`new`分配大量的数据。