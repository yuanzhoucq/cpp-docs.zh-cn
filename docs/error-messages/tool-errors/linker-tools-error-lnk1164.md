---
title: 链接器工具错误 LNK1164 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1164
dev_langs:
- C++
helpviewer_keywords:
- LNK1164
ms.assetid: da89765c-affa-4f88-b170-6d6b19a577cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f85ad1c223c9d4b22e3763f1d24a6c2631f6342d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297415"
---
# <a name="linker-tools-error-lnk1164"></a>链接器工具错误 LNK1164
部分节对齐 （数字） 大于 /ALIGN 值  
  
 对象文件中的给定部分的对齐方式大小超过用指定的值[/对齐](../../build/reference/align-section-alignment.md)选项。 **/对齐**值必须是 2 的幂和必须等于或超过对象文件中给定的部分对齐方式。  
  
 重新编译，以较小节对齐或增加 **/对齐**值。