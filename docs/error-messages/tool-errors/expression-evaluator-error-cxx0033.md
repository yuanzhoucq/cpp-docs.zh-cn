---
title: 表达式计算器错误 CXX0033
ms.date: 11/04/2016
f1_keywords:
- CXX0033
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
ms.openlocfilehash: 2916808d98f1fabc2157fbedc96d76e196661279
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195508"
---
# <a name="expression-evaluator-error-cxx0033"></a>表达式计算器错误 CXX0033

OMF 类型信息中有错误

可执行文件没有有效的对象模块格式（OMF）用于调试。

此错误与 CAN0033 相同。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 此可执行文件不是通过此版本的 Visual C++发布的链接器创建的。 使用 LINK 的当前版本重新链接对象代码。

1. .Exe 文件可能已损坏。 重新编译并重新链接程序。
