---
title: "错误 C1305 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1305
dev_langs:
- C++
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: cf4a9025b8d441ae42b7de7605594fda60dc5603
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1305"></a>错误 C1305
配置文件数据库 pgd_file 是用于不同的体系结构  
  
 /Ltcg: pginstrument 操作的另一个平台传递到已生成的.pgd 文件[/ltcg: pgoptimize](../../build/reference/ltcg-link-time-code-generation.md) 。 [按配置优化](../../build/reference/profile-guided-optimizations.md)可用于 x86 和[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]平台。 但是，与为平台 /ltcg: pginstrument 操作生成的.pgd 文件不是有效作为输入到 /ltcg: pgoptimize 为不同的平台。  
  
 若要解决此错误，仅传递使用 /ltcg: pginstrument 到 /ltcg: pgoptimize 同一平台上创建一个.pgd 文件。
