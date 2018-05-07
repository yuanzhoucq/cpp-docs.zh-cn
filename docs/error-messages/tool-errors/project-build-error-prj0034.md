---
title: 项目生成错误 PRJ0034 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0034
dev_langs:
- C++
helpviewer_keywords:
- PRJ0034
ms.assetid: 1da4a55b-231b-4476-8545-6997628fbc00
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a65ca2c53ba2801f861471c66f7e1f2ec8766345
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="project-build-error-prj0034"></a>项目生成错误 PRJ0034
项目级自定义的附加依赖项属性生成包含步骤 macro 等于 macro_expansion。  
  
 项目的自定义生成步骤包含在其原因可能是宏评估问题的附加依赖项时出错。 此错误还可能表示该路径格式错误，包含字符或在文件路径中是非法的字符的组合。  
  
 若要解决此错误，请修复宏或修复所指定的路径。 计算出的路径是从项目目录的绝对路径。