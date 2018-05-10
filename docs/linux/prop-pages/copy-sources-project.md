---
title: 复制源项目属性 (Linux C++) | Microsoft Docs
ms.custom: ''
ms.date: 9/26/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 1a44230d-5dd8-4d33-93b4-e77e03e00150
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: d13bc7c129696e2b7251ccb23b68338956864321
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="copy-sources-project-properties-linux-c"></a>复制源项目属性 (Linux C++)

此属性页上设置的属性适用于项目中所有的文件，除设置了文件级属性的文件外。

属性 | 描述
--- | ---
要复制的源 | 指定要复制到远程系统的源。 更改此列表可能转变或者影响目录结构，文件将在其中被复制到远程系统。
复制源文件 | 指定是否要将源复制到远程系统。
要复制的其他源 | 指定要复制到远程系统的其他源。 根据需要，可使用类似 fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2 的语法以本地到远程的映射对形式提供列表，其中可将本地文件复制到远程系统的指定远程位置。
