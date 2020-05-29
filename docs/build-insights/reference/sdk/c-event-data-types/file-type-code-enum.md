---
title: FILE_TYPE_CODE枚举
description: C++生成见解 SDK FILE_TYPE_CODE枚举引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_TYPE_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: dea603a072d7b2f472112a75b2e9ccded78399a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325566"
---
# <a name="file_type_code-enum"></a>FILE_TYPE_CODE枚举

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

枚`FILE_TYPE_CODE`举描述文件的类型。

## <a name="members"></a>成员

| “属性” | “值” | 说明 |
|--|--|--|
| `FILE_TYPE_CODE_OTHER` | 0 （0x000000） | 此枚举中未列出的文件类型。 |
| `FILE_TYPE_CODE_OBJ` | 1 (0x00000001) | 对象 （.obj）\*文件。 |
| `FILE_TYPE_CODE_EXECUTABLE_IMAGE` | 2 （0x0000002） | 可执行文件\*（.exe） 或\*DLL （.dll） 文件。 |
| `FILE_TYPE_CODE_LIB` | 3 （0x0000003） | 静态库 （*.lib） 文件。 |
| `FILE_TYPE_CODE_IMP_LIB` | 4 （0x0000004） | 导入库 （*.lib） |
| `FILE_TYPE_CODE_EXP` | 5 （0x0000005） | 导出 （*.exp） 文件。 |

## <a name="remarks"></a>备注

::: moniker-end
