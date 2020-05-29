---
title: 项目生成错误 PRJ0035
ms.date: 08/27/2018
f1_keywords:
- PRJ0035
helpviewer_keywords:
- PRJ0035
ms.assetid: 0667116d-338c-40a4-972c-da875f778cb5
ms.openlocfilehash: 8486c4f62f637f6f7e9826a289c21f8f194eb9f3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192167"
---
# <a name="project-build-error-prj0035"></a>项目生成错误 PRJ0035

> XML 文件 "*file*" 包含无法翻译成用户的 ANSI 代码页的 Unicode 内容。
>
> *文件的 UNICODE 内容*

*文件*是创建为 Web 部署工具的命令行的 XML 文件。

项目系统在 Web 部署属性页上的某些属性中找到了 Unicode 字符，这些字符无法正确地转换为 ANSI。

此错误的解决方法是将属性的内容更新为使用 ANSI 或在计算机上安装代码页，并将其设置为系统默认值。
