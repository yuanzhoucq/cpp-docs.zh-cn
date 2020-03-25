---
title: 项目生成错误 PRJ0006
ms.date: 11/04/2016
f1_keywords:
- PRJ0006
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
ms.openlocfilehash: 816355276a203adba1401841ce02eb94a18085b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192778"
---
# <a name="project-build-error-prj0006"></a>项目生成错误 PRJ0006

无法打开临时文件 "file"。 请确保该文件存在，并且该目录不是写保护的。

视觉C++对象无法在生成过程中创建临时文件。 此问题的原因包括：

- 无临时目录。

- 只读临时目录。

- 磁盘空间不足。

- $ （IntDir）文件夹是只读的，或者包含只读的临时文件。

错误 PRJ0007：无法创建输出目录 "directory" 时，也会发生此错误。 错误 PRJ0007 表示无法创建 $ （IntDir）目录，这意味着临时文件的创建也会失败。

每次指定时都会创建临时文件：

- 响应文件。

- 自定义生成步骤。

- 生成事件。
