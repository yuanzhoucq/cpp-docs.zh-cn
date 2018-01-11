---
title: "项目生成错误 PRJ0034 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0034
dev_langs: C++
helpviewer_keywords: PRJ0034
ms.assetid: 1da4a55b-231b-4476-8545-6997628fbc00
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e68097d234519cdea75875d355ef798672ad4b22
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0034"></a>项目生成错误 PRJ0034
项目级自定义的附加依赖项属性生成包含步骤 macro 等于 macro_expansion。  
  
 项目的自定义生成步骤包含在其原因可能是宏评估问题的附加依赖项时出错。 此错误还可能表示该路径格式错误，包含字符或在文件路径中是非法的字符的组合。  
  
 若要解决此错误，请修复宏或修复所指定的路径。 计算出的路径是从项目目录的绝对路径。