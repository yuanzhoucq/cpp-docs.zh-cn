---
title: 设置链接器选项
ms.date: 11/04/2016
helpviewer_keywords:
- files [C++], LINK
- input files [C++], linker
- linker [C++], ways to set options
- linker [C++], switches
- input files [C++]
- object/library modules
ms.assetid: e08fb487-0f2e-4f24-87db-232dbc8bd2e2
ms.openlocfilehash: 61f4ee8d02cda5b2cd270d7ef789bf58060e7fdf
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423165"
---
# <a name="setting-linker-options"></a>设置链接器选项

内部或外部的开发环境，可以设置链接器选项。 每个链接器选项的主题讨论如何在开发环境中设置。 请参阅[链接器选项](../../build/reference/linker-options.md)有关的完整列表。

当您在开发环境外部运行链接时，可以在一个或多个方面来指定输入：

- 在[命令行](../../build/reference/linker-command-line-syntax.md)

- 使用[命令文件](../../build/reference/link-command-files.md)

- 在[环境变量](../../build/reference/link-environment-variables.md)

链接第一个处理指定的选项在链接的环境变量中，然后按照它们在命令行指定的顺序和命令文件中的选项。 如果一个选项重复使用不同的参数，处理的最后一个优先。

选项适用于整个生成;无选项可以应用于特定的输入文件。

## <a name="see-also"></a>请参阅

[C/C++ 生成参考](../../build/reference/c-cpp-building-reference.md)<br/>
[链接器选项](../../build/reference/linker-options.md)
