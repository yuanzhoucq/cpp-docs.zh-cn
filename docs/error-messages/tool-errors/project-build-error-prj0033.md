---
title: "项目生成错误 PRJ0033 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0033
dev_langs: C++
helpviewer_keywords: PRJ0033
ms.assetid: 84d4a052-0586-4b78-9315-81c1e8386c1e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ab3cd4cdac74e7c64bfd786beb7aab147d5cdd82
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="project-build-error-prj0033"></a>项目生成错误 PRJ0033
自定义生成的附加依赖项属性为文件 file 包含 macro 计算出结果进入 macro_expansion。  
  
 文件上的自定义生成步骤包含在其原因可能是宏评估问题的附加依赖项时出错。 此错误还可能表示该路径格式错误，包含字符或在文件路径中是非法的字符的组合。  
  
 若要解决此错误，请修复宏或修复所指定的路径。 计算出的路径是从项目目录的绝对路径。