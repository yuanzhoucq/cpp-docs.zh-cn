---
title: 项目生成错误 PRJ0016 |Microsoft Docs
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
ms.openlocfilehash: ceb004cba243d6e2e9c44aadcaa40670ef7a0bbb
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890252"
---
# <a name="project-build-error-prj0016"></a>项目生成错误 PRJ0016

用户的安全设置阻止从正在创建进程。 这些设置是生成所必需的。

以不具有创建使用进程的进程的权限的用户的身份登录。 你必须更改此用户帐户的权限级别或联系你的帐户管理员。

如果设置以下注册表项，也可能发生此错误：

\\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun

若要解决此错误，删除 RestrictRun 密钥。 如果需要此注册表项，则追加**vcspawn.exe**到列表项中的条目。

此错误的另一个原因是，您的策略设置不包括 VCSpawn.exe HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun 的注册表项下为此用户帐户允许窗口程序。

有关其他信息，请参阅[遵循系统策略设置](https://msdn.microsoft.com/library/aa372139)，针对"仅运行允许的 Windows 应用程序"部分中。