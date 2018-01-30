---
title: "输入流操控器 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- input streams, manipulators
- input stream objects
ms.assetid: 0addcacb-7b7b-4d70-9775-a59abc400fb3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ce3f1b99fe44d07a8793501c800f32077509ec0d
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2018
---
# <a name="input-stream-manipulators"></a>输入流操控器
许多操控器，如[setprecision](../standard-library/iomanip-functions.md#setprecision)，为定义`ios`类，因此应用到输入流。 但是，少数操控器实际上会影响输入流对象。 在这些会影响输入流对象的操控器中，最重要的是基数操控器 `dec`、`oct` 和 `hex`，它们决定输入流中数字使用的转换基数。  
  
 提取时，`hex` 操控器会启用对多种输入格式的处理。 例如，c、C、0xc、0xC、0Xc 和 0XC 会全部被解释为十进制整数 12。 0 - 9、A - F、a - f、x 和 X 以外的任何字符都会终止数值转换。 因此，序列 `"124n5"` 会转换为数字 124，位集为 [basic_ios::fail](../standard-library/basic-ios-class.md#fail)。  
  
## <a name="see-also"></a>请参阅  
 [输入流](../standard-library/input-streams.md)

