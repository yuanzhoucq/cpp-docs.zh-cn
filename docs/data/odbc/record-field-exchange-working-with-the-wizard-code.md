---
title: 记录字段交换：使用向导代码
ms.date: 11/04/2016
helpviewer_keywords:
- DoFieldExchange method, overriding
- Unicode, with database classes
- field data members, declaring
- RFX (ODBC), wizard code
- RFX (ODBC), implementing
- field data members
- ODBC, RFX
- m_nParams data member, initializing
- m_nFields data member
- m_nParams data member
- overriding, DoFieldExchange
- m_nFields data member, initializing
ms.assetid: f00d882a-ff1b-4a75-9717-98d8762bb237
ms.openlocfilehash: c0e1a35e5476c9e2e335c6f2863429d89e4fa28a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492113"
---
# <a name="record-field-exchange-working-with-the-wizard-code"></a>记录字段交换：使用向导代码

本主题说明代码的 MFC 应用程序向导并**添加类**(如中所述[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) 为支持 RFX 和如何你可能想要更改该代码编写。

> [!NOTE]
>  本主题适用于从派生的类`CRecordset`中的批量行提取尚未实现。 如果使用批量行提取，实现批量记录字段交换 (Bulk RFX)。 批量 RFX 是类似于 RFX。 若要了解的差异，请参阅[记录集： 提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

当使用 MFC 应用程序向导创建记录集类或**添加类**，向导会将您基于数据源中，表的并在向导中做出的列选择写入 RFX 相关的以下元素：

- 记录集类中的记录集字段数据成员的声明

- 重写 `CRecordset::DoFieldExchange`

- 记录集类构造函数中的记录集字段数据成员的初始化

##  <a name="_core_the_field_data_member_declarations"></a> 字段数据成员声明

在向导中的.h 文件，如下所示的类编写记录集类声明`CSections`:

```cpp
class CSections : public CRecordset
{
public:
   CSections(CDatabase* pDatabase = NULL);
   DECLARE_DYNAMIC(CSections)

// Field/Param Data
   CString   m_strCourseID;
   CString   m_strInstructorID;
   CString   m_strRoomNo;
   CString   m_strSchedule;
   CString   m_strSectionNo;

// Overrides
   // Wizard generated virtual function overrides
   protected:
   virtual CString GetDefaultConnect();  // Default connection string
   virtual CString GetDefaultSQL();      // Default SQL for Recordset
   virtual void DoFieldExchange(CFieldExchange* pFX);  // RFX support

// Implementation
#ifdef _DEBUG
   virtual void AssertValid() const;
   virtual void Dump(CDumpContext& dc) const;
#endif

};
```

如果您添加的参数数据成员或您自己绑定的新字段数据成员，则将它们添加后在向导生成的。

另请注意，该向导将重写`DoFieldExchange`类的成员函数`CRecordset`。

##  <a name="_core_the_dofieldexchange_override"></a> DoFieldExchange 重写

[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)是 RFX 的核心。 框架将调用`DoFieldExchange`任何时候，需要将数据从数据源到记录集或从记录集移到数据源。 `DoFieldExchange` 有关获取信息的支持字段数据成员通过还[IsFieldDirty](../../mfc/reference/crecordset-class.md#isfielddirty)并[IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull)成员函数。

以下`DoFieldExchange`重写为`CSections`类。 向导会将该函数写入记录集类的.cpp 文件中。

```cpp
void CSections::DoFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   RFX_Text(pFX, "CourseID", m_strCourseID);
   RFX_Text(pFX, "InstructorID", m_strInstructorID);
   RFX_Text(pFX, "RoomNo", m_strRoomNo);
   RFX_Text(pFX, "Schedule", m_strSchedule);
   RFX_Text(pFX, "SectionNo", m_strSectionNo);
}
```

请注意，该函数的以下主要功能：

- 该函数的此部分称为字段映射。

- 调用`CFieldExchange::SetFieldType`，通过`pFX`指针。 此调用指定到结尾的所有 RFX 函数都调用`DoFieldExchange`或者对下一步调用`SetFieldType`输出列。 有关详细信息，请参阅[CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)。

- 多次调用`RFX_Text`全局函数，一个每个字段数据成员 (其中的所有`CString`在示例中的变量)。 这些调用指定数据源的列名称和字段数据成员之间的关系。 RFX 函数执行实际数据传输。 类库提供对所有常见的数据类型的 RFX 函数。 有关 RFX 函数的详细信息，请参阅[记录字段交换： 使用 RFX 函数](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)。

    > [!NOTE]
    >  在结果集中列的顺序必须与 RFX 函数调用中的顺序匹配`DoFieldExchange`。

- `pFX`指针，指向[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)对象，该框架将调用时传递对象`DoFieldExchange`。 `CFieldExchange`对象指定的操作的`DoFieldExchange`将要执行的传输和其他上下文信息的方向。

##  <a name="_core_the_recordset_constructor"></a> 记录集构造函数

这些向导编写的记录集构造函数包含与 RFX 相关的两项操作：

- 每个字段数据成员初始化

- 用于初始化[m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)数据成员，其中包含字段数据成员的数目

构造函数`CSections`记录集的示例如下所示：

```cpp
CSections::CSections(CDatabase* pdb)
   : CRecordset(pdb)
{
   m_strCourseID = "";
   m_strInstructorID = "";
   m_strRoomNo = "";
   m_strSchedule = "";
   m_strSectionNo = "";
   m_nFields = 5;
}
```

> [!NOTE]
>  如果您任何字段数据成员手动添加，可能会动态绑定的新列时，必须递增`m_nFields`。 执行此操作通过追加另一行代码，如：

```cpp
m_nFields += 3;
```

这是用于添加三个新字段的代码。 如果添加任何参数数据成员，则必须初始化[m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)数据成员，其中包含参数数据成员的数目。 放置`m_nParams`在括号外的初始化。

## <a name="see-also"></a>请参阅

[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)