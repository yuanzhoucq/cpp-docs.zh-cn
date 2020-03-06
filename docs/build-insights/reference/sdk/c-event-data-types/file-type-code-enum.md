---
title: FILE_TYPE_CODE 枚举
description: C++生成见解 SDK FILE_TYPE_CODE 枚举引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_TYPE_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e64f9315c62ce40c436032d6c96fdfa725847a7f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335164"
---
# <a name="file_type_code-enum"></a>FILE_TYPE_CODE 枚举

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`FILE_TYPE_CODE` 枚举描述文件的类型。

## <a name="members"></a>Members

| 名称 | 值 | 说明 |
|--|--|--|
| `FILE_TYPE_CODE_OTHER` | 0（0x00000000） | 此枚举中未列出的文件类型。 |
| `FILE_TYPE_CODE_OBJ` | 1 (0x00000001) | 对象（\*.obj）文件。 |
| `FILE_TYPE_CODE_EXECUTABLE_IMAGE` | 2（0x00000002） | 可执行文件（\*.exe）或 DLL （\*.dll）文件。 |
| `FILE_TYPE_CODE_LIB` | 3（0x00000003） | 静态库（* .lib）文件。 |
| `FILE_TYPE_CODE_IMP_LIB` | 4（0x00000004） | 导入库（* .lib） |
| `FILE_TYPE_CODE_EXP` | 5（0x00000005） | 导出（* .exp）文件。 |

## <a name="remarks"></a>备注

::: moniker-end
