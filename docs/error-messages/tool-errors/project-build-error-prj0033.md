---
title: 项目生成错误 PRJ0033
ms.date: 11/04/2016
f1_keywords:
- PRJ0033
helpviewer_keywords:
- PRJ0033
ms.assetid: 84d4a052-0586-4b78-9315-81c1e8386c1e
ms.openlocfilehash: 141355ac49ec4722e85b5d4c25240e8048a72c9a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192180"
---
# <a name="project-build-error-prj0033"></a>项目生成错误 PRJ0033

文件 "file" 的自定义生成步骤的 "附加依赖项" 属性包含 "宏"，其计算结果为 "macro_expansion"。

文件上的自定义生成步骤在其附加依赖项中包含错误可能是由宏计算问题引起的。 此错误还可能意味着路径格式不正确，包含文件路径中非法字符或字符的组合。

若要解决此错误，请修复宏或修复路径规范。 计算的路径是项目目录中的绝对路径。
