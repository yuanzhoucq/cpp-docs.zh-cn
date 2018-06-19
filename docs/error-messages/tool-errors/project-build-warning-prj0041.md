---
title: 项目生成警告 PRJ0041 |Microsoft 文档
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
ms.openlocfilehash: 6e845967b0a7116d6edade98b571de5bc1bcd9a1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318056"
---
# <a name="project-build-warning-prj0041"></a>项目生成警告 PRJ0041
找不到缺少依赖项依赖关系文件 file。 你的项目仍然可以生成，但可能会一直显示过期，直到找到此文件。  
  
 一个文件 （资源文件或.idl/.odl 文件，例如，包含项目系统无法解析一个 include 语句。  
  
 由于项目系统不会处理预处理器语句 (例如 #if)，则有问题的语句可能不会实际会生成的一部分。  
  
 若要解决此警告，删除所有不必要的代码在.rc 文件中或添加占位符文件的适当的名称。