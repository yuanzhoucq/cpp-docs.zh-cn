---
title: 链接器工具警告 LNK4222
ms.date: 11/04/2016
f1_keywords:
- LNK4222
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
ms.openlocfilehash: 52a4fee532eb9997dcf013f95246b27fdffc4c20
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563093"
---
# <a name="linker-tools-warning-lnk4222"></a>链接器工具警告 LNK4222

不应为导出的符号 symbol 分配序号

不应按序号导出以下符号：

- `DllCanUnloadNow`

- `DllGetClassObject`

- `DllGetClassFactoryFromClassString`

- `DllInstall`

- `DllRegisterServer`

- `DllRegisterServerEx`

- `DllUnregisterServer`

这些函数始终位于按名称、 使用`GetProcAddress`。 对此发出警告，链接器导出的类型是因为它可能导致可查看大图像。 如果序号导出的范围很大，包含导出相对较少，则可能发生这种情况。 例如，应用于对象的

```
EXPORTS
   DllGetClassObject   @1
   MyOtherAPI      @100
```

将需要 100 个槽，其中 98 个导出地址表中 (2-99) 仅供补充。 另一方面

```
EXPORTS
   DllGetClassObject
   MyOtherAPI      @100
```

将需要两个槽。 (请注意您还可以导出与[/export](../../build/reference/export-exports-a-function.md)链接器选项。)