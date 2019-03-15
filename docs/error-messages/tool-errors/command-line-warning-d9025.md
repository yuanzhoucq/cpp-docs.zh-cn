---
title: 命令行警告 D9025
ms.date: 11/04/2016
f1_keywords:
- D9025
helpviewer_keywords:
- D9025
ms.assetid: 6edff72c-1508-46c2-99f4-0e4b3c5e60c9
ms.openlocfilehash: e7090dda72868ad7ee4d5f8e4f1ba6a0ad121c98
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822453"
---
# <a name="command-line-warning-d9025"></a>命令行警告 D9025

重写"选项 1"与"选项 2"

*Option1*选项指定了，但然后重写*option2*。 *Option2*选项已使用。

如果两个选项指定相互矛盾的或不兼容的指令，则使用命令行上最右侧的选项中指定或隐含的指令。

如果在从开发环境中，编译时收到此警告，并且不确定冲突的选项来自哪里，考虑以下方面：

- 在代码中或在项目的项目设置中，可以指定一个选项。 如果您看一下编译器的[命令行属性页](../../build/reference/command-line-property-pages.md)如果你看到中的选项冲突**所有选项**字段选项在项目的属性页，否则为设置选项，然后在源代码中设置。

   如果项目的属性页中设置了选项，查看在编译器的预处理器属性页上 （使用解决方案资源管理器中选择的项目节点）。  如果您看不到选项集存在，检查每个源代码文件 （在解决方案资源管理器） 的预处理器属性页设置以确保它不存在添加。

   如果在代码中设置了选项可以在代码中或在 windows 头文件中设置它。  您可以尝试创建预处理过的文件 ([/P](../../build/reference/p-preprocess-to-a-file.md)) 并在其中搜索符号。