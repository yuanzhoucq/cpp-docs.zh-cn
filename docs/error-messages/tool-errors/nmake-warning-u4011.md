---
title: NMAKE 警告 U4011 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U4011
dev_langs:
- C++
helpviewer_keywords:
- U4011
ms.assetid: e8244514-eba6-4285-8853-7baeefdcd8a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af9c0f90c507eebe212a9c3cbfb2f2d21cded43d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320790"
---
# <a name="nmake-warning-u4011"></a>NMAKE 警告 U4011
'target': 可用; 不是所有依赖项未生成的目标  
  
 给定的目标的从属项不存在或已过期，并且用于更新从属的命令返回非零退出代码。 /K 选项告知 NMAKE 以继续处理生成的相关的部分并完成 NMAKE 会话后颁发退出代码为 1。  
  
 此警告前面是警告[U4010](../../error-messages/tool-errors/nmake-warning-u4010.md)有关未能创建或更新每个依赖项。