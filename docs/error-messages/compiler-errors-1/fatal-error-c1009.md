---
title: "错误 C1009 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1009
dev_langs: C++
helpviewer_keywords: C1009
ms.assetid: dcc8383c-3362-4c47-9c26-25d2451ebd53
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 92d91240ea092ff75387246952ce5b7207527173
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1009"></a>错误 C1009
编译器限制： 宏嵌套太深  
  
 编译器尝试在同一时间展开太多的宏。 编译器已限制为 256 级别的嵌套宏。 嵌套的宏拆分为更简单的宏。