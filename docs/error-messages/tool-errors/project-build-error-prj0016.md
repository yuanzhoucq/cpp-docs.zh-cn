---
title: 项目生成错误 PRJ0016
ms.date: 11/04/2016
f1_keywords:
- PRJ0016
helpviewer_keywords:
- PRJ0016
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
ms.openlocfilehash: 6733ef1f390f2ff377356dda3f7cd3ebfe10cc2b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509881"
---
# <a name="project-build-error-prj0016"></a>项目生成错误 PRJ0016

用户的安全设置阻止创建进程。 这些设置是生成所必需的。

你以无权使用进程创建进程的用户身份登录。 必须更改此用户帐户的权限级别, 或与帐户管理员联系。

如果设置了以下注册表项, 也会发生此错误:

\\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun

若要解决此错误, 请删除 RestrictRun 项。 如果需要此注册表项, 请将**vcspawn**追加到项中的项列表。

导致此错误的另一个原因是, 策略设置不会在注册表项 HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun 下包含 VCSpawn 作为此用户帐户的允许的窗口程序。

有关其他信息, 请参阅 "仅运行允许的 Windows 应用程序" 部分中的 "[坚持使用系统策略设置](/previous-versions/windows/desktop/Policy/adhering-to-system-policy-settings)"。