# VBA-Challenge

## Overview of Project

-The purpose of this project was to analyze information on group of stocks from the years 2017 and 2018. This was completed by coding VBA to automate tasks and quickly provide information on which stocks to potentially invest in. The second purpose was to use refactoring to make the code more efficient and improve the time it takes to run the analysis. The data that was output contains two sets of data over two years (2017 and 2018). The results were pulled from two worksheets that contained stock information for twelve companies. The information was the ticker of the company, the date of exchange with the price at open, the highest and lowest price for the day, the price at close, the adjusted close and the volume traded. From there, the macro provided the results for the year for the company including the ticker, total daily volume exchanged and the rate of return for the given year the user inputs.

## Results

The entire code for the project is listed below:
Sub AllStocksAnalysisRefactored()
    Dim startTime As Single
    Dim endTime  As Single

    yearValue = InputBox("What year would you like to run the analysis on?")

    startTime = Timer
    
    'Format the output sheet on All Stocks Analysis worksheet
    Worksheets("All Stocks Analysis").Activate
    
    Range("A1").Value = "All Stocks (" + yearValue + ")"
    
    'Create a header row
    Cells(3, 1).Value = "Ticker"
    Cells(3, 2).Value = "Total Daily Volume"
    Cells(3, 3).Value = "Return"

    'Initialize array of all tickers
    Dim tickers(12) As String
    
    tickers(0) = "AY"
    tickers(1) = "CSIQ"
    tickers(2) = "DQ"
    tickers(3) = "ENPH"
    tickers(4) = "FSLR"
    tickers(5) = "HASI"
    tickers(6) = "JKS"
    tickers(7) = "RUN"
    tickers(8) = "SEDG"
    tickers(9) = "SPWR"
    tickers(10) = "TERP"
    tickers(11) = "VSLR"
    
    'Activate data worksheet
    Worksheets(yearValue).Activate
    
    'Get the number of rows to loop over
    RowCount = Cells(Rows.Count, "A").End(xlUp).Row
    
    '1a) Create a ticker Index
    tickerIndex = 0

    '1b) Create three output arrays
    Dim tickerVolumes(12) As Long
    Dim tickerStartingPrices(12) As Single
    Dim tickerEndingPrices(12) As Single
    
    ''2a) Create a for loop to initialize the tickerVolumes to zero.
    For i = 0 To 11
    tickerVolumes(i) = 0
    tickerStartingPrices(i) = 0
    tickerEndingPrices(i) = 0
    Next i
        
    ''2b) Loop over all the rows in the spreadsheet.
    For i = 2 To RowCount
    
        '3a) Increase volume for current ticker
        tickerVolumes(tickerIndex) = tickerVolumes(tickerIndex) + Cells(i, 8).Value
        
        '3b) Check if the current row is the first row with the selected tickerIndex.
        'If  Then
        If Cells(i, 1).Value = tickers(tickerIndex) And Cells(i - 1, 1).Value <> tickers(tickerIndex) Then
        tickerStartingPrices(tickerIndex) = Cells(i, 6).Value
        End If
        
        '3c) check if the current row is the last row with the selected ticker
         'If the next row's ticker doesn't match, increase the tickerIndex.
        'If  Then
          If Cells(i, 1).Value = tickers(tickerIndex) And Cells(i + 1, 1).Value <> tickers(tickerIndex) Then
            tickerEndingPrices(tickerIndex) = Cells(i, 6).Value
        End If
            
            '3d Increase the tickerIndex.
            If Cells(i, 1).Value = tickers(tickerIndex) And Cells(i + 1, 1).Value <> tickers(tickerIndex) Then
            tickerIndex = tickerIndex + 1
        End If
        'End if
        
    
    Next i
    
    '4) Loop through your arrays to output the Ticker, Total Daily Volume, and Return.
    For i = 0 To 11
        
        Worksheets("All Stocks Analysis").Activate
        Cells(4 + i, 1).Value = tickers(i)
        Cells(4 + i, 2).Value = tickerVolumes(i)
        Cells(4 + i, 3).Value = tickerEndingPrices(i) / tickerStartingPrices(i) - 1
        
    Next i
    
    'Formatting
    Worksheets("All Stocks Analysis").Activate
    Range("A3:C3").Font.FontStyle = "Bold"
    Range("A3:C3").Borders(xlEdgeBottom).LineStyle = xlContinuous
    Range("B4:B15").NumberFormat = "#,##0"
    Range("C4:C15").NumberFormat = "0.0%"
    Columns("B").AutoFit

    dataRowStart = 4
    dataRowEnd = 15

    For i = dataRowStart To dataRowEnd
        
        If Cells(i, 3) > 0 Then
            
            Cells(i, 3).Interior.Color = vbGreen
            
        Else
        
            Cells(i, 3).Interior.Color = vbRed
            
        End If
        
    Next i
 
    endTime = Timer
    MsgBox "This code ran in " & (endTime - startTime) & " seconds for the year " & (yearValue)

End Sub

-When comparing the original code to the new code we can see slight changes in the time needed to run the macro. In 2017 the original code ran in 0.4 seconds and the refactored code ran in 0.54 seconds. For 2018 the original code .42 seconds and the refactored code ran in .46 seconds. Both are hardly noticeable to make a difference but if this was to run on larger projects then the time disparity could become larger.
  ![VBA_Challenge_2017_Before](Resources/VBA_Challenge_2017_Before.png)
  ![VBA_Challenge_2017](Resources/VBA_Challenge_2017.png)
  ![VBA_Challenge_2018_Before](Resources/VBA_Challenge_2018_Before.png)
  ![VBA_Challenge_2018](Resources/VBA_Challenge_2018.png)
-Looking at the stocks there are only two that have shown a return over the two years. ENPH and RUN both has a positive return rate with RUN showing a much larger return. All other stocks had a negative return percentage however AY had a much smaller loss than all others and would be one to watch for. TERP is the only stock that has not have a positive return.
![VBA_Challenge_2017_Results](Resources/VBA_Challenge_2017_Results.png)
![VBA_Challenge_2018_Results](Resources/VBA_Challenge_2018_Results.png)

## Summary

-Refactoring our existing code shows these advantages and disadvantages. Luckily, no new bugs or errors are introduced. However, the time difference was slightly better under the original code where it doesn’t make a difference. A larger project may show a significant advantage to either the original or refactored code. Refactoring does have the benefit of making the coding more organized and easier to read. I had a slight issue with getting the button to work and within the loop and the organization on the coding and highlighting problem areas made it easy to resolve.

