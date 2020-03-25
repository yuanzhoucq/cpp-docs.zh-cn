---
title: 命令行警告 D9025
ms.date: 11/04/2016
f1_keywords:
- D9025
helpviewer_keywords:
- D9025
ms.assetid: 6edff72c-1508-46c2-99f4-0e4b3c5e60c9
ms.openlocfilehash: 4afd4d4dc07ffaae6038c025ee371278ebbebea6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196711"
---
# <a name="command-line-warning-d9025"></a>命令行警告 D9025

重写 "选项 1" 和 "选项 2"

已指定*选项 1*选项，但已被*选项 2*重写。 使用了*选项 2*选项。

如果两个选项指定了矛盾或不兼容的指令，则使用命令行右侧最远的选项中指定或隐含的指令。

如果在从开发环境中进行编译时收到此警告，并不确定冲突选项来自何处，请注意以下事项：

- 可以在代码或项目的项目设置中指定一个选项。 如果查看编译器的 "[命令行" 属性页](../../build/reference/command-line-property-pages.md)，并且在 "**所有选项**" 字段中看到冲突的选项，则会在项目的属性页中设置这些选项，否则将在源代码中设置这些选项。

   如果在项目的属性页中设置这些选项，请查看编译器的预处理器属性页（在 "解决方案资源管理器中选择" 项目 "节点）。  如果看不到 "设置" 选项，请检查每个源代码文件的预处理器属性页设置（在解决方案资源管理器中）以确保不会将其添加到其中。

   如果在代码中设置这些选项，则可以在代码或 windows 标头中设置这些选项。  您可以尝试创建一个预处理文件（[/p](../../build/reference/p-preprocess-to-a-file.md)），然后在该文件中搜索符号。
