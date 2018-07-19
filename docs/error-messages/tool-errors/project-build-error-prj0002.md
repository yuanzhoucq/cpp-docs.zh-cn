---
title: 项目生成错误 PRJ0002 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0002
dev_langs:
- C++
helpviewer_keywords:
- PRJ0002
ms.assetid: 1c820b1f-9a24-4681-80ed-4fcbfd7caa00
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 54e1870ce9137ba172f848a499dd31133119eea0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318271"
---
# <a name="project-build-error-prj0002"></a>项目生成错误 PRJ0002
返回从命令行错误结果。  
  
 将命令，***命令行***，其中的格式中的用户输入从**属性页**对话框中，返回错误代码，但没有信息将显示在输出窗口。  
  
 对此错误的解决方法取决于哪一种工具生成错误。 对于 MIDL，你将了解发生的问题，如果定义 /o （重定向输出）。  
  
 批处理文件，如自定义生成步骤或生成事件，不提供有关失败条件有用的信息也可能是导致此错误的原因。