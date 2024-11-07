// Current Year Profit
IF YEAR([Order Date]) = [Select Year]
THEN [Profit]
END

// Previous Year Profit
IF YEAR([Order Date]) = [Select Year] - 1
THEN [Profit]
END

// Current Year Quantity
IF YEAR([Order Date]) = [Select Year]
THEN [Quantity]
END

// Previous Year Quantity
IF YEAR([Order Date]) = [Select Year] - 1
THEN [Quantity]
END

// Current Year Sales
IF YEAR([Order Date]) = [Select Year]
THEN [Sales]
END

// Previous Year Sales
IF YEAR([Order Date]) = [Select Year] - 1
THEN [Sales]
END

// % Profit
(SUM([CY Profit]) - SUM([PY Profit])) / SUM([PY Profit])

// % Quantity
(SUM([CY Quantity]) - SUM([PY Quantity])) / SUM([PY Quantity])

// % Sales
(SUM([CY Sales]) - SUM([PY Sales])) / SUM([PY Sales])

// KPI Average of Profit
IF SUM([CY Profit]) > WINDOW_AVG(SUM([CY Profit]))
THEN 'Above'
ELSE 'Below'
END

// KPI Average of Sales
IF SUM([CY Sales]) > WINDOW_AVG(SUM([CY Sales]))
THEN 'Above'
ELSE 'Below'
END

// Indicator if Current Year Sales is less than Previous Year Sales
IF SUM([CY Sales]) < SUM([PY Sales])
THEN '●'
ELSE ''
END

// Min/Max Quantity
IF SUM([CY Quantity]) = WINDOW_MAX(SUM([CY Quantity]))
THEN SUM([CY Quantity])
ELSEIF SUM([CY Quantity]) = WINDOW_MIN(SUM([CY Quantity]))
THEN SUM([CY Quantity])
END

// Min/Max Sales
IF SUM([CY Sales]) = WINDOW_MAX(SUM([CY Sales]))
THEN SUM([CY Sales])
ELSEIF SUM([CY Sales]) = WINDOW_MIN(SUM([CY Sales]))
THEN SUM([CY Sales])
END

// Min/Max Profit
IF SUM([CY Profit]) = WINDOW_MAX(SUM([CY Profit]))
THEN SUM([CY Profit])
ELSEIF SUM([CY Profit]) = WINDOW_MIN(SUM([CY Profit]))
THEN SUM([CY Profit])
END
