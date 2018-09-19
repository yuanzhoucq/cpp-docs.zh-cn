---
title: 图像格式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 3ca3654b-42fe-4253-9f2e-723644041aa0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e69d1a7c62d4e9c52cc628f30f94c346d83647f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715411"
---
# <a name="image-format"></a>图像格式

可执行映像格式是 PE32 +。 可执行映像 （Dll 和 Exe） 是 2 千兆字节的最大大小限制为的因此使用 32 位偏移量相对地址可用于处理静态图像数据。 此数据包括导入地址表、 字符串常量，静态全局数据等。

## <a name="see-also"></a>请参阅

[x64 软件约定](../build/x64-software-conventions.md)