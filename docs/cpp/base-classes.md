---
title: "基类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "基类"
  - "基类, virtual"
  - "派生类, 多个基类"
  - "继承, 多个"
  - "多重继承, 基类"
  - "虚拟基类"
ms.assetid: 6e6d54d0-6f21-4a16-9103-22935d98f596
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 基类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

继承过程将创建一个新的派生类，它由基类的成员加上派生类添加的任何新成员组成。  在多重继承中，可以构建一个继承关系图，其中相同的基类是多个派生类的一部分。  下图显示了此类关系图。  
  
 ![基类的多个实例](../cpp/media/vc38xn1.png "vc38XN1")  
单个基类的多个实例  
  
 在该图中，显示了 `CollectibleString` 和 `CollectibleSortable` 的组件的图形化表示形式。  但是，基类 `Collectible` 位于通过 `CollectibleSortableString` 路径和 `CollectibleString` 路径的 `CollectibleSortable` 中。  若要消除此冗余，可以在继承此类类时将其声明为虚拟基类。  
  
 有关声明虚拟基类以及如何构建带虚拟基类的对象的信息，请参阅[虚拟基类](../misc/virtual-base-classes.md)。  
  
## 请参阅  
 [派生类概述](../misc/overview-of-derived-classes.md)