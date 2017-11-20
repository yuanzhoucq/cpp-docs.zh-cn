---
title: "C 字符常量 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- characters, constants
- (') single quotation mark
- constants, character
- single quotation mark
ms.assetid: 388ae7d7-2c3a-44d6-a507-63f541ecd2da
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 70525e774ea7c89cbd767b607a142d338b797df3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="c-character-constants"></a>C 字符常量
“字符常量”通过在单引号 (' ') 内封闭可表示的字符集中的单个字符来构成。 字符常量用于表示[执行字符集](../c-language/execution-character-set.md)内的字符。  
  
## <a name="syntax"></a>语法  
 *character-constant*：  
 “ c-char-sequence ”  
  
 L” c-char-sequence “  
  
 *c-char-sequence*:  
 *c-char*  
  
 *c-char-sequence c-char*  
  
 *c-char*:  
 除单引号 (')、反斜杠 (\\) 或者换行符以外的所有源字符集成员  
  
 escape-sequence  
  
 *escape-sequence*:  
 *simple-escape-sequence*  
  
 *octal-escape-sequence*  
  
 *hexadecimal-escape-sequence*  
  
 *simple-escape-sequence*: one of  
 **\a \b \f \n \r \t \v**  
  
 **\\' \\" \\\ \\?**  
  
 *octal-escape-sequence*:  
 \\  octal-digit  
  
 \\  octal-digit octal-digit  
  
 \\  octal-digit octal-digit octal-digit  
  
 *hexadecimal-escape-sequence*：  
 **\x**  *hexadecimal-digit*  
  
 *hexadecimal-escape-sequence hexadecimal-digit*  
  
## <a name="see-also"></a>另请参阅  
 [C 常量](../c-language/c-constants.md)