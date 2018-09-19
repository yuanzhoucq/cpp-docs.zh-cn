---
title: 项目生成警告 PRJ0041 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0041
dev_langs:
- C++
helpviewer_keywords:
- PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7677c5718783065f64e52f98f7ddbed76e905d2a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038134"
---
# <a name="project-build-warning-prj0041"></a>项目生成警告 PRJ0041

找不到缺少依赖项的文件 file 的依赖关系。 你的项目仍然可以生成，但可能会一直显示直到找到此文件已过期。

一个文件 （资源文件或.idl/.odl 文件，例如，包含项目系统无法解析一个 include 语句。

项目系统不会处理预处理器语句 (例如 #if)，因为有问题的语句可能实际上不是生成的一部分。

若要解决此警告，请删除.rc 文件中的所有不必要的代码或添加具有相应名称的占位符文件。