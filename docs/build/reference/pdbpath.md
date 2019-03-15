---
title: /PDBPATH
ms.date: 11/04/2016
f1_keywords:
- /pdbpath
helpviewer_keywords:
- .pdb files, path
- -PDBPATH dumpbin option
- /PDBPATH dumpbin option
- PDBPATH dumpbin option
- PDB files, path
ms.assetid: ccf67dcd-0b23-4250-ad47-06c48acbe82b
ms.openlocfilehash: f29b8e61fbfbdb0f373e3e7510cb3f1fe0b9cc2a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809205"
---
# <a name="pdbpath"></a>/PDBPATH

```
/PDBPATH[:VERBOSE] filename
```

### <a name="parameters"></a>参数

*filename*<br/>
要为其查找匹配的.pdb 文件的.dll 或.exe 文件的名称。

**:VERBOSE**<br/>
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

[DUMPBIN 选项](dumpbin-options.md)<br/>
[/PDBALTPATH（使用备用 PDB 路径）](pdbaltpath-use-alternate-pdb-path.md)
