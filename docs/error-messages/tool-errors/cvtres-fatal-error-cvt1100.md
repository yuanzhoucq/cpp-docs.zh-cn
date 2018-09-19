---
title: CVTRES 错误 CVT1100 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CVT1100
dev_langs:
- C++
helpviewer_keywords:
- CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18a5508301c54637fb34a751c8f1c4e307e47d50
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068957"
---
# <a name="cvtres-fatal-error-cvt1100"></a>CVTRES 错误 CVT1100

重复的资源-类型： 类型、 名称： 名称、 语言： 语言、 标志： 标志、 大小： 大小

多次指定了给定的资源。

如果链接器创建类型库，并且未指定出现此错误的[/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md)和你的项目中的资源已使用 1。 在这种情况下，指定 /TLBID 并指定最多 65535 的另一个数。