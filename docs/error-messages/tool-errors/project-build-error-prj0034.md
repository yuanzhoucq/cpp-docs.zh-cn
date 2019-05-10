---
title: 项目生成错误 PRJ0034
ms.date: 11/04/2016
f1_keywords:
- PRJ0034
helpviewer_keywords:
- PRJ0034
ms.assetid: 1da4a55b-231b-4476-8545-6997628fbc00
ms.openlocfilehash: 7c078a3d2aef24df9151cb10f81c1b7423809e68
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347582"
---
# <a name="project-build-error-prj0034"></a>项目生成错误 PRJ0034

项目级自定义的附加依赖项属性生成包含的步骤宏计算为 macro_expansion。

上一个项目的自定义生成步骤中包含错误，其原因可能是宏评估问题的附加依赖项。 此错误还可能意味着路径有格式错误，其中包含的字符或在文件路径中是非法的字符的组合。

若要解决此错误，请修复该宏或修复所指定的路径。 计算出的路径是从项目目录的绝对路径。