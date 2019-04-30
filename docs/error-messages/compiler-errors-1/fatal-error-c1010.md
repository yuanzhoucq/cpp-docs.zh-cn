---
title: 错误 C1010
ms.date: 11/04/2016
f1_keywords:
- C1010
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
ms.openlocfilehash: 6974f0d82653203973be50b5ea709bd9487a215f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363968"
---
# <a name="fatal-error-c1010"></a>错误 C1010

查找预编译头时意外的文件尾。 是否忘记添加 #include 名称到您的源？

使用指定的包含文件[/Yu](../../build/reference/yu-use-precompiled-header-file.md)源文件中未列出。  在大多数的视觉对象默认情况下启用此选项C++项目类型和"stdafx.h"是默认值包括此选项指定的文件。

在 Visual Studio 环境中，使用以下方法之一来解决此错误：

- 如果在项目中不使用预编译标头，设置**创建/使用预编译标头**源文件复制到的属性**不使用预编译标头**。 若要设置此编译器选项，请按照下列步骤：

   1. 在项目的解决方案资源管理器窗格中，右键单击项目名称，然后单击**属性**。

   1. 在左窗格中，单击**C /C++** 文件夹。

   1. 单击**预编译标头**节点。

   1. 在右窗格中，单击**创建/使用预编译标头**，然后单击**不使用预编译标头**。

- 请确保不会无意中删除、 重命名或删除标头文件 (默认情况下，stdafx.h) 从当前项目。 此文件还需要使用在源文件中的任何其他代码之前包含 **#include"stdafx.h"**。 (此标头文件指定为**通过文件创建/使用 PCH**项目属性)