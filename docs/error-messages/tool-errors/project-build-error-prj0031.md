---
title: 项目生成错误 PRJ0031 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0031
dev_langs:
- C++
helpviewer_keywords:
- PRJ0031
ms.assetid: b42435c6-e570-4f8e-9ad5-12a7ea69ccb2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d5ebd25c239a05c4300b574ec0d47035904187d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318316"
---
# <a name="project-build-error-prj0031"></a>项目生成错误 PRJ0031
自定义生成的 Outputs 属性为文件 file 包含 macro 计算出结果进入 macro_expansion。  
  
 文件的自定义生成步骤具有可能由于宏计算问题发生的错误输出。 此错误还可能表示该路径格式错误，包含字符或在文件路径中是非法的字符的组合。  
  
 若要解决此错误，请修复宏或修复所指定的路径。 计算出的路径是从项目目录的绝对路径。