---
title: 项目生成警告 PRJ0049
ms.date: 11/04/2016
helpviewer_keywords:
- PRJ0049
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
ms.openlocfilehash: e857a50215dc7516c0e2ec45a97638c76f40f43b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191739"
---
# <a name="project-build-warning-prj0049"></a>项目生成警告 PRJ0049

引用的目标 "\<引用 >" 需要 .NET Framework \<MinFrameworkVersion > 并且将无法在此项目的目标框架上运行

使用 Visual Studio 2008 创建的应用程序可以指定其目标 .NET Framework 的版本。 如果添加对依赖于高于目标版本的 .NET Framework 版本的程序集或项目的引用，则将在编译时收到此警告。

### <a name="to-correct-this-warning"></a>更正此警告

1. 选择以下之一：

   - 在项目的 "**属性页**" 对话框中更改目标框架，使其晚于或等于所有引用的程序集和项目的最小 framework 版本。 有关详细信息，请参阅[添加引用](../../build/adding-references-in-visual-cpp-projects.md)。

   - 删除对具有低于目标框架的最小 framework 版本的程序集或项目的引用。 这些项将在项目的**属性页**中用警告图标标记。

## <a name="see-also"></a>另请参阅

[项目生成错误和警告 (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)
