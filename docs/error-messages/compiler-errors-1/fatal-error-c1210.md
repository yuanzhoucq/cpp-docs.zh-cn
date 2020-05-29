---
title: 错误 C1210
ms.date: 11/04/2016
f1_keywords:
- C1210
helpviewer_keywords:
- C1210
ms.assetid: e2208309-c284-425c-a7e8-48e96e66f35b
ms.openlocfilehash: 50bafa522c931c909b5ce163a78305ffc028765a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203380"
---
# <a name="fatal-error-c1210"></a>错误 C1210

> 安装的运行时版本不支持 /clr:pure 和 /clr:safe

**/Clr： pure**和 **/clr： safe**编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

使用的编译器是当前版本而公共语言运行时是早期版本时将发生 C1210。

编译器的一些功能在早期的运行时版本中可能无效。

若要解决 C1210，请安装适用于你的编译器的公共语言运行时版本。
