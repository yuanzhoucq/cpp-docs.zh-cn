---
title: 资源编译器警告 RW4004 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW4004
dev_langs:
- C++
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33305f1f86c0cc1722e4a235ec27927f6e70675f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095984"
---
# <a name="resource-compiler-warning-rw4004"></a>资源编译器警告 RW4004

ASCII 字符不等价于虚拟键代码

字符串文本已用于 VIRTKEY 类型快捷键中的虚拟键代码。

此警告允许你继续操作，但请注意，生成的快捷键可能与你指示的字符串不匹配。 （VIRTKEYs 与 ASCII 快捷键使用不同的键代码。）

当字符串文本在语法上有效时，您只能确保获取你想使用的加速器**VK_\* #define** WINDOWS.h 中的值。