---
title: "链接器工具错误 LNK1166 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1166
dev_langs: C++
helpviewer_keywords: LNK1166
ms.assetid: d69548a8-0efb-44e1-90b7-b27636a4b575
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 44c71d074e950c857123bad5619bfa7a19fd1dff
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1166"></a>链接器工具错误 LNK1166
无法调整代码偏移量 = 偏移量，va = 值  
  
 链接无法填充所需的代码。  
  
 某些指令不允许在某些处理器上跨页边界。 链接尝试将添加填充代码来纠正这种情况。 在这种情况下，链接可能不解决此问题。