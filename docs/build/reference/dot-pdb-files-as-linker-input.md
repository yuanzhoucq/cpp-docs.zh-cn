---
title: 用作链接器输入的 .Pdb 文件
ms.date: 11/04/2016
helpviewer_keywords:
- .pdb files, as linker input
- PDB files, as linker input
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
ms.openlocfilehash: 23974a9e20f8259c3a38af15664d328ded7ff7d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628886"
---
# <a name="pdb-files-as-linker-input"></a>用作链接器输入的 .Pdb 文件

对象 (.obj) 文件使用了 /Zi 选项编译包含程序数据库 (PDB) 的名称。 未指定链接器; 的对象的 PDB 文件名称链接使用嵌入的名称，如果需要查找 PDB。 这同样适用于可调试库; 中包含的对象可调试库的 PDB 必须可供随同库一起链接器。

链接还使用 PDB 来保存.exe 文件或.dll 文件的调试信息。 该程序的 PDB 是输出文件和输入的文件，因为链接在重新生成该程序时更新 PDB。

## <a name="see-also"></a>请参阅

[LINK 输入文件](../../build/reference/link-input-files.md)<br/>
[链接器选项](../../build/reference/linker-options.md)