---
title: "项目生成错误 PRJ0019 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0019"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0019"
ms.assetid: 5390a62b-aacf-4bc8-b9d7-08f1e0233423
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 项目生成错误 PRJ0019
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

工具从以下位置返回错误  
  
 自定义生成步骤或生成事件的错误等级是非零值。  
  
 如果工具返回了错误代码而无错误信息，您也会看到 PRJ0019 错误。  例如，如果将 MIDL 的输出重定向到 NUL，则会发生此错误。  
  
 有关更多信息，请参见[自定义生成步骤和生成事件疑难解答](../../ide/troubleshooting-build-customizations.md)。  
  
 当需要管理访问权限，而您却作为 Users 组的成员运行时，也会发生此错误。  有关详细信息，请参阅[作为用户组的成员运行](../../top/running-as-a-member-of-the-users-group.md)。