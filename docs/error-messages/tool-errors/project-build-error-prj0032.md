---
title: 项目生成错误 PRJ0032
ms.date: 11/04/2016
f1_keywords:
- PRJ0032
helpviewer_keywords:
- PRJ0032
ms.assetid: bc6acbea-4041-4237-8b5a-f0434705d89f
ms.openlocfilehash: f1f292f3979c993a8fa8cb8ff44653ac7124b121
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499825"
---
# <a name="project-build-error-prj0032"></a>项目生成错误 PRJ0032

项目级自定义生成步骤的输出属性包含计算为 macro_expansion 的宏。

项目的自定义生成步骤具有错误的输出，很可能是由于宏计算问题。 此错误还可能意味着路径有格式错误，其中包含的字符或在文件路径中是非法的字符的组合。

若要解决此错误，请修复该宏或修复所指定的路径。 计算出的路径是从项目目录的绝对路径。