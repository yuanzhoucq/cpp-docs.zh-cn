---
title: 错误 C1900
ms.date: 11/04/2016
f1_keywords:
- C1900
helpviewer_keywords:
- C1900
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
ms.openlocfilehash: 6a802928315126b72397ba6e8cc61b66f46deb41
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202835"
---
# <a name="fatal-error-c1900"></a>错误 C1900

> "*Tool1*" 版本 "*数字 1*" 与 "*tool2*" 版本 "*数字 2*" 之间的 Il 不匹配

编译器的各种 pass 中运行的工具不匹配。 *数字 1*和*数字 2*指文件的日期。 例如，在 pass 1 中，编译器前端运行 (c1.dll)，而在 pass 2 中，编译器后端运行 (c2.dll)。 文件上的日期必须匹配。

若要解决此问题，请确保 Visual Studio 已应用所有的更新。 如果问题仍然存在，请使用 Windows 控制面板中的 "**程序和功能**" 修复或重新安装 Visual Studio。
