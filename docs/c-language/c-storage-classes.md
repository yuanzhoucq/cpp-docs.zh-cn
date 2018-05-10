---
title: C 存储类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- static variables, lifetime
- storage classes
- lifetime, variables
- specifiers, storage class
- storage class specifiers, C storage classes
- storage duration
ms.assetid: 893fb929-f7a9-43dc-a0b3-29cb1ef845c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 089f2298cac21ac9fff0d25a76e9393cddb84bba
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="c-storage-classes"></a>C 存储类
变量的“存储类”可确定项是具有“全局”还是“本地”生存期。 C 将这两个生存期称为“静态”和“自动”。 具有全局生存期的项存在且具有贯穿整个程序执行过程的值。 所有函数都具有全局生存期。  
  
 每次执行控制权传递到从中定义它们的块时，都会为自动变量或具有本地生存期的变量分配新存储。 当执行返回时，这些变量不再具有有意义的值。  
  
 C 提供了以下存储类说明符：  
  
## <a name="syntax"></a>语法  
 *storage-class-specifier*：  
 **auto**  
  
 **register**  
  
 **static**  
  
 **extern**  
  
 **typedef**  
  
 __declspec ( extended-decl-modifier-seq ) /* Microsoft 专用 \*/  
  
 除 `__declspec` 之外，只能在声明中的 declaration-specifier 中使用一个 storage-class-specifier。 如果没有制定存储类规范，块中的声明将创建自动对象。  
  
 使用 auto 或 register 说明符声明的项具有本地生存期。 使用 static 或 `extern` 说明符声明的项具有全局生存期。  
  
 由于 `typedef` 和 `__declspec` 与其他四个 storage-class-specifier 终端的语义不同，因此将分开讨论它们。 有关 `typedef` 的特定信息，请参阅 [Typedef 声明](../c-language/typedef-declarations.md)。 有关 `__declspec` 的特定信息，请参阅[扩展的存储类特性](../c-language/c-extended-storage-class-attributes.md)。  
  
 源文件中变量和函数声明的位置还会影响存储类和可见性。 所有函数定义之外的声明据说显示在“外部级别”。 函数定义中的声明显示在“内部级别”。  
  
 每个存储类说明符的确切含义取决于两个因素：  
  
-   声明是显示在外部还是内部级别  
  
-   要声明的项是变量还是函数  
  
 [用于外部级别声明的存储类说明符](../c-language/storage-class-specifiers-for-external-level-declarations.md)和[用于内部级别的存储类说明符](../c-language/storage-class-specifiers-for-internal-level-declarations.md)介绍了每种声明中的 storage-class-specifier 终端并解释了从变量中省略 storage-class-specifier 时的默认行为。 [存储类说明符与函数声明](../c-language/storage-class-specifiers-with-function-declarations.md)讨论了与函数一起使用的存储类说明符。  
  
## <a name="see-also"></a>请参阅  
 [声明和类型](../c-language/declarations-and-types.md)