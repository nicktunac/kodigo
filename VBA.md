#VBA#
Get last row number of a Column

    LastRow = Range("A1").CurrentRegion.Rows.Count

Get rows after filter

    Dim r As Range
    Dim StartRow As Long
    Dim EndRow As Long

    Set r = ActiveSheet.Range("A2:A81000").Rows.SpecialCells(xlCellTypeVisible)
    ' r is now $A$73351:$A$77343

    StartRow = r.Row ' returns 73351
    EndRow = r.Row + r.Rows.Count - 1 ' returns 77343
    
Reference a workbook

    Dim workbook As Excel.Workbook
    Set workbook = Workbooks.Open("C:\Documents and Settings\xxxx\Desktop\test1.xls")
    
 Iterate to a directory
 
    Dim StrFile As String
    StrFile = Dir(directory & "\*.xlsx*")
    Do While Len(StrFile) > 0
        Debug.Print StrFile
        StrFile = Dir
    Loop
    
Copy From Sheet-X to Sheet-Y

    Sheets("<Sheet_Name>").Select
    Range("A(X):A(Y)").Select
    Selection.Copy
    Sheets("<Sheet_Name>").Select
    Range("A(X)").Select
    ActiveSheet.Paste

Call a Function with multiple parameter

    Call generateURL(n, firstCol) , or
    generateURL n, firstCol
    
Save workbook without saving    
    
    wbk.Activate
    ActiveWorkbook.Close Savechanges:=False
