---
title: "编译器警告 （等级 1） C4678 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4678
dev_langs:
- C++
helpviewer_keywords:
- C4678
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: d35e60d60d194bc0ca68a116dc45b6d9864d9fe2
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4678"></a>编译器警告（等级 1）C4678
基类“base_type”的可访问性比“derived_type”低  
  
某个公共类型是从私有类型派生的。 如果在引用的程序集中实例化该公共类型，将无法访问私有基类型的成员。  
  
C4678 才可使用已过时的编译器选项连接**/clr:oldSyntax**。 在使用时，则会发生错误**/clr**，以便具有可访问性的基类，其派生的类。  

