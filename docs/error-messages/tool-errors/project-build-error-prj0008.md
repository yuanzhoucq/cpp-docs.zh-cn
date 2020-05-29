---
title: 项目生成错误 PRJ0008
ms.date: 11/04/2016
f1_keywords:
- PRJ0008
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
ms.openlocfilehash: 7d1c11ab7539f25d371c0bfbd2853b6155c9661c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192947"
---
# <a name="project-build-error-prj0008"></a>项目生成错误 PRJ0008

无法删除文件 "file"。

**请确保该文件未被其他进程打开并且未被写保护。**

在重新生成或清理过程中C++ ，视觉对象将删除生成的所有已知中间文件和输出文件，以及在 "[常规配置设置" 属性页](../../build/reference/general-property-page-project.md)中的 "**清理时要删除的扩展**" 属性中满足通配符规范的任何文件。

如果视觉对象C++无法删除文件，则会看到此错误。 若要解决此错误，请为执行生成的用户将文件及其目录设置为可写。
