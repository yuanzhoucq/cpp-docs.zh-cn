---
title: 错误 C1900
ms.date: 11/04/2016
f1_keywords:
- C1900
helpviewer_keywords:
- C1900
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
ms.openlocfilehash: c4622dd4552f7bfcc822a3aab4d5783146d68ac7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581852"
---
# <a name="fatal-error-c1900"></a>错误 C1900

> 之间的 Il 不匹配*tool1*版本*number1*'和'*tool2*版本*number2*

编译器的各种 pass 中运行的工具不匹配。 *number1*并*number2*文件引用的日期。 例如，在 pass 1 中，编译器前端运行 (c1.dll)，而在 pass 2 中，编译器后端运行 (c2.dll)。 文件上的日期必须匹配。

若要解决此问题，请确保 Visual Studio 已应用所有的更新。 如果问题仍然存在，请使用**程序和功能**Windows 控制面板来修复或重新安装 Visual Studio 中。