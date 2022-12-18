# Honey-Bee-Colonies <br><br/>

### Dashboard
<p align="center">
<img width="650em" src="https://github.com/Power-BI-Solutions/Honey-Bee-Colonies/blob/main/honey_bee_colonies.gif" align = "center"/>
</p>
<br><br/>

### Data Source
- [Bee Colony Census Data by County.csv](https://data.world/finley/bee-colony-statistical-data-from-1987-2017/workspace/file?filename=Bee+Colony+Census+Data+by+County.csv)
- [Bee Colony Loss.xlsx](https://data.world/finley/bee-colony-statistical-data-from-1987-2017/workspace/file?filename=Bee+Colony+Loss.xlsx)
- [Bee Colony Survey Data by State.csv](https://data.world/finley/bee-colony-statistical-data-from-1987-2017/workspace/file?filename=Bee+Colony+Survey+Data+by+State.csv)
<br><br/>

### Custom Measures
I used the following measures within the dashboard:

```dax
Colonies = SUM(census_data[value])
``` 

```dax
Total Colonies = SUM(survey_data[value])
``` 


```dax
Avg. Loss = AVERAGE(colony_loss[percentage_total_annual_loss])
``` 


```dax
Avg. of Total = 
VAR rowscounts = CALCULATE(COUNTROWS(colony_loss),ALL(colony_loss))
VAR TotalQuantity = CALCULATE(SUM(colony_loss[percentage_total_annual_loss]),ALL(colony_loss))
RETURN
CALCULATE(DIVIDE(TotalQuantity,rowscounts,0),ALL(colony_loss[percentage_total_annual_loss])
)
``` 


```dax
Custom Order = 
IF(VALUES(colony_loss[year]) = "2010/11", 1,
IF(VALUES(colony_loss[year]) = "2011/12", 2,
IF(VALUES(colony_loss[year]) = "2012/13", 3,
IF(VALUES(colony_loss[year]) = "2013/14", 4,
IF(VALUES(colony_loss[year]) = "2014/15", 5,
IF(VALUES(colony_loss[year]) = "2015/16", 6,
IF(VALUES(colony_loss[year]) = "2016/17", 7,
0)))))))
``` 







