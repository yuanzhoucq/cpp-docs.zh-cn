---
title: "链接器工具错误 LNK1223 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1223
dev_langs: C++
helpviewer_keywords: LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c330077e8de73b8eeb71b0a418eb89d2ec0ebfdc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1223"></a>链接器工具错误 LNK1223
无效或已损坏的文件： 文件包含无效的.pdata 基值  
  
 对于使用 pdata 的 RISC 平台，如果编译器发出具有无序条目的 .pdata 部分，则将发生此错误。  
  
 若要解决此问题，请尝试编译而不[/GL （全程序优化）](../../error-messages/tool-errors/linker-tools-error-lnk1223.md)启用。 在某些情况下，空的函数体也可能导致此错误。