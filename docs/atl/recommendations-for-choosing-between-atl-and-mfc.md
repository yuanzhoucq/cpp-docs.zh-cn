---
title: "Recommendations for Choosing Between ATL and MFC | Microsoft Docs"
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
  - "ATL, 与 MFC"
  - "MFC, ATL 支持"
ms.assetid: 269325bb-11a8-4330-ad2b-a14a2458679e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Recommendations for Choosing Between ATL and MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在开发组件和应用程序时，可以选择两种方法之间— ATL和MFC \(Microsoft基础选件类库\)。  
  
## 使用 ATL  
 ATL快，最简单的方法绑定到C\+\+创建一个COM组件并维护一个小的复盖区域。  请使用ATL创建控件，如果不需要MFC自动提供的所有内置功能。  
  
## 使用 MFC  
 MFC允许您创建完整的应用程序，ActiveX控件，因此，活动文档。  如果您在MFC中创建了一个控件时，您可能希望继续在MFC的开发。  当创建新控件时，请考虑使用ATL，如果不需要任何MFC的内置功能。  
  
## 使用在MFC项目的ATL  
 您可以添加ATL支持在现有MFC项目通过运行向导。  有关详细信息，请参见 [添加ATL支持向MFC项目](../mfc/reference/adding-atl-support-to-your-mfc-project.md)。  
  
## 请参阅  
 [ATL 介绍](../atl/introduction-to-atl.md)