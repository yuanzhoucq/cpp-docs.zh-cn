---
title: "BSCMAKE 错误 BK1517 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: BK1517
dev_langs: C++
helpviewer_keywords: BK1517
ms.assetid: 24391f42-0a3e-40a9-9991-c8b9a6a7b1c7
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5978ceab4a5a5e768ddda635398466bb941c42cd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="bscmake-error-bk1517"></a>BSCMAKE 错误 BK1517
sbrfile 用 /Yc 和 /Yu 编译的源文件  
  
 .Sbr 文件引用自身。 它用 /Yc 编译后用 /Yu 可能重新编译。 源文件的文件名将编译器选项重置 /yc，然后选择**重新生成**生成新的.sbr 文件。 没有重新编译 /Yu 的源文件。