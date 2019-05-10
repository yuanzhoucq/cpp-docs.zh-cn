---
title: 错误 C1013
ms.date: 11/04/2016
f1_keywords:
- C1013
helpviewer_keywords:
- C1013
ms.assetid: 5514a679-efe7-4055-bdd3-5693ca0c332f
ms.openlocfilehash: 4ee0b8ce97ba5d49e2784f7cd3c74c3b930c6a21
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344786"
---
# <a name="fatal-error-c1013"></a>错误 C1013

编译器限制 : 左括号太多

表达式在单个表达式中包含太多级别的括号。 简化表达式，或将其分解为多个语句。

在 Visual C++ 6.0 Service Pack 3 之前，单个表达式中嵌套括号的上限是 59 个。 目前，嵌套括号的上限是 256 个。