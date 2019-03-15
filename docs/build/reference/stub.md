---
title: STUB
ms.date: 11/04/2016
f1_keywords:
- STUB
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
ms.openlocfilehash: 5224fdaa2a03dc615c9e7e7bb7f7ba822a40807e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822114"
---
# <a name="stub"></a>STUB

生成虚拟设备驱动程序 (VxD) 的模块定义文件中使用时，可以指定文件的名称包含 IMAGE_DOS_HEADER 结构 （WINNT 中定义。H) 若要在虚拟设备驱动程序 (VxD) 中使用而不是默认标头。

```
STUB:filename
```

## <a name="remarks"></a>备注

另一种方法指定*文件名*是与[/存根](stub-ms-dos-stub-file-name.md)链接器选项。

存根 （stub） 是有效的模块定义文件中仅在生成 VxD 时。

## <a name="see-also"></a>请参阅

[模块定义语句的规则](rules-for-module-definition-statements.md)
