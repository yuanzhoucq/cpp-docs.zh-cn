---
title: 错误 C1046
ms.date: 11/04/2016
f1_keywords:
- C1046
helpviewer_keywords:
- C1046
ms.assetid: 822ec5f5-b0b0-4711-99e1-fc237b619af6
ms.openlocfilehash: e8ce3bda246c990c4b58c6270e26a88835903886
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466035"
---
# <a name="fatal-error-c1046"></a>错误 C1046

编译器限制： 结构嵌套太深

结构、 联合或类超出是 15 个级别的嵌套限制。 重写的定义，以减少嵌套级别。 结构、 联合或类通过拆分成两个或多个部分使用`typedef`以定义一个或多个嵌套的结构。