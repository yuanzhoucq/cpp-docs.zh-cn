---
title: 转储延迟加载的导入
ms.date: 11/04/2016
helpviewer_keywords:
- delay-loaded imports, dumping
- imports (delay-loaded)
- delay-loaded imports
ms.assetid: f766acf4-9df8-4b85-8cf6-0be3ffc4c124
ms.openlocfilehash: 368c6b851340dd2a39df9a758f15d52ff5104479
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271861"
---
# <a name="dumping-delay-loaded-imports"></a>转储延迟加载的导入

可以使用转储延迟加载的导入[dumpbin /imports](imports-dumpbin.md)和显示，其略有不同的信息不是标准导入。 它们被隔离到它们自己的 /imports 转储的部分，并显式标记为延迟加载的导入。 如果卸载图片中包含的信息，该记录。 如果没有出现的绑定信息，以及导入的绑定地址记录目标 DLL 的时间/日期戳。

## <a name="see-also"></a>请参阅

[延迟加载 DLL 的链接器支持](linker-support-for-delay-loaded-dlls.md)
