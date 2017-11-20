---
title: "C 整数常量 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: integer constants
ms.assetid: fcf6b83c-2038-49ec-91ca-3d5ca1f83037
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 20025ae47491084436864481357125e741ccc486
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="c-integer-constants"></a>C 整数常量
“整数常量”是表示整数值的十进制（基数为 10）、八进制（基数为 8）或十六进制（基数为 16）数字。 使用整数常量表示不能更改的整数值。  
  
## <a name="syntax"></a>语法  
 *integer-constant*:  
 *decimal-constant integer-suffix* opt  
  
 *octal-constant integer-suffix* opt  
  
 *hexadecimal-constant integer-suffix* opt  
  
 *decimal-constant*:  
 *nonzero-digit*  
  
 *decimal-constant digit*  
  
 *octal-constant*:  
 **0**  
  
 *octal-constant octal-digit*  
  
 *hexadecimal-constant*:  
 **0x**  *hexadecimal-digit*  
  
 **0X**  *hexadecimal-digit*  
  
 *hexadecimal-constant hexadecimal-digit*  
  
 *nonzero-digit*: one of  
 **1 2 3 4 5 6 7 8 9**  
  
 *octal-digit*: one of  
 **0 1 2 3 4 5 6 7**  
  
 *hexadecimal-digit*: one of  
 **0 1 2 3 4 5 6 7 8 9**  
  
 **a b c d e f**  
  
 **A B C D E F**  
  
 *integer-suffix*:  
 *unsigned-suffix long-suffix* opt  
  
 *long-suffix unsigned-suffix* opt  
  
 *unsigned-suffix*: one of  
 **u U**  
  
 *long-suffix*: one of  
 **l L**  
  
 *64-bit integer-suffix*:  
 **i64**  
  
 整数常量为正数，除非它们的前面有减号 (**-**)。 减号解释为一元算术求反运算符。 （有关此运算符的信息，请参阅[一元算术运算符](../c-language/unary-arithmetic-operators.md)。）  
  
 如果整数常量以 **0x** 或 **0X**  开始，则它是十六进制。 如果它以数字 **0** 开始，则为八进制。 否则，将其假定为十进制。  
  
 下列行是等效的：  
  
```  
0x1C   /* = Hexadecimal representation for decimal 28 */  
034    /* = Octal representation for decimal 28 */  
```  
  
 空白字符不能分隔整数常量的数字。 这些示例显示有效的十进制、八进制和十六进制常量。  
  
```  
/* Decimal Constants */  
10  
132  
32179  
  
/* Octal Constants */  
012  
0204  
076663  
  
/* Hexadecimal Constants */  
0xa or 0xA  
0x84  
0x7dB3 or 0X7DB3  
```  
  
## <a name="see-also"></a>另请参阅  
 [C 常量](../c-language/c-constants.md)