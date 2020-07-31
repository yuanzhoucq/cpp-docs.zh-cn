---
title: 错误 C1046
ms.date: 11/04/2016
f1_keywords:
- C1046
helpviewer_keywords:
- C1046
ms.assetid: 822ec5f5-b0b0-4711-99e1-fc237b619af6
ms.openlocfilehash: c299648ccb709fd88733f588ca1ded2cbdd17911
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220309"
---
# <a name="fatal-error-c1046"></a>错误 C1046

编译器限制：结构嵌套太深

结构、联合或类超出了15个级别的嵌套限制。 重写定义以降低嵌套级别。 使用 **`typedef`** 定义一个或多个嵌套结构，将结构、联合或类拆分为两个或多个部分。
