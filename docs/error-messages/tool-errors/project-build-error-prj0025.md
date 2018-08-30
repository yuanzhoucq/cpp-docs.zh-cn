---
title: 项目生成错误 PRJ0025 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0025
dev_langs:
- C++
helpviewer_keywords:
- PRJ0025
ms.assetid: 57725c78-bc63-44f3-9667-2969b2d7c41d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 949e36424fc213459e56332c0802d2719581bac1
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209807"
---
# <a name="project-build-error-prj0025"></a>项目生成错误 PRJ0025

> 批处理文件*文件*包含未能翻译成用户的 ANSI 代码页的 Unicode 内容。
>
> *UNICODE 文件的内容*

项目系统找到在自定义的 Unicode 内容生成规则或生成事件不能正确翻译成用户的当前 ANSI 代码页。

此错误的解决方法是更新生成规则的内容或生成事件以使用 ANSI 或在计算机上安装的代码页，并将其设置为系统默认值。

有关详细信息自定义生成步骤和生成事件，请参阅[了解自定义生成步骤和生成事件](../../ide/understanding-custom-build-steps-and-build-events.md)。