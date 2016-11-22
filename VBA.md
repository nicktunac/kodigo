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
    
Disable Screenupdate and Display Alerts

    Application.ScreenUpdating = False
    Application.DisplayAlerts = False
    
Remove Autofilter (If filter is already activated)

    Cells.AutoFilter
    
Exact, compare 2 selection
    
    =AND(EXACT(<RANGES>,<RANGES>)) then CTRL + SHIFT + ENTER
    
FuzzyMatching

    Function FuzzyMatch(ByVal string1 As String, ByVal string2 As String) As Long

    Dim i As Long, j As Long, string1_length As Long, string2_length As Long
    Dim distance(0 To 60, 0 To 50) As Long, smStr1(1 To 60) As Long, smStr2(1 To 50) As Long
    Dim min1 As Long, min2 As Long, min3 As Long, minmin As Long, MaxL As Long

    string1_length = Len(string1):  string2_length = Len(string2)

    distance(0, 0) = 0
    For i = 1 To string1_length:    distance(i, 0) = i: smStr1(i) = Asc(LCase(Mid$(string1, i, 1))): Next
    For j = 1 To string2_length:    distance(0, j) = j: smStr2(j) = Asc(LCase(Mid$(string2, j, 1))): Next
    For i = 1 To string1_length
        For j = 1 To string2_length
            If smStr1(i) = smStr2(j) Then
                distance(i, j) = distance(i - 1, j - 1)
            Else
                min1 = distance(i - 1, j) + 1
                min2 = distance(i, j - 1) + 1
                min3 = distance(i - 1, j - 1) + 1
                If min2 < min1 Then
                    If min2 < min3 Then minmin = min2 Else minmin = min3
                Else
                    If min1 < min3 Then minmin = min1 Else minmin = min3
                End If
                distance(i, j) = minmin
            End If
        Next
    Next

    ' FuzzyMatch will properly return a percent match (100%=exact) based on similarities and Lengths etc...
    MaxL = string1_length: If string2_length > MaxL Then MaxL = string2_length
    FuzzyMatch = 100 - CLng((distance(string1_length, string2_length) * 100) / MaxL)

    End Function
    
For Loop

    For LCounter = 1 to 5
      MsgBox (LCounter)
    Next LCounter

Create Sheet

    Private Sub CreateSheet()
        Dim ws As Worksheet
        With ThisWorkbook
            Set ws = .Sheets.Add(After:=.Sheets(.Sheets.Count))
            ws.Name = "Tempo"
        End With
    End Sub
