---
title: dllimport-dllexport 的规则和限制
ms.date: 11/04/2016
helpviewer_keywords:
- dllexport attribute [C++], limitations and rules
- dllimport attribute [C++], limitations and rules
- dllexport attribute [C++]
ms.assetid: 274b735f-ab9c-4b07-8d0e-fdb65d664634
ms.openlocfilehash: c2f121d978962fe7fc03aa453fb0a16650aa2727
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220868"
---
# <a name="rules-and-limitations-for-dllimportdllexport"></a>dllimport/dllexport 的规则和限制

**Microsoft 专用**

- 如果你没有使用 `dllimport` 或 `dllexport` 特性声明函数，则此函数被视为不是 DLL 接口的一部分。 因此，函数的定义必须存在于该模块或同一程序的另一个模块中。 若要使函数成为 DLL 接口的一部分，您必须将其他模块中函数的定义声明为 `dllexport`。 否则，在构建客户端时，将生成链接器错误。

- 如果程序中的单个模块包含对同一函数的 `dllimport` 和 `dllexport` 声明，则 `dllexport` 特性优先于 `dllimport` 特性。 但是，会生成编译器警告。 例如：

    ```
    #define DllImport   __declspec( dllimport )
    #define DllExport   __declspec( dllexport )

       DllImport void func1( void );
       DllExport void func1( void );   /* Warning; dllexport */
                                       /* takes precedence. */

    ```

- 无法利用使用 `dllimport` 特性声明的数据对象的地址来初始化静态数据指针。 例如，下面的代码将生成错误：

    ```
    #define DllImport   __declspec( dllimport )
    #define DllExport   __declspec( dllexport )

       DllImport int i;
       .
       .
       .
       int *pi = &i;                           /* Error */

       void func2()
       {
          static int *pi = &i;                   /* Error */
       }

    ```

- 如果利用使用 `dllimport` 声明的函数的地址来初始化静态函数指针，会将指针设置为 DLL 导入 thunk（将控制权转移给函数的代码存根）的地址，而不是函数的地址。 此赋值不生成错误消息：

    ```
    #define DllImport   __declspec( dllimport )
    #define DllExport   __declspec( dllexport )

       DllImport void func1( void
       .
       .
       .
       static void ( *pf )( void ) = &func1;   /* No Error */

       void func2()
       {
          static void ( *pf )( void ) = &func1;  /* No Error */
       }

    ```

- 由于包含对象声明中的 `dllexport` 特性的程序必须为该对象提供定义，因此您可以利用 `dllexport` 函数的地址初始化全局或局部静态函数指针。 同样，您可以利用 `dllexport` 数据对象的地址初始化全局或局部静态数据指针。 例如：

    ```
    #define DllImport   __declspec( dllimport )
    #define DllExport   __declspec( dllexport )

       DllImport void func1( void );
       DllImport int i;

       DllExport void func1( void );
       DllExport int i;
       .
       .
       .
       int *pi = &i;                            /* Okay */
       static void ( *pf )( void ) = &func1;    /* Okay */

       void func2()
       {
          static int *pi = i;                     /* Okay */
          static void ( *pf )( void ) = &func1;   /* Okay */
       }

    ```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[DLL 导入和导出函数](../c-language/dll-import-and-export-functions.md)
