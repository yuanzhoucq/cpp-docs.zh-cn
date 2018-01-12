---
title: "记录字段交换： 处理向导代码 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8909a9e933e7b3f1c59fa9ab283706f7a6d1f0c0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="record-field-exchange-working-with-the-wizard-code"></a>记录字段交换：使用向导代码
本主题解释的代码，MFC 应用程序向导和**添加类**(中所述[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) 为支持 RFX 和如何你可能想要更改该代码编写。  
  
> [!NOTE]
>  本主题适用于从派生的类`CRecordset`中哪些批量行提取尚未实现。 如果你将批量行提取，实现批量记录字段交换 (Bulk RFX)。 批量 RFX 等同于 RFX。 若要了解的差别，请参阅[记录集： 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 当使用 MFC 应用程序向导创建记录集类或**添加类**，向导会将你基于数据源中，表，并在向导中做出的列选择写入 RFX 相关的以下元素：  
  
-   记录集类中的记录集字段数据成员的声明  
  
-   重写`CRecordset::DoFieldExchange`  
  
-   记录集类构造函数中的记录集字段数据成员的初始化  
  
##  <a name="_core_the_field_data_member_declarations"></a>字段数据成员声明  
 向导中的.h 文件，如下所示的类编写记录集类声明`CSections`:  
  
```  
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
  
 如果你添加的参数数据成员或您自己绑定的新字段数据成员，请将它们添加后在向导生成的。  
  
 此外，请注意，该向导将覆盖`DoFieldExchange`类的成员函数`CRecordset`。  
  
##  <a name="_core_the_dofieldexchange_override"></a>DoFieldExchange 替代  

 [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)是 RFX 的核心。 框架调用`DoFieldExchange`随时，需要将数据从数据源得到记录集或从记录集移到数据源。 `DoFieldExchange`此外支持获取有关的信息字段数据成员通过[IsFieldDirty](../../mfc/reference/crecordset-class.md#isfielddirty)和[IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull)成员函数。  
  
 以下`DoFieldExchange`替代为`CSections`类。 向导会将该函数写入记录集类的.cpp 文件中。  
  
```  
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
  
 请注意该函数的主要功能如下：  
  
-   此部分的函数称为字段映射。  
  
-   调用`CFieldExchange::SetFieldType`，直到`pFX`指针。 此调用指定左边缘所有 RFX 函数都调用`DoFieldExchange`或到下一个调用`SetFieldType`输出列。 有关详细信息，请参阅[CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)。  
  
-   对多个调用`RFX_Text`全局函数-一个每个字段数据成员 (所有这些选项均进行`CString`在示例中的变量)。 这些调用指定的数据源上的一个列名称和字段数据成员之间的关系。 RFX 函数执行实际的数据传输。 类库提供 RFX 函数对于所有常见的数据类型。 有关 RFX 函数的详细信息，请参阅[记录字段交换： 使用 RFX 函数](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)。  
  
    > [!NOTE]
    >  结果集中的列的顺序必须匹配中的 RFX 函数调用的顺序`DoFieldExchange`。  
  
-   `pFX`指向[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)框架传递时，它调用对象的`DoFieldExchange`。 `CFieldExchange`对象指定的操作，`DoFieldExchange`是执行的传输和其他上下文信息的方向。  
  
##  <a name="_core_the_recordset_constructor"></a>记录集构造函数  
 向导编写的记录集构造函数包含与 RFX 相关的以下两项操作：  
  
-   每个字段数据成员初始化  
  
-   初始化[m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)数据成员，其中包含字段数据成员的数目  
  
 构造函数`CSections`记录集示例如下所示：  
  
```  
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
>  如果因为你可能会动态绑定新列时手动添加任何字段数据成员，则必须增加`m_nFields`。 执行操作来追加另一个代码行，如：  
  
```  
m_nFields += 3;  
```  

 这是添加三个新字段的代码。 如果添加任何参数数据成员，必须初始化[m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)数据成员，其中包含参数数据成员的数目。 Put`m_nParams`括号外的初始化。  

  
## <a name="see-also"></a>请参阅  
 [记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)