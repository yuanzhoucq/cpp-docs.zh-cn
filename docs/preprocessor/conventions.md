---
title: 文档约定
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
- preprocessor, conventions
ms.assetid: 469ce448-dc6c-4d0e-ba2b-e2e7a10155e1
ms.openlocfilehash: bb826b879b71edd3631c11a717320cee51c87175
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220369"
---
# <a name="document-conventions"></a>文档约定

约定将对不同的语法组件使用不同的字体特性。 符号和字体如下所示：

| 特性 | 描述 |
|---------------|-----------------|
| nonterminal | 斜体类型指示非终止符。 |
| **#include** | 粗体类型的终止符是必须按所示方式输入的文本保留字和符号。 此上下文中的字符始终区分大小写。 |
| <sub>opt</sub> | 后跟 <sub>opt </sub> 的非终止符始终是可选的。|
| default typeface | 用此字样描述或列出的集中的字符可在语句中用作终止符。 |

跟在非终止符之后的冒号 (:) 引入其定义。 替代定义在单独的行上列出。

在代码语法块中, 默认字样中的这些符号具有特殊含义:

| 符号 | 描述 |
|---|---|
| \[ ] | 方括号括起一个可选元素。 |
| { \| } | 大括号环绕替代元素, 用竖线分隔。 |
| ... | 指示上一个元素模式可以重复。 |

在代码语法块中, 逗号`,`(), 句点`.`(), 分号 (`;`), 冒号 (`:`), 括号 (`( )`)、双引号 (`"`) 和单引号 (`'`) 都是文本。

## <a name="see-also"></a>请参阅

[语法摘要 (C/C++)](../preprocessor/grammar-summary-c-cpp.md)
