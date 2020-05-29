---
title: 项目生成错误 PRJ0036
ms.date: 11/04/2016
f1_keywords:
- PRJ0036
helpviewer_keywords:
- PRJ0036
ms.assetid: ee215cd1-2d66-474d-9a63-b9096f1c4923
ms.openlocfilehash: 67a225f907d06cd240ec2ebef236c0b4e0b849e2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192090"
---
# <a name="project-build-error-prj0036"></a>项目生成错误 PRJ0036

Web 部署工具的 "附加文件" 属性包含无效项。

Web 部署属性页上的 "其他文件" 属性包含错误，可能是由于宏计算问题引起的。 此错误还可能意味着路径格式不正确，包含文件路径中非法字符或字符的组合。

若要解决此错误，请修复宏或修复路径规范。 计算的路径是项目目录中的绝对路径。

此错误还可能意味着引用的一个文件不存在。
