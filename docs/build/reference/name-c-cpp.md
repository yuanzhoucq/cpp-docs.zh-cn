---
title: 名称 （C/C + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- name
dev_langs:
- C++
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc37a96e50c6cd5bae2cc60661db04f3b92d162b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715749"
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