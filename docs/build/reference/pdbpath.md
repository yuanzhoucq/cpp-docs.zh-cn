---
title: -PDBPATH |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /pdbpath
dev_langs:
- C++
helpviewer_keywords:
- .pdb files, path
- -PDBPATH dumpbin option
- /PDBPATH dumpbin option
- PDBPATH dumpbin option
- PDB files, path
ms.assetid: ccf67dcd-0b23-4250-ad47-06c48acbe82b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c9d93ef38ba444fd716bd3363a6605eae66dfec
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699670"
---
# <a name="pdbpath"></a>/PDBPATH

```
/PDBPATH[:VERBOSE] filename
```

### <a name="parameters"></a>参数

*filename*<br/>
要为其查找匹配的.pdb 文件的.dll 或.exe 文件的名称。

**: VERBOSE**<br/>
（可选）报告其中尝试找到.pdb 文件的所有目录。

## <a name="remarks"></a>备注

/ 计算机沿相同路径，调试器将搜索.pdb 文件，并将报告该.pdb 文件如果有，对应于中指定的文件中将搜索 PDBPATH*文件名*。

当使用 Visual Studio 调试器，可能会遇到的问题，因为，调试器进行调试的文件的不同版本使用的.pdb 文件。

/PDBPATH 将搜索沿以下路径的.pdb 文件：

- 检查可执行文件所在的位置。

- 检查写入到可执行文件的 PDB 的位置。 这通常是在已链接映像时的位置。

- 检查沿配置 Visual Studio IDE 中的搜索路径。

- 检查沿 _NT_SYMBOL_PATH 和 _NT_ALT_SYMBOL_PATH 路径环境变量。

- 检查 Windows 目录中。

## <a name="see-also"></a>请参阅

[DUMPBIN 选项](../../build/reference/dumpbin-options.md)<br/>
[/PDBALTPATH（使用备用 PDB 路径）](../../build/reference/pdbaltpath-use-alternate-pdb-path.md)