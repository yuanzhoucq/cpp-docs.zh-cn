---
title: 错误 C1084
ms.date: 11/04/2016
f1_keywords:
- C1084
helpviewer_keywords:
- C1084
ms.assetid: b2f273ef-3a14-4d5f-8ce0-7a11a0388fe6
ms.openlocfilehash: b0c8e6a8f8321dccdfd7cee128a4cf06cebda991
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501134"
---
# <a name="fatal-error-c1084"></a>错误 C1084

无法读取 filetype 文件：“file”: 消息

此错误通常是由编译器无法执行内部系统 API 调用造成的。 遇到此错误时显示的消息通常是由[_wcserror_s](../../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)或[FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage)生成的。

执行以下步骤可帮助解决 C1084 错误：

- 请确保指定的文件存在。

- 请确保设置了访问指定文件所需的相应权限。

- 请确保命令行语法符合[编译器命令行语法](../../build/reference/compiler-command-line-syntax.md)中所述的规则。

- 请确保正确设置环境变量**TMP**和**TEMP** , 并确保访问这些环境变量所引用的目录的适当权限。 还要确保**TMP**和**TEMP**环境变量所引用的驱动器包含足够的可用空间。

- 如果消息指出“文件号错误”，说明指定的文件在后台进行编译的同时，可能已在前台关闭。

执行上面的诊断后，请执行干净的生成。