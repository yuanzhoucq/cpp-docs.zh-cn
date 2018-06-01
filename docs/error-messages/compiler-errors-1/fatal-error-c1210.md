---
title: 错误 C1210 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1210
dev_langs:
- C++
helpviewer_keywords:
- C1210
ms.assetid: e2208309-c284-425c-a7e8-48e96e66f35b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d22a34f44fb2c97fe341cb313d7917a35506cdd
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704979"
---
# <a name="fatal-error-c1210"></a>错误 C1210

> 安装的运行时版本不支持 /clr:pure 和 /clr:safe

**/Clr: pure**和 **/clr: safe**编译器选项是在 Visual Studio 2015 中已过时，在 Visual Studio 2017 中不支持。

使用的编译器是当前版本而公共语言运行时是早期版本时将发生 C1210。

编译器的一些功能在早期的运行时版本中可能无效。

若要解决 C1210，请安装适用于你的编译器的公共语言运行时版本。