---
title: 项目生成错误 PRJ0034
ms.date: 11/04/2016
f1_keywords:
- PRJ0034
helpviewer_keywords:
- PRJ0034
ms.assetid: 1da4a55b-231b-4476-8545-6997628fbc00
ms.openlocfilehash: bcb7e22d6a09e3435eb2236532101a1836c08a03
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192178"
---
# <a name="project-build-error-prj0034"></a>项目生成错误 PRJ0034

项目级自定义生成步骤的 "附加依赖项" 属性包含 "宏"，其计算结果为 "macro_expansion"。

项目上的自定义生成步骤包含其附加依赖项中的错误，这可能是由于宏计算问题所致。 此错误还可能意味着路径格式不正确，包含文件路径中非法字符或字符的组合。

若要解决此错误，请修复宏或修复路径规范。 计算的路径是项目目录中的绝对路径。
