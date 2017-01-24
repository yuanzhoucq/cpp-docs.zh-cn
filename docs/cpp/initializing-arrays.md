---
title: "初始化数组 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "初始化数组"
  - "初始化数组 [c + +]"
ms.assetid: 41efe5f0-15b5-4f49-9196-c4902f8fc705
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 初始化数组
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果类具有构造函数，该类的数组将由构造函数初始化。 如果初始值设定项列表中的项少于数组中的元素，则默认的构造函数将用于剩余元素。 如果没有为类定义默认构造函数，初始值设定项列表必须完整，即数组中的每个元素都必须有一个初始值设定项。  
  
 考虑定义了两个构造函数的`Point` 类：  
  
```  
// initializing_arrays1.cpp  
class Point  
{  
public:  
   Point()   // Default constructor.  
   {  
   }  
   Point( int, int )   // Construct from two ints  
   {  
   }  
};  
  
// An array of Point objects can be declared as follows:  
Point aPoint[3] = {  
   Point( 3, 3 )     // Use int, int constructor.  
};  
  
int main()  
{  
}  
```  
  
 `aPoint` 的第一个元素是使用构造函数 `Point( int, int )` 构造的；剩余的两个元素是使用默认构造函数构造的。  
  
 静态成员数组 (是否 **const** 与否) 可在它们的定义 （类声明的外部） 中初始化。 例如:   
  
```  
// initializing_arrays2.cpp  
class WindowColors  
{  
public:  
    static const char *rgszWindowPartList[7];  
};  
  
const char *WindowColors::rgszWindowPartList[7] = {  
    "Active Title Bar", "Inactive Title Bar", "Title Bar Text",  
    "Menu Bar", "Menu Bar Text", "Window Background", "Frame"   };  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [(NOTINBUILD)特殊成员函数](http://msdn.microsoft.com/zh-cn/82223d73-64cb-4923-b678-78f9568ff3ca)