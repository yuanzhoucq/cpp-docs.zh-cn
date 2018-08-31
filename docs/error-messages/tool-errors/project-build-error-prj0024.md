---
title: 项目生成错误 PRJ0024 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0024
dev_langs:
- C++
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb539a5f1ee5f1aa5f9d828d93fa6d0dc8690c22
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215593"
---
# <a name="project-build-error-prj0024"></a>项目生成错误 PRJ0024

> Unicode 路径*路径*未能翻译成用户的 ANSI 代码页。

*路径*是原始的 Unicode 版本的路径字符串。 在情况下会出现此错误的不能直接转换为 ANSI 的当前系统代码页的 Unicode 路径。

如果您正在使用开发项目使用代码页不在您的计算机上的系统上可能出现此错误。

此错误的解决方法是更新路径以使用 ANSI 文本，或在计算机上安装的代码页，并将其设置为系统默认值。