---
title: 链接器工具错误 LNK1188 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1188
dev_langs:
- C++
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e31943ae253a332576fba73102db410b103a0096
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1188"></a>链接器工具错误 LNK1188
BADFIXUPSECTION:: 无效的修正目标 symbol;可能零长度部分  
  
 在 VxD 链接，期间的重定位的目标没有一个部分。 与 LINK386 （较旧版本），（由 MASM 组指令生成） OMF 组记录可能已使用来合并另一个非零长度部分具有零长度的部分。 COFF 格式不支持组指令和零长度部分。 链接会自动将此类型的 OMF 对象转换到 COFF，可能会发生此错误。