---
title: "编译器警告 （等级 2） C4275 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4275
dev_langs:
- C++
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 873a96d4595b75ff6b9567500723c32d7ba5bd2b
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-2-c4275"></a>编译器警告（等级 2）C4275
非 – DLL 接口 classkey identifier 用作基本 DLL 接口 classkey identifier  
  
 导出的类被派生自不导出的类。  
  
 若要在导出具有的类时，数据损坏的可能性降到最低[__declspec （dllexport)](../../cpp/dllexport-dllimport.md)，确保︰  
  
-   通过从 DLL 导出的函数访问所有静态数据。  
  
-   您的类的任何内联的方法可以不修改静态数据。  
  
-   您的类的任何内联的方法使用 CRT 函数，或使用静态数据的其他库函数。  
  
-   没有内联的类函数使用 CRT 函数或其他库的功能，其中，例如，访问静态数据。  
  
-   您的类的任何方法 (而不考虑内联) 可以使用类型其中 EXE 和 DLL 中的实例化具有静态数据差异。  
  
 您可以避免通过定义一个 DLL，它定义了一个类具有虚函数和函数您可以调用来实例化并删除对象类型的导出类。  您可以然后只需调用虚函数的类型。  
  
 导出模板的详细信息，请参阅[从中查看EN-US;&16895;8](http://support.microsoft.com/default.aspx?scid=KB;EN-US;168958)。  
  
 如果从 c + + 标准库，编译调试版本中的类型派生，可以在 Visual c + + 中忽略 C4275 (**/MTd**)，其中编译器错误消息是指 _Container_base。  
  
```  
// C4275.cpp  
// compile with: /EHsc /MTd /W2 /c  
#include <vector>  
using namespace std;  
class Node;  
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275  
```
