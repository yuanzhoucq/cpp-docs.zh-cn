---
title: 2.7.2.3 lastprivate
ms.date: 11/04/2016
ms.assetid: 77f6a5c9-704f-4a88-8476-29db852ed800
ms.openlocfilehash: 15f9af23c4f4e1c0ce2914a979f7a41e7b4a6bc1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428452"
---
# <a name="2723-lastprivate"></a>2.7.2.3 lastprivate

`lastprivate`子句提供的提供的功能超集`private`子句。 语法`lastprivate`子句如下所示：

```
lastprivate(variable-list)
```

中指定的变量*变量列表*具有`private`子句语义。 当`lastprivate`标识的每个值的工作共享构造的指令上出现子句`lastprivate`从关联的循环中，或从词法上最后一个区域指令，按顺序最后一次迭代的变量分配给变量的原始对象。 不是的值分配到的最后一次迭代**有关**或**为并行**，或通过从词法上最后一部分**部分**或**并行部分**指令，则构造之后具有不确定的值。 未分配的子对象后构造还具有不确定的值。

对限制`lastprivate`子句如下所示：

- 所有限制`private`应用。

- 指定为类类型的变量`lastprivate`必须具有可访问的、 明确的复制赋值运算符。

- 专用并行区域内或在中都出现的变量`reduction`子句**并行**指令不能指定`lastprivate`绑定到并行构造的工作共享指令上的子句。