---
title: 项目生成错误 PRJ0050 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0050
dev_langs:
- C++
helpviewer_keywords:
- PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb3949ea0db2f1667aecf1aeeefd922b192cbf41
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100586"
---
# <a name="project-build-error-prj0050"></a>项目生成错误 PRJ0050

未能注册输出。 请确保有适当的权限来修改注册表。

Visual c + + 生成系统无法注册 （dll 或.exe） 生成的输出。 您需要以修改注册表的管理员身份登录。

如果您正在构建.dll，可以尝试以注册.dll 手动使用 regsvr32.exe，此时应显示在生成失败的原因有关的信息。

如果您不构建.dll，查看将导致错误的命令生成日志。