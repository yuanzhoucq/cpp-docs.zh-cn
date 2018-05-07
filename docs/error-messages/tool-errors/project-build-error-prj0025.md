---
title: 项目生成错误 PRJ0025 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0025
dev_langs:
- C++
helpviewer_keywords:
- PRJ0025
ms.assetid: 57725c78-bc63-44f3-9667-2969b2d7c41d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 087a5d5af8ed92bdd0446ae87af037acbfd38a95
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="project-build-error-prj0025"></a>项目生成错误 PRJ0025
批处理文件 file 包含无法转换为用户的 ANSI 代码页的 Unicode 内容。  
  
 ***UNICODE 文件的内容***  
  
 项目系统找到 Unicode 内容在自定义生成规则或生成事件中发现不正确转换为用户的当前 ANSI 代码页。  
  
 此错误的解决方法是生成规则的内容更新或生成事件以使用 ANSI 或在你的计算机上安装的代码页，并将其设置为系统默认值。  
  
 有关详细信息自定义生成步骤和生成事件，请参阅[了解自定义生成步骤和生成事件](../../ide/understanding-custom-build-steps-and-build-events.md)。