---
title: NAME (C/C++)
ms.date: 11/04/2016
f1_keywords:
- name
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
ms.openlocfilehash: c05e82409d6b6e48390d54160e8ff23ada788d41
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646194"
---
# <a name="name-cc"></a>NAME (C/C++)

指定主输出文件的名称。

```
NAME [application][BASE=address]
```

## <a name="remarks"></a>备注

指定输出文件名称的等效方法是使用[/out](../../build/reference/out-output-file-name.md)链接器选项和设置的基址等效方法由[/base](../../build/reference/base-base-address.md)链接器选项。 如果同时指定两者，/扩展将重写**名称**。

如果您生成 DLL 时，名称只会影响 DLL 名称。

## <a name="see-also"></a>请参阅

[模块定义语句的规则](../../build/reference/rules-for-module-definition-statements.md)