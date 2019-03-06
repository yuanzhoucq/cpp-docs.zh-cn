---
title: NAME (C/C++)
ms.date: 11/04/2016
f1_keywords:
- name
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
ms.openlocfilehash: c4888b8f9b6dba4b826f2ee7dda7529a4bdf1586
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414494"
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
