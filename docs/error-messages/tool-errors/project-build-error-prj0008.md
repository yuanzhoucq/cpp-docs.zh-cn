---
title: 项目生成错误 PRJ0008
ms.date: 11/04/2016
f1_keywords:
- PRJ0008
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
ms.openlocfilehash: 696b77e9906b231a680027a3faaf23e53d8fb6e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525896"
---
# <a name="project-build-error-prj0008"></a>项目生成错误 PRJ0008

无法删除文件 file。

**请确保文件未被另一个进程打开并且未被写保护。**

重新生成或清理期间，Visual c + + 删除所有已知中间文件和输出文件的生成，以及符合中的通配符规范的任何文件**删除的扩展**属性中的[常规配置设置属性页](../../ide/general-property-page-project.md)。

如果 Visual c + + 不能删除文件，您将看到此错误。 若要解决此错误，使该文件，其目录可写在生成的用户。