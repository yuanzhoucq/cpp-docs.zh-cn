---
title: 表达式计算器错误 CXX0033
ms.date: 11/04/2016
f1_keywords:
- CXX0033
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
ms.openlocfilehash: 8563eb2fbc24c6ad8db639d2e227802412a16090
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642764"
---
# <a name="expression-evaluator-error-cxx0033"></a>表达式计算器错误 CXX0033

OMF 类型信息时出错

可执行文件没有有效的对象模块格式 (OMF) 以进行调试。

此错误是与 CAN0033 相同。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 可执行文件不是与随此版本的 Visual c + + 链接器创建的。 重新链接使用 LINK.exe 的当前版本的对象代码。

1. .Exe 文件可能已损坏。 重新编译并重新链接程序。