---
title: 项目生成警告 PRJ0041
ms.date: 11/04/2016
f1_keywords:
- PRJ0041
helpviewer_keywords:
- PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
ms.openlocfilehash: bb6469b1daf193223a9b3361cc3e4bfb96d0c751
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191922"
---
# <a name="project-build-warning-prj0041"></a>项目生成警告 PRJ0041

找不到文件 "file" 缺少依赖项 "依赖项"。 你的项目仍可能会生成，但可能会在找到此文件之前继续显示。

例如，文件（资源文件或 .idl/odl 文件包含项目系统无法解析的 include 语句）。

因为项目系统不处理预处理器语句（例如 #if），所以有问题的语句实际上可能并不是生成的一部分。

若要解决此警告，请在 .rc 文件中删除所有不必要的代码，或添加相应名称的占位符文件。
