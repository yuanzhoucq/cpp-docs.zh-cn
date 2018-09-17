---
title: '@ （指定编译器响应文件） |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '@'
dev_langs:
- C++
helpviewer_keywords:
- response files, C/C++ compiler
- '@ compiler option'
- cl.exe compiler, specifying response files
ms.assetid: 400fffee-909d-4f60-bf76-45833e822685
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c86d49aea2ce7a8d8b438c64cd883b71e5a4646
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720845"
---
# <a name="-specify-a-compiler-response-file"></a>@（指定编译器响应文件）

指定编译器响应文件。

## <a name="syntax"></a>语法

> **\@**<em>response_file</em>

## <a name="arguments"></a>自变量

*response_file*<br/>
包含编译器的命令的文本文件。

## <a name="remarks"></a>备注

响应文件可以包含将在命令行指定任何命令。 如果命令行自变量超过 127 个字符，这可能很有用。

不能指定**\@** 选项响应文件中。 也就是说，响应文件不能嵌入另一个响应文件。

从命令行中，您可以指定任意多个响应文件选项 (例如， `@respfile.1 @respfile.2`) 所需。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

- 响应文件不能从开发环境中指定，也必须在命令行指定。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 不能以编程方式更改此编译器选项。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)
