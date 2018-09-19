---
title: 链接器工具警告 LNK4075 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4075
dev_langs:
- C++
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a021a9345975dcb197ab578901baf22f76db846
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059649"
---
# <a name="linker-tools-warning-lnk4075"></a>链接器工具警告 LNK4075

忽略由于"option2"规范"选项 1"

第二个选项可重写第一个。

指定互相排斥的链接器选项。  检查链接器选项。  指定链接器选项的位置取决于如何构建您的项目。

- 如果您正在构建开发环境中，查看你的项目，链接器属性页并了解这两个链接器选项的指定位置。  请参阅[使用项目属性](../../ide/working-with-project-properties.md)有关详细信息。

- 如果在命令行生成时，查看此处指定的链接器选项。

- 如果生成使用生成脚本，仔细查看您的脚本，请参阅这些链接器选项指定的位置。

找到指定互斥链接器选项的位置后，删除其中一个链接器选项。

一些特定的示例：

- 如果使用编译时将模块链接 **/ZI**，这意味着内部链接器选项调用意味着没有 /EDITANDCONTINUE /EDITANDCONTINUE，并使用 /opt: ref，/opt: icf 或 /incremental: no，已编译的模块，将获取 LNK4075。  请参阅[/Z7、 /Zi、 /ZI （调试信息格式）](../../build/reference/z7-zi-zi-debug-information-format.md)有关详细信息。