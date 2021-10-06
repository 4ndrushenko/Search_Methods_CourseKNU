Lab6.R
================


``` r
## 1.   виконання завдання 1: За допомогою download.file() завантажте 
файл getdata_data_ss06hid.csv.

#  ur12 <- "https://d396qusza40orc.cloudfront.net/getdata/data/ss06hid.csv" 
file2 <- "getdata_data ss06hid.csv" 
download.file(ur12, file2)
 data2 -reаd.csv(file2) 
print('3 first rows of Dataset 2:') 
head (data2, n-3) 
n_val 3D length (which (data2 $ VAL - 24)) 
cat ('Number with value $ 1000000 +: ", n_val)

##result

> cat ('Number with valuе $ 1000000 +:', n_val)
Number with value $ 1000000 +: 53

   