---
title: "项目生成错误 PRJ0050 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0050
dev_langs: C++
helpviewer_keywords: PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e9d9b123da2e32db0f695c31bc9643a481d352b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0050"></a>项目生成错误 PRJ0050
未能注册输出。 请确保你具有适当的权限来修改注册表。  
  
 Visual c + + 生成系统无法注册 （dll 或.exe） 的生成输出。 你需要以管理员身份来修改注册表登录。  
  
 如果要生成.dll，你可以尝试注册手动使用 regsvr32.exe.dll，这应该会显示有关生成失败的原因的信息。  
  
 如果你不生成.dll，查看引起错误的命令生成日志。