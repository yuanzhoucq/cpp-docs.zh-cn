---
title: "链接器工具错误 LNK1188 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1188
dev_langs: C++
helpviewer_keywords: LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 81d2988742eb9e8cd6aef134510ac8272d3dd27c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1188"></a>链接器工具错误 LNK1188
BADFIXUPSECTION:: 无效的修正目标 symbol;可能零长度部分  
  
 在 VxD 链接，期间的重定位的目标没有一个部分。 与 LINK386 （较旧版本），（由 MASM 组指令生成） OMF 组记录可能已使用来合并另一个非零长度部分具有零长度的部分。 COFF 格式不支持组指令和零长度部分。 链接会自动将此类型的 OMF 对象转换到 COFF，可能会发生此错误。