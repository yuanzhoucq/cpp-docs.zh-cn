---
title: "项目生成错误 PRJ0031 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0031
dev_langs:
- C++
helpviewer_keywords:
- PRJ0031
ms.assetid: b42435c6-e570-4f8e-9ad5-12a7ea69ccb2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f1c07145f42e1ad71fb6c2a3542d9014b7e33b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0031"></a>项目生成错误 PRJ0031
自定义生成的 Outputs 属性为文件 file 包含 macro 计算出结果进入 macro_expansion。  
  
 文件的自定义生成步骤具有可能由于宏计算问题发生的错误输出。 此错误还可能表示该路径格式错误，包含字符或在文件路径中是非法的字符的组合。  
  
 若要解决此错误，请修复宏或修复所指定的路径。 计算出的路径是从项目目录的绝对路径。