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
ms.openlocfilehash: b8e4725c8781a27cb22c554b614464cf7eb232a5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="bscmake-error-bk1517"></a>BSCMAKE 错误 BK1517
sbrfile 用 /Yc 和 /Yu 编译的源文件  
  
 .Sbr 文件引用自身。 它用 /Yc 编译后用 /Yu 可能重新编译。 源文件的文件名将编译器选项重置 /yc，然后选择**重新生成**生成新的.sbr 文件。 没有重新编译 /Yu 的源文件。