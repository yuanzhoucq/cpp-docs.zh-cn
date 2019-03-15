---
title: 项目生成警告 PRJ0049
ms.date: 11/04/2016
helpviewer_keywords:
- PRJ0049
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
ms.openlocfilehash: fba3de0be764aa56b56ed22c6a9fde9366295456
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816225"
---
# <a name="project-build-warning-prj0049"></a>项目生成警告 PRJ0049

引用的目标 '\<引用 > 需要.NET Framework \<MinFrameworkVersion > 并将无法在此项目的目标框架上运行

通过使用 Visual Studio 2008 创建的应用程序可以指定应面向.NET Framework 的版本。 如果添加对程序集或依赖于晚于目标版本的.NET framework 版本的项目的引用，则会在编译时此警告。

### <a name="to-correct-this-warning"></a>若要更正此警告

1. 选择以下选项之一：

   - 更改在项目的目标的框架**属性页**对话框中，这样就晚于或等于最小的 framework 版本的所有引用的程序集和项目。 有关详细信息，请参阅[添加引用](../../build/adding-references-in-visual-cpp-projects.md)。

   - 删除对该程序集或晚于目标框架的最小的 framework 版本的项目的引用。 这些项都标有在项目的警告图标**属性页**。

## <a name="see-also"></a>请参阅

[项目生成错误和警告 (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)