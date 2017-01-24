---
title: "项目生成错误 PRJ0016 | Microsoft Docs"
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
  - "PRJ0016"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0016"
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 项目生成错误 PRJ0016
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用户的安全设置禁止创建该进程。这些设置是生成所必需的。  
  
 登录用的用户身份不具有使用进程创建进程的权限。  必须更改此用户帐户的权限级别，或者与帐户管理员联系。  
  
 如果设置了以下注册表项，也可能发生该错误：  
  
 \\\\HKCU\\Software\\Microsoft\\Windows\\CurrentVersion\\Policies\\Explorer\\RestrictRun  
  
 若要解决此错误，请删除 RestrictRun 项。  如果需要此注册表项，则将 **vcspawn.exe** 追加到该注册表项中条目的列表后。  
  
 此错误的另一种原因是：对于此用户帐户，“策略设置”未将注册表项 HKEY\_CURRENT\_USER\\Software\\Microsoft\\Windows\\CurrentVersion\\Policies\\RestrictRun 下的 VCSpawn.exe 作为允许的 Window 程序包含在内。  
  
 有关附加信息，请参见：  
  
-   知识库文章 324153，可打开 [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;324153](http://support.microsoft.com/default.aspx?scid=kb;en-us;324153)。  
  
-   [遵循系统策略设置](http://msdn.microsoft.com/library/aa372139)，“Run only allowed Windows applications”中的一节。