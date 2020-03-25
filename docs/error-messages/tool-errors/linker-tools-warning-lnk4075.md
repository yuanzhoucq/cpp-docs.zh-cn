---
title: 链接器工具警告 LNK4075
ms.date: 11/04/2016
f1_keywords:
- LNK4075
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
ms.openlocfilehash: e4a385b9559e2f54e81bda76e6dd13505e978a74
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183483"
---
# <a name="linker-tools-warning-lnk4075"></a>链接器工具警告 LNK4075

由于 "选项 2" 规范，忽略 "选项 1"

第二个选项重写第一个选项。

正在指定互斥链接器选项。  检查链接器选项。  链接器选项的指定位置取决于生成项目的方式。

- 如果在开发环境中生成，请查看项目的链接器属性页，并查看两个链接器选项的指定位置。  有关详细信息，请参阅[设置编译器和生成属性](../../build/working-with-project-properties.md)。

- 如果在命令行中生成，请查看此处指定的链接器选项。

- 如果使用生成脚本进行生成，请查看脚本，以查看在何处指定这些链接器选项。

如果找到指定了互斥链接器选项的位置，请删除其中一个链接器选项。

一些具体的示例：

- 如果链接使用 **/zi**编译的模块（这表示名为/EDITANDCONTINUE 的内部链接器选项）和使用/OPT： REF、/OPT： ICF 或/INCREMENTAL： no 编译的模块，则会收到 LNK4075。  有关详细信息，请参阅[/Z7、/zi、/zi （调试信息格式）](../../build/reference/z7-zi-zi-debug-information-format.md) 。
