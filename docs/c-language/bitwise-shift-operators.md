---
title: "按位移位运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "按位移位运算符"
  - "运算符 [C++], 按位"
  - "运算符 [C++], 移位"
  - "移位运算符, 按位"
ms.assetid: d0485785-5c72-47e1-a7c0-0adde03ade23
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 按位移位运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

移位运算符按第二个操作数指定的位置数量向左 \(`<<`\) 或向右 \(`>>`\) 移动第一个操作数。  
  
## 语法  
 *shift\-expression*:  
 *additive\-expression*  
  
 *shift\-expression*  `<<`  *additive\-expression shift\-expression*  `>>`  *additive\-expression*  
  
 两个操作数都必须是整数值。  这些运算符执行常用算术转换；结果的类型是转换后左操作数的类型。  
  
 对于左移，留空的右位将设置为 0。  对于右移，将根据转换后第一个操作数的类型填充留空的左位。  如果该类型为 `unsigned`，留空的左位将设置为 0。  否则，将使用符号位的副本填充它们。  对于没有溢出的左移运算符，语句  
  
```  
expr1 << expr2   
```  
  
 等效于乘以 2<sup>expr2</sup>。  对于右移运算符，  
  
```  
expr1 >> expr2   
```  
  
 等效于除以 2<sup>expr2</sup>（如果 `expr1` 无符号或具有非负值）。  
  
 如果第二个操作数为负，或者右操作数大于或等于提升后的左操作数的宽度（以位为单位），则移位运算的结果不确定的。  
  
 由于没有为溢出或下溢情况提供移位运算符执行的转换，因此当移位运算的结果不能用转换后第一个操作数的类型表示时，信息可能丢失。  
  
```  
unsigned int x, y, z;  
  
x = 0x00AA;  
y = 0x5500;  
  
z = ( x << 8 ) + ( y >> 8 );  
```  
  
 在此示例中，`x` 将向左移位 8 个位置，`y` 将向右移位 8 个位置。  移位值（假定 0xAA55）将相加并赋给 `z`。  
  
 将负值向右移位可生成原始值一半的值（向下舍入）。  例如，–253（二进制 11111111 00000011）向右移动 1 位会生成 –127（二进制 11111111 10000001）。  将 \+ 253 向右移位生成 \+126。  
  
 右移保留符号位。  当带符号的整数向右移位时，最高有效位将保留。  当无符号的整数右移位时，将清除最高有效位。  
  
## 请参阅  
 [左移和右移运算符（\>\> 和 \<\<）](../cpp/left-shift-and-right-shift-operators-input-and-output.md)