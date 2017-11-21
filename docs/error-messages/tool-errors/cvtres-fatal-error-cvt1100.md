---
title: "CVTRES 错误 CVT1100 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CVT1100
dev_langs: C++
helpviewer_keywords: CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ba8ea3fdfdea9ca5aa142a1f2a8f15c5d3ac536a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cvtres-fatal-error-cvt1100"></a>CVTRES 错误 CVT1100
重复的资源-类型:、 名称:、 语言： 语言、 标志： 标志、 大小：  
  
 已多次指定给定的资源。  
  
 如果链接器正在创建类型库，并且你未指定，可能发生此错误[/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md)和你的项目中的资源已使用 1。 在这种情况下，指定 /TLBID 并指定最大为 65535 的另一个数。