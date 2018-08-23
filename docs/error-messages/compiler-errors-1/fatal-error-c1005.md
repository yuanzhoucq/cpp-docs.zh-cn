---
title: 错误 C1005 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1005
dev_langs:
- C++
helpviewer_keywords:
- C1005
ms.assetid: 150daf8e-a38a-4669-9c1a-a05b5a1f65ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13ff7f5dbc1f9ecb66c54f52fae4a38d1e4d4664
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197710"
---
# <a name="fatal-error-c1005"></a>错误 C1005
字符串过大，无法缓冲  
  
 编译器中间文件内的字符串溢出了缓冲区。  
  
 当你传递到 [/Fd](../../build/reference/fd-program-database-file-name.md) 或 [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) 编译器选项的参数大于 256 个字节时，可能会遇到此错误。