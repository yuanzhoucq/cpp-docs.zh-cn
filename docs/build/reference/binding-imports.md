---
title: 绑定导入
ms.date: 11/04/2016
helpviewer_keywords:
- /DELAY:NOBIND linker option
- DELAY:NOBIND linker option
ms.assetid: bb766038-deb1-41b1-bcbc-29a30e8c1e2a
ms.openlocfilehash: 90af3af7e71928b18c77c0d21ff6a30c4561e251
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415235"
---
# <a name="binding-imports"></a>绑定导入

默认链接器行为是为延迟加载的 DLL 创建可绑定导入地址表。 如果绑定了 DLL，该帮助器函数将尝试使用绑定的信息，而不是调用**GetProcAddress**上每个引用的导入。 如果时间戳或首选的地址不匹配的加载的 DLL，helper 函数将假定绑定导入地址表已过时，并将继续进行，如同它不存在。

如果从不打算绑定 DLL 的延迟加载导入，则指定[/延迟](../../build/reference/delay-delay-load-import-settings.md): nobind 链接器的命令行上将阻止绑定导入地址表中的图像文件的生成和使用空间。

## <a name="see-also"></a>请参阅

[延迟加载 DLL 的链接器支持](../../build/reference/linker-support-for-delay-loaded-dlls.md)
