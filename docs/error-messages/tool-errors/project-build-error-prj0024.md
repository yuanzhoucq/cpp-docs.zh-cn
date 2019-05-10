---
title: 项目生成错误 PRJ0024
ms.date: 08/27/2018
f1_keywords:
- PRJ0024
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
ms.openlocfilehash: 645b898bdffcc6d7b397c25eb3c41cea25cb361f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384096"
---
# <a name="project-build-error-prj0024"></a>项目生成错误 PRJ0024

> Unicode 路径*路径*未能翻译成用户的 ANSI 代码页。

*路径*是原始的 Unicode 版本的路径字符串。 在情况下会出现此错误的不能直接转换为 ANSI 的当前系统代码页的 Unicode 路径。

如果您正在使用开发项目使用代码页不在您的计算机上的系统上可能出现此错误。

此错误的解决方法是更新路径以使用 ANSI 文本，或在计算机上安装的代码页，并将其设置为系统默认值。