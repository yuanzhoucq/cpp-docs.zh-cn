---
title: "链接器工具错误 LNK1164 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1164
dev_langs:
- C++
helpviewer_keywords:
- LNK1164
ms.assetid: da89765c-affa-4f88-b170-6d6b19a577cf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b5c1a62430397f95f33a5a4bd6f5845b1746557d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1164"></a>链接器工具错误 LNK1164
部分节对齐 （数字） 大于 /ALIGN 值  
  
 对象文件中的给定部分的对齐方式大小超过用指定的值[/对齐](../../build/reference/align-section-alignment.md)选项。 **/对齐**值必须是 2 的幂和必须等于或超过对象文件中给定的部分对齐方式。  
  
 重新编译，以较小节对齐或增加**/对齐**值。