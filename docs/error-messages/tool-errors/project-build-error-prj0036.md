---
title: 项目生成错误 PRJ0036
ms.date: 11/04/2016
f1_keywords:
- PRJ0036
helpviewer_keywords:
- PRJ0036
ms.assetid: ee215cd1-2d66-474d-9a63-b9096f1c4923
ms.openlocfilehash: 9b9232583c464548167e22d0104e0c6098093eab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435277"
---
# <a name="project-build-error-prj0036"></a>项目生成错误 PRJ0036

Web 部署工具的附加文件属性包含无效项。

Web 部署属性页上的其他文件属性包含一个错误，可能是因为宏计算问题。 此错误还可能意味着路径有格式错误，其中包含的字符或在文件路径中是非法的字符的组合。

若要解决此错误，请修复该宏或修复所指定的路径。 计算出的路径是从项目目录的绝对路径。

此错误还可能表示一个引用的文件不存在。