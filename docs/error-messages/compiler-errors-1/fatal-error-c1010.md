---
title: 错误 C1010
ms.date: 08/19/2019
f1_keywords:
- C1010
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
ms.openlocfilehash: 35b0f60f7eb3be887598e7ffaf3e3eae74aefcff
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630787"
---
# <a name="fatal-error-c1010"></a>错误 C1010

查找预编译头时意外的文件尾。 是否忘记将 "#include 名称" 添加到源？

使用[/yu](../../build/reference/yu-use-precompiled-header-file.md)指定的包含文件未列在源文件中。  默认情况下, 在大多数 Visual Studio C++项目类型和*Pch* (visual Studio 2017 及更早版本) 中启用此选项, 这是此选项指定的默认包含文件。

在 Visual Studio 环境中, 使用以下方法之一来解决此错误:

- 如果在项目中不使用预编译头, 则将源文件的**Create/Use 预编译标头**属性设置为 "**不使用预编译标**头"。 若要设置此编译器选项, 请执行以下步骤:

   1. 在项目的解决方案资源管理器窗格中, 右键单击项目名称, 然后单击 "**属性**"。

   1. 在左窗格中, 单击 " **C/C++** 文件夹"。

   1. 单击 "**预编译头**" 节点。

   1. 在右侧窗格中, 单击 "**创建/使用预编译标头**", 然后单击 "**不使用预编译标头**"。

- 确保你没有无意中删除、重命名或删除了当前项目中的头文件 (默认情况下为 stdafx.h)。 还需要在使用 **#include "stdafx.h"** 的源文件中的任何其他代码之前包含此文件。 (此标头文件被指定为 "**通过文件项目创建/使用 PCH** " 属性)