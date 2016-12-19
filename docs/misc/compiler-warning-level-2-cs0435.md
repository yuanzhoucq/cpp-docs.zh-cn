---
title: "编译器警告（等级 2）CS0435 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0435"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0435"
ms.assetid: e70cd8c1-d399-4af8-8b1e-69a1de389aad
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器警告（等级 2）CS0435
“assembly”中的命名空间“namespace”与“assembly”中的导入类型“type”冲突。 请使用“assembly”中定义的命名空间..  
  
 源文件 \(file\_2\) 中的命名空间与 file\_1 中的导入类型冲突时，会发出此警告。 编译器使用源文件中的命名空间。  
  
 下面的示例生成 CS0435：  
  
 首先编译以下文件:  
  
```  
// CS0435_1.cs // compile with: /t:library public class Util { public class A { } }  
```  
  
 然后编译以下文件:  
  
```  
// CS0435_2.cs // compile with: /r:CS0435_1.dll using System; namespace Util { public class A { } } public class Test { public static void Main() { Console.WriteLine(typeof(Util.A)); // CS0435 } }  
```