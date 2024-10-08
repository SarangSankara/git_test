
<h2>Assignment 5</h2>
Create a Tableau KPI card showcasing
-  total profit for the current year (last year of the dataset)
- percentage growth from the previous year, indicated by a green upward arrow
  with a &quot;+&quot; sign for positive growth and a red downward arrow with a &quot;-ve&quot; sign for negative growth.
-  Incorporate a line chart depicting monthly profit trends for the current year.

![[Pasted image 20241008110141.png]]

![Image](https://i93.servimg.com/u/f93/19/44/64/05/tablel10.png)


<h4>Latest Year</h4>
``` 
YEAR([Order Date]) = {MAX(YEAR([Order Date]))}
```

<h4>Latest Year Profit</h4>
```
{ FIXED : SUM(if YEAR([Order Date])={MAX(YEAR([Order Date]))} then [Profit] END)}
``` 

<h4>Previous Year Profit</h4>
```
{ FIXED : SUM(if YEAR([Order Date])={MAX(YEAR([Order Date]))}-1 then [Profit] END)}
```


<h4>Percentage  Change Profit</h4>
```
([Latest Year Profit] - [Previous Year Profit])/[Previous Year Profit]
```

<h4>Percentage Change Profit +ve</h4>
```
zn(if [Latest Year Profit]>[Previous Year Profit]
then

([Latest Year Profit] - [Previous Year Profit])/[Previous Year Profit]end)
```

<h4>Percentage Change Profit -ve</h4>
```
zn(if [Latest Year Profit]<[Previous Year Profit]
then

([Latest Year Profit] - [Previous Year Profit])/[Previous Year Profit]end)
```

<h4>Profit Line</h4>
```
[Latest Year Profit]>[Previous Year Profit]
```

