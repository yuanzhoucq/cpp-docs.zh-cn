---
title: 项目生成错误 PRJ0009
ms.date: 11/04/2016
f1_keywords:
- PRJ0009
helpviewer_keywords:
- PRJ0009
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
ms.openlocfilehash: d02325504b04a13cd15dee0bd70891bf5a63b62e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192952"
---
# <a name="project-build-error-prj0009"></a>项目生成错误 PRJ0009

未能打开生成日志以进行写入。

**请确保该文件未被其他进程打开并且未被写保护。**

在将**生成日志记录**属性设置为 **"是"** 并执行生成或重新C++生成后，视觉对象无法以独占模式打开生成日志。

通过打开 "**选项**" 对话框（在 "**工具**" 菜单上单击 "**选项**" 命令），然后选择 "**项目**" 文件夹中的 " **VC + + 生成**" 来检查**生成日志记录**设置。 生成文件称为 Buildlog.htm，并写入中间目录 $ （IntDir）。

此错误的可能原因：

- 正在运行两个视觉C++进程，并尝试同时在这两个过程中生成相同项目的相同配置。

- 在锁定文件的进程中打开生成日志文件。

- 用户没有创建文件的权限。

- 当前用户对文件 Buildlog.htm 没有写入访问权限。
