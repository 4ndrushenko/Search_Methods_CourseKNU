Lab7.R
================


``` r



##3. Зчитайте xml файл за посиланням http://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Frestaurants.xml 
```r
library(XML)
download.file("http://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Frestaurants.xml", "lab1_data3.xml", "auto", TRUE, mode = "wb")
lab1_data3 <- xmlRoot(xmlTreeParse("lab1_data3.xml", useInternalNodes = TRUE))
sum(xpathSApply(lab1_data3, "//zipcode", xmlValue) == 21231)
```
```
[1] 127
```
