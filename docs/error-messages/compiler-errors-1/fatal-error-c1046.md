---
title: 错误 C1046 |Microsoft Docs
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
ms.openlocfilehash: 449b181167ef493c149e9e34cb2f1a681148411d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035458"
---
# <a name="fatal-error-c1046"></a>错误 C1046

编译器限制： 结构嵌套太深

结构、 联合或类超出是 15 个级别的嵌套限制。 重写的定义，以减少嵌套级别。 结构、 联合或类通过拆分成两个或多个部分使用`typedef`以定义一个或多个嵌套的结构。