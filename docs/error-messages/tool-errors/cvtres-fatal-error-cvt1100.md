---
title: CVTRES 错误 CVT1100
ms.date: 11/04/2016
f1_keywords:
- CVT1100
helpviewer_keywords:
- CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
ms.openlocfilehash: b7e67df24d41b1e8826673146fcc27fd93d143fd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196542"
---
# <a name="cvtres-fatal-error-cvt1100"></a>CVTRES 错误 CVT1100

重复的资源-类型：类型，名称：名称，语言：语言，标志：标志，大小：大小

给定的资源已指定多次。

如果链接器正在创建类型库，但未指定[/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md)并且项目中的资源已使用1，则会出现此错误。 在这种情况下，请指定/TLBID，并指定另一个数字，最大为65535。
