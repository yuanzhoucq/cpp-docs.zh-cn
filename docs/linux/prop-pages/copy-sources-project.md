---
title: 复制源项目属性 (Linux C++)
ms.date: 06/07/2019
ms.assetid: 1a44230d-5dd8-4d33-93b4-e77e03e00150
ms.openlocfilehash: afc65fb7fbc3866081fbf7da6d3c5014ba1c268d
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821323"
---
# <a name="copy-sources-project-properties-linux-c"></a>复制源项目属性 (Linux C++)

::: moniker range="vs-2015"

Linux 支持在 Visual Studio 2017 及更高版本中提供。

::: moniker-end

::: moniker range=">=vs-2017"

此属性页上设置的属性适用于项目中所有的文件，除设置了文件级属性的文件外。

Property | 说明
--- | ---
要复制的源 | 指定要复制到远程系统的源。 更改此列表可能转变或者影响目录结构，文件将在其中被复制到远程系统。
复制源文件 | 指定是否要将源复制到远程系统。
要复制的其他源 | 指定要复制到远程系统的其他源。 根据需要，可使用类似 fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2 的语法以本地到远程的映射对形式提供列表，其中可将本地文件复制到远程系统的指定远程位置。

::: moniker-end
