---
title: 路径字段限制
ms.date: 11/04/2016
f1_keywords:
- _MAX_EXT
- _MAX_DIR
- _MAX_PATH
- _MAX_FNAME
- _MAX_DRIVE
helpviewer_keywords:
- path field constants
- MAX_FNAME constant
- _MAX_DIR constant
- _MAX_DRIVE constant
- paths, maximum limit
- _MAX_PATH constant
- MAX_DRIVE constant
- _MAX_FNAME constant
- _MAX_EXT constant
- MAX_DIR constant
- MAX_EXT constant
ms.assetid: 2b5d0e43-1347-45b4-8397-24a8a45c444e
ms.openlocfilehash: 89609de3fc5584a960480bff83566f5e38c8be1f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477527"
---
# <a name="path-field-limits"></a>路径字段限制

## <a name="syntax"></a>语法

```cpp
#include <stdlib.h>
```

## <a name="remarks"></a>备注

这些常量定义路径的最大长度以及路径内的单个字段的最大长度。

|返回的常量|含义|
|--------------|-------------|
|`_MAX_DIR`|目录组件的最大长度|
|`_MAX_DRIVE`|驱动器组件的最大长度|
|`_MAX_EXT`|扩展组件的最大长度|
|`_MAX_FNAME`|文件名组件的最大长度|
|`_MAX_PATH`|完整路径的最大长度|

> [!NOTE]
> C 运行库支持的路径的最大长度为 32768 个字符，但这取决于操作系统（特别是文件系统）支持这些较长的路径。 字段长度的总和不应超过 `_MAX_PATH` 以便与 FAT32 文件系统完全向后兼容。 Windows NTFS 文件系统支持的路径的最大长度为 32768 个字符（但仅在使用 Unicode API 时才支持）。 在使用较长的路径名时，为路径添加字符 \\\\?\ 作为前缀，并使用 Unicode 版本的 C 运行时函数。

## <a name="see-also"></a>请参阅

[全局常量](../c-runtime-library/global-constants.md)