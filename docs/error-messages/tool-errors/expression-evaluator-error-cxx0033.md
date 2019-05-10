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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397050"
---
# <a name="expression-evaluator-error-cxx0033"></a>表达式计算器错误 CXX0033

OMF 类型信息时出错

可执行文件没有有效的对象模块格式 (OMF) 以进行调试。

此错误是与 CAN0033 相同。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 可执行文件不用发行与视觉对象的此版本的链接器创建C++。 重新链接使用 LINK.exe 的当前版本的对象代码。

1. .Exe 文件可能已损坏。 重新编译并重新链接程序。