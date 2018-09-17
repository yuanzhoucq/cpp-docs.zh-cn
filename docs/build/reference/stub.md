---
title: 存根 （STUB) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- STUB
dev_langs:
- C++
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 151d7b425a7f397a05e3a06e9d94489a0c76f899
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725109"
---
# <a name="stub"></a>STUB

生成虚拟设备驱动程序 (VxD) 的模块定义文件中使用时，可以指定文件的名称包含 IMAGE_DOS_HEADER 结构 （WINNT 中定义。H) 若要在虚拟设备驱动程序 (VxD) 中使用而不是默认标头。

```
STUB:filename
```

## <a name="remarks"></a>备注

另一种方法指定*文件名*是与[/存根](../../build/reference/stub-ms-dos-stub-file-name.md)链接器选项。

存根 （stub） 是有效的模块定义文件中仅在生成 VxD 时。

## <a name="see-also"></a>请参阅

[模块定义语句的规则](../../build/reference/rules-for-module-definition-statements.md)