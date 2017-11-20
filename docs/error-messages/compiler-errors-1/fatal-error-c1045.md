---
title: "错误 C1045 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1045
dev_langs: C++
helpviewer_keywords: C1045
ms.assetid: 766c2f89-4ecd-4281-adaa-14b270cc0829
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 523c717f2e3e3e7485cfbd1f4c2e7bf270b4e6a3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1045"></a>错误 C1045
编译器限制 : 链接规范嵌套太深  
  
 嵌套的外部对象超过编译器限制。 允许嵌套的外部项使用外部链接类型，如 `extern` “C++”。 减少嵌套的外部项的数量以解决该错误。