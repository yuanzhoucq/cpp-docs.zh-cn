---
title: "输入流操控器 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- input streams, manipulators
- input stream objects
ms.assetid: 0addcacb-7b7b-4d70-9775-a59abc400fb3
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 17242528dd2be4a72a763f34ee651fc170fea58c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="input-stream-manipulators"></a>输入流操控器
[setprecision]--brokenlink--(../Topic/not%20found:3ddde610-70cc-4cfa-8a89-3e83d1d356a8.md#setprecision) 等许多操控器已针对 `ios` 类加以定义，因此适用于输入流。 但是，少数操控器实际上会影响输入流对象。 在这些会影响输入流对象的操控器中，最重要的是基数操控器 `dec`、`oct` 和 `hex`，它们决定输入流中数字使用的转换基数。  
  
 提取时，`hex` 操控器会启用对多种输入格式的处理。 例如，c、C、0xc、0xC、0Xc 和 0XC 会全部被解释为十进制整数 12。 0 - 9、A - F、a - f、x 和 X 以外的任何字符都会终止数值转换。 因此，序列 `"124n5"` 会转换为数字 124，位集为 [basic_ios::fail](../standard-library/basic-ios-class.md#fail)。  
  
## <a name="see-also"></a>请参阅  
 [输入流](../standard-library/input-streams.md)

