---
title: LIBRARY
ms.date: 11/04/2016
f1_keywords:
- LIBRARY
helpviewer_keywords:
- LIBRARY .def file statement
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
ms.openlocfilehash: 73609be698719da05fff357ba80200c49f598add
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422659"
---
# <a name="library"></a>LIBRARY

告知链接以创建 DLL。 同时，链接创建导入库，除非生成中使用了.exp 文件。

```
LIBRARY [library][BASE=address]
```

## <a name="remarks"></a>备注

*库*参数指定的 DLL 的名称。 此外可以使用[/out](../../build/reference/out-output-file-name.md)链接器选项以指定 DLL 的输出名称。

基 =*地址*参数设置操作系统使用要加载的 DLL 的基址。 此参数重写 0x10000000 默认 DLL 位置。 请参阅的说明[/base](../../build/reference/base-base-address.md)有关基址的详细信息的选项。

请记住使用[/DLL](../../build/reference/dll-build-a-dll.md)链接器选项生成 DLL 时。

## <a name="see-also"></a>请参阅

[模块定义语句的规则](../../build/reference/rules-for-module-definition-statements.md)
