---
title: 项目生成错误 PRJ0031
ms.date: 11/04/2016
f1_keywords:
- PRJ0031
helpviewer_keywords:
- PRJ0031
ms.assetid: b42435c6-e570-4f8e-9ad5-12a7ea69ccb2
ms.openlocfilehash: e13236f65aaca778a297cdd2942c07b75dd701d0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192492"
---
# <a name="project-build-error-prj0031"></a>项目生成错误 PRJ0031

文件 "file" 的自定义生成步骤的 "输出" 属性包含 "宏"，其计算结果为 "macro_expansion"。

文件上的自定义生成步骤出现错误的输出可能是由于宏计算问题所致。 此错误还可能意味着路径格式不正确，包含文件路径中非法字符或字符的组合。

若要解决此错误，请修复宏或修复路径规范。 计算的路径是项目目录中的绝对路径。
