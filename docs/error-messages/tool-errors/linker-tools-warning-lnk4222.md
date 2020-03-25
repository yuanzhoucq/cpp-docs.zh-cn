---
title: 链接器工具警告 LNK4222
ms.date: 11/04/2016
f1_keywords:
- LNK4222
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
ms.openlocfilehash: f74379861ad04142fd78a8e307af165072c9cadd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183028"
---
# <a name="linker-tools-warning-lnk4222"></a>链接器工具警告 LNK4222

不应为导出符号 "symbol" 分配序号

以下符号不应按序号导出：

- `DllCanUnloadNow`

- `DllGetClassObject`

- `DllGetClassFactoryFromClassString`

- `DllInstall`

- `DllRegisterServer`

- `DllRegisterServerEx`

- `DllUnregisterServer`

这些函数始终按名称定位，使用 `GetProcAddress`。 链接器会发出有关此类导出的警告，因为它可能会导致更大的图像。 如果序号导出的范围很大，但有相对较少的导出，则可能会发生这种情况。 例如，

```
EXPORTS
   DllGetClassObject   @1
   MyOtherAPI      @100
```

将要求导出地址表中包含100个槽，其中有98个（2-99）。 另一方面

```
EXPORTS
   DllGetClassObject
   MyOtherAPI      @100
```

将需要两个槽。 （请注意，还可以通过[/export](../../build/reference/export-exports-a-function.md)链接器选项进行导出。）
