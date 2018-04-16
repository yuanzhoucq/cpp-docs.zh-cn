---
title: "链接器工具警告 LNK4010 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4010
dev_langs:
- C++
helpviewer_keywords:
- LNK4010
ms.assetid: 2824cf99-4174-4b60-a6e2-c01e9f1ee52d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 79f52338eea40c42cacf8b0880afe42b75037abc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4010"></a>链接器工具警告 LNK4010
无效的子系统数字版本号;假定的默认子系统版本  
  
 你可以指定图像的子系统的版本 ([/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md))。 每个子系统具有最低版本要求。 如果指定的版本低于最小值，将发生此警告，链接器将仅使用默认子系统。