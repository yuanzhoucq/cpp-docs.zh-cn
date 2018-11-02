---
title: 项目生成警告 PRJ0041
ms.date: 11/04/2016
f1_keywords:
- PRJ0041
helpviewer_keywords:
- PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
ms.openlocfilehash: b0fceff05ffe35515965b7e0a880c8b4c941b07e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583204"
---
# <a name="project-build-warning-prj0041"></a>项目生成警告 PRJ0041

找不到缺少依赖项的文件 file 的依赖关系。 你的项目仍然可以生成，但可能会一直显示直到找到此文件已过期。

一个文件 （资源文件或.idl/.odl 文件，例如，包含项目系统无法解析一个 include 语句。

项目系统不会处理预处理器语句 (例如 #if)，因为有问题的语句可能实际上不是生成的一部分。

若要解决此警告，请删除.rc 文件中的所有不必要的代码或添加具有相应名称的占位符文件。