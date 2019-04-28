---
title: 项目生成错误 PRJ0008
ms.date: 11/04/2016
f1_keywords:
- PRJ0008
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
ms.openlocfilehash: 5741b7ef8cb9a7ae53d64874d3531e9271c09e0f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359483"
---
# <a name="project-build-error-prj0008"></a>项目生成错误 PRJ0008

无法删除文件 file。

**请确保文件未被另一个进程打开并且未被写保护。**

在重新生成或清理，但 VisualC++删除所有已知中间文件和输出文件的生成，以及符合中的通配符规范的任何文件**删除的扩展插件**中的属性[常规配置设置属性页](../../build/reference/general-property-page-project.md)。

你将看到此错误，如果 VisualC++不能删除文件。 若要解决此错误，使该文件，其目录可写在生成的用户。