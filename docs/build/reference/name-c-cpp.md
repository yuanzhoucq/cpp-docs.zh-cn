---
title: NAME (C/C++)
ms.date: 11/04/2016
f1_keywords:
- name
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
ms.openlocfilehash: d0813befc622db72e095c449794405fc5d58465b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812182"
---
# <a name="name-cc"></a>NAME (C/C++)

指定主输出文件的名称。

```
NAME [application][BASE=address]
```

## <a name="remarks"></a>备注

指定输出文件名称的等效方法是使用[/out](out-output-file-name.md)链接器选项和设置的基址等效方法由[/base](base-base-address.md)链接器选项。 如果同时指定两者，/扩展将重写**名称**。

如果您生成 DLL 时，名称只会影响 DLL 名称。

## <a name="see-also"></a>请参阅

[模块定义语句的规则](rules-for-module-definition-statements.md)
