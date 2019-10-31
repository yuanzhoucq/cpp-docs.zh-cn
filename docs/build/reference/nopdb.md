---
title: /NOPDB
description: /NOPDB 选项使 DUMPBIN 无法加载和搜索 PDB 文件中的符号信息。
ms.date: 10/29/2019
f1_keywords:
- /NOPDB
helpviewer_keywords:
- /NOPDB dumpbin option
- /NOPDB
ms.openlocfilehash: 3b745049517888d13de245d4e29be3985c122ada
ms.sourcegitcommit: 6ed1bc5b26dc60a780c1fc5f2f19d57ba1dc47d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73145745"
---
# <a name="nopdb"></a>/NOPDB

告诉 DUMPBIN 不加载和搜索程序数据库（PDB）文件中的符号信息。

## <a name="syntax"></a>语法

> **/NOPDB**

## <a name="remarks"></a>备注

默认情况下，DUMPBIN 会尝试为其目标对象文件、库或可执行文件加载 PDB 文件。 DUMPBIN 使用此信息将地址与符号名称匹配。 如果 PDB 文件较大，或者必须从远程服务器加载，则进程可能会非常耗时。 **/NOPDB**选项告知 DUMPBIN 跳过此步骤。 它仅打印对象文件、库或可执行文件中可用的地址和符号信息。

### <a name="to-set-the-nopdb-linker-option-in-visual-studio"></a>在 Visual Studio 中设置/NOPDB 链接器选项

1. 打开项目的 "**属性页**" 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择“配置属性” > “链接器” > “命令行”属性页。

1. 在 "**附加选项**" 框中，添加 **/NOPDB**选项。 选择 **"确定" 或 "** **应用**" 保存更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 此选项不具有编程等效项。

## <a name="see-also"></a>请参阅

[DUMPBIN 命令行](dumpbin-command-line.md)\
[DUMPBIN 选项](dumpbin-options.md)\
[DUMPBIN 引用](dumpbin-reference.md)
