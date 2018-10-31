---
title: CVTRES 错误 CVT1100
ms.date: 11/04/2016
f1_keywords:
- CVT1100
helpviewer_keywords:
- CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
ms.openlocfilehash: c7e65ccc79852ec99dd2406398fe1b3cdecacde7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429297"
---
# <a name="cvtres-fatal-error-cvt1100"></a>CVTRES 错误 CVT1100

重复的资源-类型： 类型、 名称： 名称、 语言： 语言、 标志： 标志、 大小： 大小

多次指定了给定的资源。

如果链接器创建类型库，并且未指定出现此错误的[/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md)和你的项目中的资源已使用 1。 在这种情况下，指定 /TLBID 并指定最多 65535 的另一个数。