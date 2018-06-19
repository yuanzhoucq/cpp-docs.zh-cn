---
title: 项目生成错误 PRJ0016 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0016
dev_langs:
- C++
helpviewer_keywords:
- PRJ0016
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6184e5bb251a2b74e8500cc195a38f2d814c1b5f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319047"
---
# <a name="project-build-error-prj0016"></a>项目生成错误 PRJ0016
用户的安全设置阻止从正在创建的过程。 这些设置是生成所必需的。  
  
 您没有权限来创建使用一个进程的进程的用户身份登录。 你必须更改此用户帐户的权限级别，或联系你的帐户管理员。  
  
 如果设置以下注册表项，也可能发生此错误：  
  
 \\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun  
  
 若要解决此错误，删除 RestrictRun 密钥。 如果需要此注册表项，则追加**vcspawn.exe**到的项中的条目的列表。  
  
 此错误的另一个原因是，你的策略设置不包括 VCSpawn.exe 注册表项 HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun 下作为此用户帐户的允许窗口程序。  
  
 有关其他信息，请参阅：  
  
-   知识库文章 324153，可在找到[ http://support.microsoft.com/default.aspx?scid=kb; en-我们; 324153](http://support.microsoft.com/default.aspx?scid=kb;en-us;324153)。  
  
-   [遵守系统策略设置](http://msdn.microsoft.com/library/aa372139)，在"仅运行许可的 Windows 应用程序"部分。