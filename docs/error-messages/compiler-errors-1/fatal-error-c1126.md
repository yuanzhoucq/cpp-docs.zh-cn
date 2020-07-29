---
title: 错误 C1126
ms.date: 11/04/2016
f1_keywords:
- C1126
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
ms.openlocfilehash: 110fbfe984ee7714e0c8ee2e2cb4deec4f43905a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87207922"
---
# <a name="fatal-error-c1126"></a>错误 C1126

"identifier"：自动分配超出大小

为函数的局部变量分配的空间（加上编译器使用的有限空间量，如用于交换函数的额外20个字节）超过限制。

若要更正此错误，请使用 `malloc` 或 **`new`** 以分配大量的数据。
