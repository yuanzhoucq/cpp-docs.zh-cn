---
title: "标识符 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- decorated names
- decorated names, about decorated names
- identifiers, C++
- white space, in C++ identifiers
- identifiers
ms.assetid: 03a0dfb1-4530-4cdf-8295-5ea4dca4c1b8
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 84b0aafe5c5327e175791bb5107c72500f9834b1
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="identifiers-c"></a>标识符 （c + +）
标识符是用于表示以下内容之一的字符序列：  
  
-   对象或变量名称  
  
-   类、结构或联合名称  
  
-   枚举类型名称  
  
-   类、结构、联合或枚举的成员  
  
-   函数或类成员函数  
  
-   typedef 名称  
  
-   标签名称  
  
-   宏名称  
  
-   宏参数  
  
 允许将以下字符用作标识符的任意字符：  
  
```  
_ a b c d e f g h i j k l m  
n o p q r s t u v w x y z  
A B C D E F G H I J K L M  
N O P Q R S T U V W X Y Z  
```  
  
 还允许在标识符中使用通用字符名称的某些范围。  标识符中的通用字符名称不能指定控制字符或基本源字符集中的字符。 有关详细信息，请参阅 [Character Sets](../cpp/character-sets2.md)。 允许将以下 Unicode 码位数字范围用作标识符中任意字符的通用字符名称：  
  
-   00A8、00AA、00AD、00AF、00B2-00B5、00B7-00BA、00BC-00BE、00C0-00D6、00D8-00F6、00F8-00FF、0100-02FF、0370-167F、1681-180D、180F-1DBF、1E00-1FFF、200B-200D、202A-202E、203F-2040、2054、2060-206F、2070-20CF、2100-218F、2460-24FF、2776-2793、2C00-2DFF、2E80-2FFF、3004-3007、3021-302F、3031-303F、3040-D7FF、F900-FD3D、FD40-FDCF、FDF0-FE1F、FE30-FE44、FE47-FFFD、10000-1FFFD、20000-2FFFD、30000-3FFFD、40000-4FFFD、50000-5FFFD、60000-6FFFD、70000-7FFFD、80000-8FFFD、90000-9FFFD、A0000-AFFFD、B0000-BFFFD、C0000-CFFFD、D0000-DFFFD、E0000-EFFFD  
  
 允许将以下字符用作标识符中除第一个字符以外的任意字符：  
  
```  
0 1 2 3 4 5 6 7 8 9  
```  
  
 还允许将以下 Unicode 码位数字范围用作标识符中除第一个字符以外任意字符的通用字符名称：  
  
-   0300-036F、1DC0-1DFF、20D0-20FF、FE20-FE2F  
  
 **Microsoft 专用**  
  
 只有 Microsoft C++ 标识符的前 2048 个字符是有意义的。 用户定义类型的名称由编译器“修饰”以保留类型信息。 结果名称（包括类型信息）不能超过 2048 个字符。 (请参阅[修饰名](../build/reference/decorated-names.md)有关详细信息。)可能影响修饰标识符的长度的因素包括：  
  
-   标识符是表示用户定义类型的对象还是表示派生自用户定义类型的类型。  
  
-   标识符是否表示派生自函数的函数或类型。  
  
-   函数的参数的数量。  
  
 美元符号 `$` 在 Visual C++ 中是有效标识符。 Visual C++ 还允许在标识符中使用通用字符名称允许的范围所表示的实际字符。 若要使用这些字符，必须使用包含它们的文件编码代码页保存文件。  此示例演示如何在代码中互换使用扩展字符和通用字符名称。  
  
```  
// extended_identifier.cpp  
// In Visual Studio, use File, Advanced Save Options to set  
// the file encoding to Unicode codepage 1200  
struct テスト         // Japanese 'test'  
{  
    void トスト() {}  // Japanese 'toast'  
};  
  
int main() {  
    テスト \u30D1\u30F3;  // Japanese パン 'bread' in UCN form  
    パン.トスト();        // compiler recognizes UCN or literal form  
}  
```  
  
 编译 C++/CLI 代码时，标识符中允许的字符范围限制更少。 使用 /clr 编译的代码中的标识符应遵循  [标准 ECMA-335：公共语言基础结构 (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm)。  
  
 **结束 Microsoft 专用**  
  
 标识符的第一个字符必须是字母字符（大写、小写或带下划线 ( **_** ) 的字母）。 由于 C++ 标识符区分大小写，因此 `fileName` 与 `FileName`不同。  
  
 标识符不能与关键字有完全相同的拼写和大小写。 包含关键字的标识符是合法的。 例如， `Pint` 是一个合法标识符，即使它包含 `int`关键字。  
  
 在标识符开头使用两个顺序下划线字符 ( **__** ) 或在单个前导下划线后跟一个大写字母的用法是专为所有范围的 C++ 实现保留的。 由于当前或将来的保留标识符可能发生冲突，因此应避免对文件范围的名称使用一个前导下划线后跟小写字母。  
  
## <a name="see-also"></a>另请参阅  
 [词法约定](../cpp/lexical-conventions.md)
