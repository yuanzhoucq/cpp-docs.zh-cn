---
title: 模块定义语句的规则
ms.date: 11/04/2016
f1_keywords:
- .def
helpviewer_keywords:
- module definition files, statement syntax
- module definition files
ms.assetid: f65cd3a7-65d7-4d06-939f-a8b1ecd50f2d
ms.openlocfilehash: 6d6528b81777711e52153e19a656619a2895b0d6
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424751"
---
# <a name="rules-for-module-definition-statements"></a>模块定义语句的规则

下面的语法规则适用于.def 文件中的所有语句。 每个语句描述了适用于特定语句的其他规则。

- 语句、 属性关键字和用户指定的标识符是区分大小写。

- 长文件名包含空格或分号 （;） 的名称必须括在引号 （"）。

- 使用一个或多个空格、 制表符或换行字符来分隔语句关键字与它的参数并将每个语句分隔。 冒号 （:） 或等号 （=），它将指定参数括在零或多个空格、 制表符或换行字符。

- 一个**名称**或**库**语句中，如果使用，必须所有其他语句之前。

- **各节**并**导出**语句可以出现不止一次在.def 文件中。 每个语句可能需要多个规范，必须由一个或多个空格、 制表符或换行字符分隔。 语句关键字必须出现一次在第一个规范之前，可以重复之前每个其他规范。

- 许多语句都具有等效的链接命令行选项。 请参阅其他详细信息的相应链接选项的说明。

- .Def 文件中的注释指定由分号 （;） 在每个注释行的开头。 注释不能使用一条语句，共享一条线路，但它可以出现多行语句中的规范之间。 (**各节**并**导出**是多行语句。)

- 数值参数是指定十进制或十六进制。

- 如果字符串自变量与匹配[保留字](../../build/reference/reserved-words.md)，它必须括在双引号 （"）。

## <a name="see-also"></a>请参阅

[模块定义 (.Def) 文件](../../build/reference/module-definition-dot-def-files.md)
