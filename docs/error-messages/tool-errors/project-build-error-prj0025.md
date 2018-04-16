---
title: "项目生成错误 PRJ0025 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0025
dev_langs:
- C++
helpviewer_keywords:
- PRJ0025
ms.assetid: 57725c78-bc63-44f3-9667-2969b2d7c41d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f99a57439e87e1841555c90326072ba1667b6b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0025"></a>项目生成错误 PRJ0025
批处理文件 file 包含无法转换为用户的 ANSI 代码页的 Unicode 内容。  
  
 ***UNICODE 文件的内容***  
  
 项目系统找到 Unicode 内容在自定义生成规则或生成事件中发现不正确转换为用户的当前 ANSI 代码页。  
  
 此错误的解决方法是生成规则的内容更新或生成事件以使用 ANSI 或在你的计算机上安装的代码页，并将其设置为系统默认值。  
  
 有关详细信息自定义生成步骤和生成事件，请参阅[了解自定义生成步骤和生成事件](../../ide/understanding-custom-build-steps-and-build-events.md)。