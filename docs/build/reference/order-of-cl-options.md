---
title: CL 选项的顺序（C++）-Visual Studio
ms.date: 12/14/2018
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
ms.openlocfilehash: 6c57a68dd15d82a9d6a01bfe145374bda6eb1510
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439203"
---
# <a name="order-of-cl-options"></a>CL 选项的顺序

选项可以出现在 CL 命令行中的任何位置，但/link 选项除外，后者必须最后发生。 编译器以[CL 环境变量](cl-environment-variables.md)中指定的选项开始，然后从左到右读取命令行（按照其遇到的顺序处理命令文件）。 每个选项都适用于命令行上的所有文件。 如果 CL 遇到冲突的选项，它将使用最右侧的选项。

## <a name="see-also"></a>另请参阅

[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
